# 2일차
# 오늘 배운것
## c언어 pointer(*)
### pointer(*)란?
###  프로그래밍 언어에서 변수의 메모리 공간의 주소를 가리키는 변수를 말한다.
### 선언하는법은?
### int *b = a; 처럼 선언할 때에는 변수명 앞에 *를 붙혀서 pointer 변수임을 명시한다.
```
#include <stdio.h>
int main() {
	int a = 8;
	int* p;
	p = &a;
	printf("%d", *p);
}
```
### 출력 : 8