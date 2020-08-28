# library.h

```c
#ifndef __LIBRARY_H__
#define __LIBRARY_H__

#define MAX_BOOK_COUNT 3

typedef struct _BOOK {
	char name[20];
	char author[20];
	int pay;
	int state;
	int number;
} Book;

void addBook(Book* book);
int bookindex(Book* book, int NUMBER);
void borrowBook(Book* book);
void getBackBook(Book* book);
void all_showBook(Book* book);
void showBook(Book* book);

#endif __LIBRARY_H__
```

