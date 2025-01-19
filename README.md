#include <iostream>
#include <string>
#include <vector>
#include <map>
using namespace std;

// Define a structure for a Book
struct Book {
    string title;
    string author;
    int publishYear;
    bool isBorrowed;
};

// Function to display book information
void displayBookInfo(const vector<Book>& books) {
    for (size_t i = 0; i < books.size(); i++) {
        cout << "Book " << i + 1 << ":" << endl;
        cout << "Title: " << books[i].title << endl;
        cout << "Author: " << books[i].author << endl;
        cout << "Publish Year: " << books[i].publishYear << endl;
        cout << "Borrowed: " << (books[i].isBorrowed ? "Yes" : "No") << endl;
        cout << "----------------------------" << endl;
    }
}

// Function to add a new book
void addBook(vector<Book>& books) {
    Book newBook;
    cout << "Enter title: ";
    cin.ignore();
    getline(cin, newBook.title);
    cout << "Enter author: ";
    getline(cin, newBook.author);
    cout << "Enter publish year: ";
    cin >> newBook.publishYear;
    cout << "Is the book borrowed? (1 for Yes, 0 for No): ";
    cin >> newBook.isBorrowed;

    books.push_back(newBook);
    cout << "Book added successfully!" << endl;
}

// Function to remove a book by its index
void removeBook(vector<Book>& books) {
    int index;
    cout << "Enter the index of the book to remove: ";
    cin >> index;

    if (index > 0 && index <= books.size()) {
        books.erase(books.begin() + index - 1);
        cout << "Book removed successfully!" << endl;
    } else {
        cout << "Invalid index!" << endl;
    }
}

// Function to search books by title
void searchBooksByTitle(const vector<Book>& books, const string& title) {
    bool found = false;
    for (size_t i = 0; i < books.size(); i++) {
        if (books[i].title == title) {
            cout << "Book found!" << endl;
            cout << "Title: " << books[i].title << endl;
            cout << "Author: " << books[i].author << endl;
            cout << "Publish Year: " << books[i].publishYear << endl;
            cout << "Borrowed: " << (books[i].isBorrowed ? "Yes" : "No") << endl;
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Book with title \"" << title << "\" not found." << endl;
    }
}

// Function to search books by author
void searchBooksByAuthor(const vector<Book>& books, const string& author) {
    bool found = false;
    for (size_t i = 0; i < books.size(); i++) {
        if (books[i].author == author) {
            cout << "Book found!" << endl;
            cout << "Title: " << books[i].title << endl;
            cout << "Author: " << books[i].author << endl;
            cout << "Publish Year: " << books[i].publishYear << endl;
            cout << "Borrowed: " << (books[i].isBorrowed ? "Yes" : "No") << endl;
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Book by author \"" << author << "\" not found." << endl;
    }
}

// Function to generate reading statistics
void generateStatistics(const vector<Book>& books) {
    int totalBooks = books.size();
    int borrowedBooks = 0;

    map<int, int> yearDistribution;

    for (const auto& book : books) {
        if (book.isBorrowed) {
            borrowedBooks++;
        }
        yearDistribution[book.publishYear]++;
    }

    // Display statistics
    cout << "Total number of books: " << totalBooks << endl;
    cout << "Number of borrowed books: " << borrowedBooks << endl;
    cout << "Year-wise distribution of books:" << endl;

    for (const auto& entry : yearDistribution) {
        cout << "Year " << entry.first << ": " << entry.second << " book(s)" << endl;
    }
}

int main() {
    vector<Book> books = {
        {"The Hobbit", "J.R.R. Tolkien", 1937, false},
        {"1984", "George Orwell", 1949, true},
        {"To Kill a Mockingbird", "Harper Lee", 1960, false},
        {"The Great Gatsby", "F. Scott Fitzgerald", 1925, true},
        {"Moby Dick", "Herman Melville", 1851, false},
        {"War and Peace", "Leo Tolstoy", 1869, true},
        {"Pride and Prejudice", "Jane Austen", 1813, false},
        {"The Catcher in the Rye", "J.D. Salinger", 1951, true},
        {"The Odyssey", "Homer", -800, false},
        {"Ulysses", "James Joyce", 1922, true}
    };

    int choice;
    do {
        cout << "1. Display Books" << endl;
        cout << "2. Add Book" << endl;
        cout << "3. Remove Book" << endl;
        cout << "4. Search Book by Title" << endl;
        cout << "5. Search Book by Author" << endl;
        cout << "6. Generate Reading Statistics" << endl;
        cout << "7. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                displayBookInfo(books);
                break;
            case 2:
                addBook(books);
                break;
            case 3:
                removeBook(books);
                break;
            case 4: {
                string title;
                cout << "Enter title to search: ";
                cin.ignore();
                getline(cin, title);
                searchBooksByTitle(books, title);
                break;
            }
            case 5: {
                string author;
                cout << "Enter author to search: ";
                cin.ignore();
                getline(cin, author);
                searchBooksByAuthor(books, author);
                break;
            }
            case 6:
                generateStatistics(books);
                break;
            case 7:
                cout << "Exiting..." << endl;
                break;
            default:
                cout << "Invalid choice! Please try again." << endl;
                break;
        }
    } while (choice != 7);

    return 0;
}
