# main.c



```c
#include <stdio.h>
#include <string.h>
#include "bank.h"

int main() {
	Acc acc[MAX_USER_COUNT];
	int inputNumber;
	do {
		printf("계좌 추가는 1, 계좌 삭제는 2, 계좌 관리는 3, 모든 계좌 보기는 4, 특정 계좌 보기는 5, 종료하시려면 0을 입력해 주세요.\n");
		scanf("%d", &inputNumber);
		if (inputNumber == 1) {
			addUser(acc);
		}
		else if(inputNumber == 2){
			printf("\n\n| %d |\n\n", acc[0].number);
			deleteUser(acc);
		}
		else if(inputNumber == 3){
			management(acc);
		}
		else if(inputNumber == 4){
			print_all_information(acc);
		}
		else if(inputNumber == 5){
			print_information(acc);
		}
	} while (inputNumber != 0);
	printf("꺼져.\n");
	return 0;
}
```



