# Library-Management-system
#ifndef BOOK_H
#define BOOK_H

#include <iostream>
#include <string>
using namespace std;

// Book structure to store book details
struct Book {
    string title;
    string author;
    string isbn;
    bool isAvailable;
};

// Member structure to store member details
struct Member {
    string name;
    int id;
};

// Arrays to store books and members
const int MAX_BOOKS = 100;
const int MAX_MEMBERS = 50;
extern Book books[MAX_BOOKS];
extern Member members[MAX_MEMBERS];

extern int bookCount;
extern int memberCount;

void addBook();
void displayBooks();
void registerMember();
void displayMembers();
void borrowBook();
void returnBook();

#endif
