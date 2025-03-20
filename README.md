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
(FUNCTION DEFINITION)
#include "Book.h"

// Initialize global arrays and counters
Book books[MAX_BOOKS];
Member members[MAX_MEMBERS];
int bookCount = 0;
int memberCount = 0;

// Function to add a new book
void addBook() {
    if (bookCount >= MAX_BOOKS) {
        cout << "Library is full! Can't add more books.\n";
        return;
    }

    cout << "Enter book title: ";
    cin.ignore();
    getline(cin, books[bookCount].title);
    cout << "Enter author name: ";
    getline(cin, books[bookCount].author);
    cout << "Enter ISBN number: ";
    getline(cin, books[bookCount].isbn);
    books[bookCount].isAvailable = true;

    cout << "Book added successfully!\n\n";
    bookCount++;
}

// Function to display all books
void displayBooks() {
    if (bookCount == 0) {
        cout << "No books in the library.\n\n";
        return;
    }

    cout << "Books in the Library:\n";
    for (int i = 0; i < bookCount; i++) {
        cout << i + 1 << ". " << books[i].title << " by " << books[i].author
             << " (ISBN: " << books[i].isbn << ") - "
             << (books[i].isAvailable ? "Available" : "Borrowed") << "\n";
    }
    cout << endl;
}

// Function to register a new member
void registerMember() {
    if (memberCount >= MAX_MEMBERS) {
        cout << "Member limit reached! Can't add more members.\n";
        return;
    }

    cout << "Enter member name: ";
    cin.ignore();
    getline(cin, members[memberCount].name);
    members[memberCount].id = memberCount + 1;

    cout << "Member registered successfully! ID: " << members[memberCount].id << "\n\n";
    memberCount++;
}
 Function to display all members
void displayMembers() {
    if (memberCount == 0) {
        cout << "No registered members.\n\n";
        return;
    }

    cout << "Registered Members:\n";
    for (int i = 0; i < memberCount; i++) {
        cout << "ID: " << members[i].id << " - " << members[i].name << "\n";
    }
    cout << endl;
}

// Function to borrow a book
void borrowBook() {
    if (memberCount == 0 || bookCount == 0) {
        cout << "No members or books available.\n\n";
        return;
    }

    int memberId, bookIndex;
    cout << "Enter member ID: ";
    cin >> memberId;

    if (memberId < 1 || memberId > memberCount) {
        cout << "Invalid member ID.\n\n";
        return;
    }

    displayBooks();
    cout << "Enter book number to borrow: ";
    cin >> bookIndex;

    if (bookIndex < 1 || bookIndex > bookCount || !books[bookIndex - 1].isAvailable) {
        cout << "Invalid choice or book already borrowed.\n\n";
        return;
    }

    books[bookIndex - 1].isAvailable = false;
    cout << members[memberId - 1].name << " borrowed \"" << books[bookIndex - 1].title << "\".\n\n";
}

// Function to return a book
void returnBook() {
    if (bookCount == 0) {
        cout << "No books in the library.\n\n";
        return;
    }

    int bookIndex;
    displayBooks();
    cout << "Enter book number to return: ";
    cin >> bookIndex;

    if (bookIndex < 1 || bookIndex > bookCount || books[bookIndex - 1].isAvailable) {
        cout << "Invalid choice or book already returned.\n\n";
        return;
    }

    books[bookIndex - 1].isAvailable = true
    cout << "Book returned successfully!\n\n";
}
main.cpp

