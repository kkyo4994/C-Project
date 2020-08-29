# library.c

[기본]

```c
#include <stdio.h> // 기본 함수들이 선언된 헤더 파일
#include <string.h> // strcpy 함수가 선언된 헤더 파일
#include "library.h" //  정의 함수들이 선언된 헤더 파일

static int bookCount = 0; // 정적 변수 선언 및 값 초기화[책의 갯수를 의미]
static int booknumber = 1; // accNum을 정적 변수 선언 및 값을 1 설정 [책의 번호를 의미]
```

[책 추가]

```c
void addBook(Book* book) { 
	if (bookCount == MAX_BOOK_COUNT) { // 만약 bookCount가 MAX_BOOK_COUNT의 수와 같다면
		printf("책이 많습니다.\n");
		return;
	}
	printf("도서명을 입력해 주세요.\n");
	scanf("%s", book[bookCount].name); // 책의 도서명을 입력
	printf("책의 지은이를 입력해 주세요.\n");
	scanf("%s", book[bookCount].author); // 책의 지은이을 입력
	printf("책의 가격을 입력해 주세요.\n");
	scanf("%d", book[bookCount].pay); // 책의 가격을 입력
	book[MAX_BOOK_COUNT].state = 0; // 대출현황은 빌릴 수 있는 0 상태
	book[MAX_BOOK_COUNT].number = booknumber; // 책 배열의 숫자에 booknumber를 저장
	printf("책의 번호는 %d입니다.\n", booknumber);
	booknumber++; // 책의 번호 1씩 늘리기(책의 번호들이 겹치지 않게)
	bookCount++; // 책의 갯수도 늘리기
	return;
}
```

[책의 인덱스를 가져온다]

```c
int bookindex(Book* book, int NUMBER) {
	for (int i = 0; i < bookCount; i++) { // 0부터 bookCount보다 작을 때만 반복
		if (book[bookCount].number == NUMBER) { // 만약 입력한 숫자가 책들의 번호들 중에 있으면
			return i; // 그렇다면 i를 반환
		}
	}
	return -1; // 아니면 -1를 반환
}
```

[책 대출]

```c
void borrowBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum); // 책의 번호를 입력
	Bookindex = bookindex(book, BookNum); // Bookindex에 bookindex를 실행
	if (-1 == Bookindex) { // 만약 Bookindex가 1이면
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	if (book[Bookindex].state != 0){ // 만약 책의 대출 현황이 0이 아니면
		printf("현재 대출 상태인 책입니다.\n");
		return;
	}
	else { // 그렇지 않으면
		book[Bookindex].state = 1; // 책의 대출 현황을 1로 바꾼다
		printf("대출이 되었습니다.\n");
		return;
	}
	return;
}
```

[책 반납]

```c
void getBackBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum); // 책의 번호를 입력
	Bookindex = bookindex(book, BookNum); // Bookindex에 bookindex를 실행
	if (-1 == Bookindex) { // 만약 Bookindex가 1이면
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	if (book[Bookindex].state != 0) {
		book[Bookindex].state = 0;
		printf("반납이 되었습니다.\n");
		return;
	}
	else printf("대출이 안 되어있는 책입니다.\n");
	return;
}
```

[모든 책 정보 출력]

```c
void all_showBook(Book* book) {
	for (int i = 0; i < bookCount; i++) { // 0부터 bookCount보다 작을 때만 반복
		printf("도서명 : %s\n", book[i].name);
		printf("지은이 : %s\n", book[i].author);
		printf("가격 : %d\n", book[i].pay);
        // 차례대로 도서명과 지은이와 가격이 출력
		if (book[i].state == 0) { // 만약 책의 대출 현황이 0이면
			printf("대출 현황 : 대출을 할 수 있습니다.\n");
		} 
		else printf("대출 현황 : 대출이 되어있습니다.\n");
	}
	return;
}
```

[특정 책 정보 출력]

```c
void showBook(Book* book) {
	int BookNum, Bookindex;
	printf("책의 번호를 입력해 주세요.\n");
	scanf("%d", &BookNum); // 책의 번호 입력
	Bookindex = bookindex(book, BookNum); // Bookindex에 bookindex를 실행
	if (-1 ==  Bookindex) { // 만약 Bookindex가 1이면
		printf("없는 번호니, 다시 확인해 주세요.\n");
		return;
	}
	printf("도서명 : %s\n", book[Bookindex].name);
	printf("지은이 : %s\n", book[Bookindex].author);
	printf("가격 : %d\n", book[Bookindex].pay);
	if (book[Bookindex].state == 0) { // 만약 책의 대출 현황이 0이면
			printf("대출 현황 : 대출을 할 수 있습니다.\n");
		} 
		else printf("대출 현황 : 대출이 되어있습니다.\n");
	}
    // 차례대로 입력받은 숫자의 인덱스를 가진 책들의 도서명과 지은이와 가격 출력
	return;
}
```

