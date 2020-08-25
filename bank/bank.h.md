# bank.h



```c
#ifndef __BANK_H__
#define __BANK_H__

#define MAX_USER_COUNT 3

typedef struct Account {
	char name[11]; // 이름(12글자가 최대라 했으니 수에 맞는지 검사)
	int balance; // 잔액
	int number; // 계좌 고유 번호
}Acc; // Account를 짧게 Acc로 부를 수 있다

void addUser(Acc* user); // 계좌 추가하는 함수
void deleteUser(Acc* user); // 계좌 삭제하는 함수
void management(Acc* user); // 계좌 관리하는 함수
int getIndex(Acc* user, int usernumber); // 계좌 추가하는 함수
void remittance(Acc* user); // 송금하는 함수
void deposit(Acc* user); // 입금하는 함수
void withdrawal(Acc* user); // 출금하는 함수
void print_information(Acc* user); // 특정 계좌 정보 출력하는 함수
void print_all_information(Acc * user); // 전체 계좌 정보 출력하는 함수

#endif
```

