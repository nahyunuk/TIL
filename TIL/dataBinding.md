# Databinding 이란?
### 레이아웃 파일(xml)에 데이터를 결합(binding) 해주는 Android jetPack 라이브러리 중 하나 이다. Activity에서 findViewById()를 통해서 View를 가져올 필요가 없고, 연결된데이터가 변경 될때 쉽게 View에 변경된 데이터를 반영할 수 있는 장점이 있다.
## 기본 사용법
### 1) build.gradle에 dataBinding 추가
```
android {

    ...
 
    dataBinding {
        enabled = true
    }
}
```
### 2) 레이아웃 파일 수정
### 1. 루트를 layout
### 2. data 태그 추가
```
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android">

    <data>
        <import type="android.view.View"/>
        <variable
            name="test"
            type="com.example.databinding.MainActivity" />
    </data>

    <LinearLayout
        android:orientation="vertical"
        android:gravity="center"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text='@{test.text}'
            android:visibility='@{test.isClicked == true ? View.GONE : View.VISIBLE}' />

        <Button
            android:id="@+id/hideButton"
            android:text="Hide"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>

    </LinearLayout>
</layout>
```
### 3) 데이터 바인딩 설정
```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.databinding.DataBindingUtil
import com.example.databinding.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    var text = "Hello World!"
    var isClicked = false
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        val binding: ActivityMainBinding = DataBindingUtil.setContentView(this, R.layout.activity_main)

        binding.test = this

        binding.hideButton.setOnClickListener {
            isClicked = !isClicked
            binding.invalidateAll()
        }
    }
}
```
## 장점 
+ 코드 중복을 줄이고 유지보수성을 높인다.
+ UI와 로직을 명확하게 분리할 수 있다.

### 특히 데이터 바인딩은 복잡한 UI을 가진 앱에서 유용하게 사용될 수 있다.
