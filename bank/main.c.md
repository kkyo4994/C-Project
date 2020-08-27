# main.c



```c
#include <stdio.h> // 기본 함수들이(ex:printf) 선언된 헤더 파일
#include <string.h>  // strcpy 함수가 선언된 헤더 파일
#include "bank.h" // 정의 함수들이 선언된 헤더 파일 

int main() {
	Acc acc[MAX_USER_COUNT]; // MAX_USER_COUNT=3이니 3명까지 받을 수 있다
	int inputNumber;
	do {
		printf("계좌 추가는 1, 계좌 삭제는 2, 계좌 관리는 3, 모든 계좌 보기는 4, 특정 계좌 보기는 5, 종료하시려면 0을 입력해 주세요.\n");
		scanf("%d", &inputNumber); // 번호를 입력받는다
		if (inputNumber == 1) { // 만약 입력한 번호가 1번이면
			addUser(acc); // 계좌를 추가하는 함수로 간다
		}
		else if(inputNumber == 2){ // 만약 입력한 번호가 2번이면
			deleteUser(acc); // 계좌를 삭제하는 함수로 간다
		}
		else if(inputNumber == 3){ // 만약 입력한 번호가 3번이면
			management(acc); // 계좌를 관리하는 함수로 간다
		}
		else if(inputNumber == 4){ // 만약 입력한 번호가 4번이면
			print_all_information(acc); // 모든 계좌 정보 출력하는 함수로 간다
		}
		else if(inputNumber == 5){ // 만약 입력한 번호가 5번이면
			print_information(acc); // 특정 계좌 정보 출력하는 함수로 간다
		}
	} while (inputNumber != 0); // 입력한 번호가 0이 아닐 때까지
	printf("감사합니다.\n");
	return 0;
}
```



