# main.c

```c
#include <stdio.h> // 기본 함수들이 선언된 헤더 파일
#include <string.h> // strcpy 함수가 선언된 헤더 파일
#include "library.h" //  정의 함수들이 선언된 헤더 파일

int main() {
	Book book[MAX_BOOK_COUNT]; // book의 공간은 MAX_BOOK_COUNT(3)
	int inputnumber;
	do {
		printf("책 추가는 1, 책 대출은 2, 책 반납은 3, 모든 책 정보 출력은 4, 특정 책 정보 출력은 5, 종료는 0입니다.\n");
		scanf("%d", &inputnumber); // 번호를 입력
		if (inputnumber == 1) { // 만약 입력 받은 inputnumber가 1이면
			addBook(book); // 책을 추가하는 함수로 이동
		}
		else if (inputnumber == 2) { // 만약 입력 받은 inputnumber가 2이면
			borrowBook(book); // 책을 대출하는 함수로 이동
		}
		else if (inputnumber == 3) { // 만약 입력 받은 inputnumber가 3이면
			getBackBook(book); // 책을 반납하는 함수로 이동
		}
		else if (inputnumber == 4) { // 만약 입력 받은 inputnumber가 4이면
			all_showBook(book); // 모든 책의 정보를 출력하는 함수로 이동
		}
		else if (inputnumber == 5) { // 만약 입력 받은 inputnumber가 5이면
			showBook(book); // 특정 책의 정보를 출력하는 함수로 이동
		}
	} while ( inputnumber != 0); // inputnumber가 0이 아닐 때까지 반복
	printf("감사합니다.\n");
	return 0;
}
```

