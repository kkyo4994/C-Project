# bank.c

[기본]

```c
#include <stdio.h>
#include <string.h>
#include "bank.h"

static int accCount = 0;
static int accNum = 1;
```

[계좌 추가]

```c
void addUser(Acc* user) {
	if(accCount==MAX_USER_COUNT){ // 만약 만든 계좌가 MAX_USER_COUNT(3)과 같으면 
		printf("계좌가 많습니다.\n"); // '계좌가 많습니다' 출력
		return;
	}
	printf("예금주명을 입력해 주세요.\n"); 
	scanf("%s", user[accCount].name); // 사용할 계좌의 이름을 입력
	user[accCount].balance = 0; // 계좌를 처음 만들었으니 계좌의 금액은 0
	user[accCount].number= accNum; // 
	printf("계좌 고유 번호는 %d입니다.\n", accNum);
	printf("계좌가 추가되었습니다.\n");
	accNum++; // 계좌가 추가 될 때마다 계좌의 겹치지 않게 고유번호가 1 늘어난다
	accCount++; // 계좌가 추가 될 때마다 계좌 수를 가르키는 함수의 수가 1 늘어난다
	return;
}
```

[계좌 삭제]

```c
void deleteUser(Acc* user) {
	int usernumber, index;
	printf("삭제할 계좌의 고유 번호를 입력하세요.\n");
	scanf("%d", &usernumber);
	index = getIndex(user, usernumber);
	if (0 <= index) {
		printf("계좌가 삭제되었습니다.\n"); 
			for (int i = index; i < accCount; i++) {
				strcpy(user[i].name, user[i + 1].name);
				user[i].balance = user[i + 1].balance;
				user[i].number = user[i + 1].number;
			}
			accCount--;
	}
	else {
		printf("없는 고유 번호이니, 다시 확인해 주세요.\n");
	}
	return;
}
```

