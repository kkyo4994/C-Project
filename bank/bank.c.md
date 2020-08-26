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
	scanf("%d", &usernumber); // 계좌의 고유번호를 입력받는다
	index = getIndex(user, usernumber);
	if (0 <= index) { // 만약 index가 0보다 크거나 같으면
		printf("계좌가 삭제되었습니다.\n"); 
			for (int i = index; i < accCount; i++) { 
				strcpy(user[i].name, user[i + 1].name);
				user[i].balance = user[i + 1].balance;
				user[i].number = user[i + 1].number;
			}
			accCount--; // 계좌 하나 삭제
	}
	else {
		printf("없는 고유 번호이니, 다시 확인해 주세요.\n");
	}
	return;
}
```

[계좌 관리]

```c
void management(Acc* user) {
	int controlNum;
	printf("송금을 하시려면 1, 입금을 하시려면 2, 출금을 하시려면 3을 입력해 주세요.\n");
	scanf("%d", &controlNum);
	if (controlNum == 1) { // 만약에 controlNum이 1이면
		remittance(user); 
	}
	else if (controlNum == 2) { // 만약에 controlNum이 2이면
		deposit(user);
	}
	else if (controlNum == 3) { // 만약에 controlNum이 3이면
		withdrawal(user);
	}
	else printf("없는 번호이니 다시 선택해 주세요.");
	return;
}
```



```c
int getIndex(Acc* user, int usernumber) {
	for (int i = 0; i < accCount; i++) {
		printf("%d | %d | %d\n", i, usernumber, user[i].number);
		if (user[i].number == usernumber) {
			return i;
		}
	}
	printf("return -1");
	return -1;
}
```

* 계좌관리 [송금]

```c
void remittance(Acc* user) {
	int myacc, youracc, money, myindex, yourindex;
	printf("당신의 계좌의 고유 번호를 입력해 주세요.\n");
	scanf("%d", &myacc); // 계좌의 고유 번호를 입력받는다
	myindex = getIndex(user, myacc); 
	if (-1 == myindex) { // myindex가 1이면
		printf("없는 번호이니 다시 입력해 주세요.\n");
		return;
	}
	printf("받을 사람의 계좌의 고유 번호를 입력해 주세요.\n");
	scanf("%d", &youracc); 
	yourindex = getIndex(user, youracc);
	if (-1 == yourindex) { // yourindex가 1이면
		printf("없는 번호이니 다시 입력해 주세요.\n");
		return;
	}
	printf("보낼 돈의 금액을 입력해 주세요.\n");
	scanf("%d", &money);
	if (user[myindex].balance < money) { // 만약 계좌 안에 있는 돈보다 보내려는 돈이 더 크면
		printf("돈이 부족합니다.\n");
		return;
	}
	user[myindex].balance -= money; 
	yourindex = getIndex(user, youracc);
	user[yourindex].balance += money;
	printf("돈이 보내졌습니다.\n");
	return;
}
```

* 계좌관리 [입금]

```c
void deposit(Acc* user) {
	int myacc, youracc, money, myindex;
	printf("당신의 계좌의 고유 번호를 입력해 주세요.\n");
	scanf("%d", &myacc);
	myindex = getIndex(user, myacc);
	if (-1 == myindex) {
		printf("없는 번호이니 다시 입력해 주세요.\n");
		return;
	}
	printf("입금할 돈을 입력해 주세요.\n");
	scanf("%d", &money);
	user[myindex].balance += money;
	printf("입금이 되었습니다.\n");
	return;
}
```

* 계좌관리 [출금]

```c
void withdrawal(Acc* user) {
	int myacc, money, myindex;
	printf("당신의 계좌의 고유 번호를 입력해 주세요.\n");
	scanf("%d", &myacc);
	myindex = getIndex(user, myacc);
	if (-1 == myindex) {
		printf("없는 번호이니 다시 입력해 주세요.\n");
		return;
	}
	printf("출금할 금액을 입력해 주세요.\n");
	scanf("%d", &money);
	user[myindex].balance -= money;
	printf("출금이 되었습니다.\n");
	return;
}
```

[전체 계좌 정보 보기]

```c
void print_all_information(Acc* user) {
	for (int i = 0; i < accCount; i++) {
		printf("예금주 명 : %s\n", user[i].name);
		printf("현재 잔액 : %d\n", user[i].balance);
		printf("계좌 고유 번호 : %d\n", user[i].number);
	}
	return;
}
```

[특정 계좌 정보 보기]

```c
void print_information(Acc* user) {
	int uniqueNumber, myindex;
	printf("당신의 계좌의 고유 번호를 입력해 주세요.\n");
	scanf("%d", &uniqueNumber);
	myindex = getIndex(user, uniqueNumber);
	if (-1 == myindex) {
		printf("없는 번호이니 다시 입력해 주세요.\n");
		return;
	}
	printf("예금주 명 : %s\n", user[myindex].name);
	printf("현재 잔액 : %d\n", user[myindex].balance);
	printf("계좌 고유 번호 : %d\n", user[myindex].number);
	return;
}
```

