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

