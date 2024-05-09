# 3일차
# 오늘 배운것
## kotlin 기초 문법
### 변수
### var : 변수값을 변경 가능한 변수
### val : 선언시에만 초기화 가능한 변수
```
fun main(){
    var a: Int 
    a = 123
    print(a)
}
```
```
fun main(){
    val b: Int = 1232
    b = 3       //중간에 변수값 변경이 안되기 때문에 오류
    print(b)
}
```
### 형변환 
### kotlin에서는 to변수()를 통해 형변환 가능
```
fun main(){
    var a: Int = 123
    var b: String = a.toString()
    print(b)
}
```
### 배열
```
fun main(){
	//int형으로 1 2 3 4 배열 생성
    var intArr:Array<Int> = arrayOf(1, 2, 3, 4)
    //type 생략 가능
    var intArr2 = arrayOfNulls<Int>(5)
    //Any는 데이터 타입의 최상위(어느 데이터든 다 들어갈 수 있음)
    var anyArr : Array<Any> = arrayOf(1, "awd", 3.2, 4)	
    print(intArr[0])
    print(intArr2[1])
    print(anyArr[1])
}

출력
1
null
awd
```
