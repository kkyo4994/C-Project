# bank.h



```c
#ifndef __BANK_H__ // __BANK_H__이 main에 선언되어있지 않으면 실행
#define __BANK_H__ // __BANK_H__를 선언

#define MAX_USER_COUNT 3

typedef struct Account {
	char name[12]; // 이름 (자세한 설명은 밑에서)
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

#endif // #define __BANK_H__부터 여기까지 실행
```

#ifndef ~ #endif

-> 쓰는 이유는 include(헤더파일)가 중복으로 겹치지 않고 오류가 발생하지 않게 하기 위해 쓰인다.



* 문자열은 항상 마지막 공간에 널문자(\0)이 추가되어야 한다. 널문자가 추가되어야 하면 문자의 갯수 + 1에 해당하는 크기를 할당해야 한다. 이때 조건 중 최대 12글자라고 하니, 0~11은 총 12개 + 1 이다. 따라서 배열 길이를 12이라고 해야 한다.  
