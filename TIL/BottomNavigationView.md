# BottomNavigationView
## BottomNavigationView란?
### BottomNavigationView는 안드로이드 앱의 하단바이다. BottomNavigationView는 메뉴 항목에 따라 화면을 전환하는 역할을 수행하는데 전환되는 화면은 Fragment로 구성한다.
## 예시 
![nv_bar](/image/nv_bar.png)
# 간단한 BottomNavigationView 만들어 보기
### 먼저 res/menu에 BottomNavigation에 사용할 메뉴를 생성합니다.
![image](/image/nv_menu.png)
## menu_bottom_nav.xml
```  
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/fragment_home"
        android:title="홈"
        android:icon="@drawable/ic_home"/>
    <item
        android:id="@+id/fragment_search"
        android:title="검색"
        android:icon="@drawable/ic_search"/>
    <item
        android:id="@+id/fragment_favorite"
        android:title="즐겨찾기"
        android:icon="@drawable/ic_favorite"/>
    <item
        android:id="@+id/fragment_settings"
        android:title="설정"
        android:icon="@drawable/ic_settings"/>
</menu>
``` 
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    // 메뉴 아이템 클릭 시 해당 화면으로 전환을 위해 Fragment를 담을 FrameLayout을 생성합니다.
    <FrameLayout
        android:id="@+id/main_container"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        app:layout_constraintBottom_toTopOf="@+id/bottom_navigation_view"
        app:layout_constraintEnd_toEndOf="@+id/bottom_navigation_view"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    // xml에 BottomNavigationView 컴포넌트를 생성하고 앞서 만들어 두었던 menu와 연결합니다.
    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bottom_navigation_view"
        android:layout_width="match_parent"
        android:layout_height="56dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:menu="@menu/menu_bottom_nav"              
        app:labelVisibilityMode="labeled"
        app:itemTextColor="@color/black"
        app:itemIconTint="#2196F3"/>
    
</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity
```
class MainActivity : AppCompatActivity() {
    private val binding: ActivityMainBinding by lazy {
        ActivityMainBinding.inflate(layoutInflater)
    }
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(binding.root)

        setBottomNavigationView()

        // 앱 초기 실행 시 홈화면으로 설정
        if (savedInstanceState == null) {
            binding.bottomNavigationView.selectedItemId = R.id.fragment_home
        }
    }
    
    fun setBottomNavigationView() {
        binding.bottomNavigationView.setOnItemSelectedListener { item ->
            when (item.itemId) {
                R.id.fragment_home -> {
                    supportFragmentManager.beginTransaction().replace(R.id.main_container, HomeFragment()).commit()
                    true
                }
                R.id.fragment_search -> {
                    supportFragmentManager.beginTransaction().replace(R.id.main_container, SearchFragment()).commit()
                    true
                }
                R.id.fragment_favorite -> {
                    supportFragmentManager.beginTransaction().replace(R.id.main_container, FavoriteFragment()).commit()
                    true
                }
                R.id.fragment_settings -> {
                    supportFragmentManager.beginTransaction().replace(R.id.main_container, SettingsFragment()).commit()
                    true
                }
                else -> false
            }
        }
    }
}
```