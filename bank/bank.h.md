# bank.h



```c
#ifndef __BANK_H__
#define __BANK_H__

#define MAX_USER_COUNT 3

typedef struct Account {
	char name[11]; // 이름 (자세한 설명은 밑에서)
	int balance; // 잔액
	int number; // 계좌 고유 번호
}Acc; // Account를 짧게 Acc로 부를 수 있다

void addUser(Acc* user); // 계좌 추가하는 함수
void deleteUser(Acc* user); // 계좌 삭제하는 함수
void management(Acc* user); // 계좌 관리하는 함수
int getIndex(Acc* user, int usernumber); // 계좌의 인덱스를 가져오는 함수(계좌 배열의 인덱스를 가져올 수 있는)
void remittance(Acc* user); // 송금하는 함수
void deposit(Acc* user); // 입금하는 함수
void withdrawal(Acc* user); // 출금하는 함수
void print_information(Acc* user); // 특정 계좌 정보 출력하는 함수
void print_all_information(Acc * user); // 전체 계좌 정보 출력하는 함수

#endif
```



* 배열의 인덱스는 언제나 0부터 시작한다. 이때 조건 중 이름이 최대 12글자라고 하니 배열 길이를 11이라고 해야 한다. 
