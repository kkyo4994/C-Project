# library.c

[기본]

```c
#include <stdio.h>
#include <string.h>
#include "library.h"

static int bookCount = 0;
static int booknumber = 1;
```

[책 추가]

```c
void addBook(Book* book) {
	if (bookCount == MAX_BOOK_COUNT) {
		printf("책이 많습니다.\n");
		return;
	}
	printf("도서명을 입력해 주세요.\n");
	scanf("%s", book[bookCount].name);
	printf("책의 지은이를 입력해 주세요.\n");
	scanf("%s", book[bookCount].author);
	printf("책의 가격을 입력해 주세요.\n");
	scanf("%d", book[bookCount].pay);
	book[MAX_BOOK_COUNT].state = 0;
	book[MAX_BOOK_COUNT].number = booknumber;
	printf("책의 번호는 %d입니다.\n", booknumber);
	booknumber++;
	bookCount++;
	return;
}
```

[]

```c
int bookindex(Book* book, int NUMBER) {
	for (int i = 0; i < bookCount; i++) {
		if (book[bookCount].number == NUMBER) {
			return i;
		}
	}
	return -1;
}
```

[책 대출]

```c
void borrowBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum);
	Bookindex = bookindex(book, BookNum);
	if (-1 == Bookindex) {
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	if (book[Bookindex].state != 0){
		printf("현재 대출 상태인 책입니다.\n");
		return;
	}
	else book[Bookindex].state = 1;
		printf("대출이 되었습니다.\n");
		return;
}
```

[책 반납]

```c
void getBackBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum);
	Bookindex = bookindex(book, BookNum);
	if (-1 == Bookindex) {
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	if (book[Bookindex].state != 0) {
		book[Bookindex].state = 0;
		printf("반납이 되었습니다.\n");
		return;
	}
	return;
}
```

[모든 책 정보 출력]

```c
void all_showBook(Book* book) {
	for (int i = 0; i < bookCount; i++) {
		printf("도서명 : %s\n", book[i].name);
		printf("지은이 : %s\n", book[i].author);
		printf("가격 : %d\n", book[i].pay);
		printf("대출 현황 : %d\n", book[i].state);
	}
	return;
}
```

[특정 책 정보 출력]

```c
void showBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum);
	Bookindex = bookindex(book, BookNum);
	if (-1 ==  Bookindex) {
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	printf("도서명 : %s\n", book[Bookindex].name);
	printf("지은이 : %s\n", book[Bookindex].author);
	printf("가격 : %d\n", book[Bookindex].pay);
	printf("대출 현황 : %d\n", book[Bookindex].state);
	return;
}
```

