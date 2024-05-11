# 5일차 
# 오늘 배운것
## kotlin 기본 문법 2
### 함수
### fun 함수이름(매개변수: type): return type
```
fun main(){
    print(add(1,2,3))
}
fun add(a: Int, b: Int, c: Int): Int{
    return a + b + c;
}
출력:
6
```
### 조건문
### if(조건식)
### c와 비슷하다
```
fun main(){
    var a = 7
    if(a > 6){
        println(a)
    } else{
        print("exit")
    }
}
출력:
7
```