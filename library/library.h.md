# library.h

```c
#ifndef __LIBRARY_H__ // __LIBRARY_H__이 main에 선언되어있지 않으면 실행
#define __LIBRARY_H__ // __LIBRARY_H__을 선언

#define MAX_BOOK_COUNT 3

typedef struct _BOOK {
	char name[20]; // 도서명
	char author[10]; // 지은이
	int pay; // 가격
	int state; // 대출 현황
	int number; // 책의 번호
} Book; // _BOOK를 짧게 Book로 부를 수 있다

void addBook(Book* book); // 책을 추가하는 함수
int bookindex(Book* book, int NUMBER); // 책의 인덱스를 가져오는 함수
void borrowBook(Book* book); // 책을 대출하는 함수
void getBackBook(Book* book); // 책을 반납하는 함수
void all_showBook(Book* book); // 모든 책의 정보를 출력하는 함수
void showBook(Book* book); // 특정 책의 정보를 출력하는 함수

#endif __LIBRARY_H__ // #define __LIBRARY_H__부터 여기까지 실행
```

