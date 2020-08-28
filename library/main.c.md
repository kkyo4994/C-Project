# main.c

```c
#include <stdio.h>
#include <string.h>
#include "library.h"

int main() {
	Book book[MAX_BOOK_COUNT];
	int inputnumber;
	do {
		printf("책 추가는 1, 책 대출은 2, 책 반납은 3, 모든 책 정보 출력은 4, 특정 책 정보 출력은 5, 종료는 0입니다.\n");
		scanf("%d", &inputnumber);
		if (inputnumber == 1) {
			addBook(book);
		}
		else if (inputnumber == 2) {
			borrowBook(book);
		}
		else if (inputnumber == 3) {
			getBackBook(book);
		}
		else if (inputnumber == 4) {
			all_showBook(book);
		}
		else if (inputnumber == 5) {
			showBook(book);
		}
	} while ( inputnumber != 0);
	printf("감사합니다.\n");
	return 0;
}
```

