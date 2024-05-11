# 4일차
# 오늘 배운것
## c pointer array
### 선언 방법
### char* (변수이름);
```
#include<stdio.h>int main(void) {
      const char* arr[3];    //포인터 배열 선언.   
      int i;     arr[0] = "BlockDMask";        //arr[0]은 -> 문자열 주소를 가리킵니다.    
      arr[1] = "C Programming";    //arr[1]은 -> 문자열 주소를 가리킵니다.
      arr[2] = "point_arr";        //arr[2]은 -> 문자열 주소를 가리킵니다. 
       
      for (i = 0; i < 3; i++){ 
        printf("arr[%d] -> %s\n", i, arr[i]);    
        }  

      return 0;}
```
## strcpy, strlen 함수
### strcpy(a,b)
### a에 b 값을 복사 한다
```
#include <string.h>
char *strcpy(char *string1, const char *string2);
```
### strlen(arr)
### arr의 크기를 나타낸다
```
#include <stdio.h>
#include <string.h>
#define MAX_NAME_LEN 50
int main()
{
    char name[MAX_NAME_LEN+1] = "hello";
    printf("%s 길이: %d\n",name, strlen(name));
    return 0;
}
```