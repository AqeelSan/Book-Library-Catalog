<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Book Library Catalog</title>
</head>
<body>
    <h1>Book Library Catalog</h1>
    <script>
        // Define a structure for a Book
        class Book {
            constructor(title, author, publishYear, isBorrowed) {
                this.title = title;
                this.author = author;
                this.publishYear = publishYear;
                this.isBorrowed = isBorrowed;
            }
        }

        const books = [
            new Book("The Hobbit", "J.R.R. Tolkien", 1937, false),
            new Book("1984", "George Orwell", 1949, true),
            new Book("To Kill a Mockingbird", "Harper Lee", 1960, false),
            new Book("The Great Gatsby", "F. Scott Fitzgerald", 1925, true),
            new Book("Moby Dick", "Herman Melville", 1851, false),
            new Book("War and Peace", "Leo Tolstoy", 1869, true),
            new Book("Pride and Prejudice", "Jane Austen", 1813, false),
            new Book("The Catcher in the Rye", "J.D. Salinger", 1951, true),
            new Book("The Odyssey", "Homer", 1800, false),
            new Book("Ulysses", "James Joyce", 1922, true)
        ];

        function toLowerCase(str) {
            return str.toLowerCase();
        }

        function displayBookInfo() {
            let output = "";
            books.forEach((book, index) => {
                output += `<div>
                    <h2>Book ${index + 1}:</h2>
                    <p>Title: ${book.title}</p>
                    <p>Author: ${book.author}</p>
                    <p>Publish Year: ${book.publishYear}</p>
                    <p>Borrowed: ${book.isBorrowed ? "Yes" : "No"}</p>
                    <hr>
                </div>`;
            });
            document.getElementById("book-info").innerHTML = output;
        }

        function addBook() {
            const title = prompt("Enter title:");
            const author = prompt("Enter author:");
            const publishYear = prompt("Enter publish year:");
            const isBorrowed = confirm("Is the book borrowed?");

            const newBook = new Book(title, author, publishYear, isBorrowed);
            books.push(newBook);
            alert("Book added successfully!");
            displayBookInfo();
        }

        function removeBook() {
            const index = prompt("Enter the index of the book to remove:");

            if (index > 0 && index <= books.length) {
                books.splice(index - 1, 1);
                alert("Book removed successfully!");
                displayBookInfo();
            } else {
                alert("Invalid index!");
            }
        }

        function searchBooksByTitleOrAuthor() {
            const input = prompt("Enter title or author to search:");
            let found = false;
            const lowerInput = toLowerCase(input);

            books.forEach((book) => {
                if (toLowerCase(book.title) === lowerInput || toLowerCase(book.author) === lowerInput) {
                    alert(`Book found!
                    Title: ${book.title}
                    Author: ${book.author}
                    Publish Year: ${book.publishYear}
                    Borrowed: ${book.isBorrowed ? "Yes" : "No"}`);
                    found = true;
                }
            });

            if (!found) {
                alert(Book with title or author "${input}" not found.);
            }
        }

        function generateStatistics() {
            const totalBooks = books.length;
            const borrowedBooks = books.filter(book => book.isBorrowed).length;

            const yearDistribution = books.reduce((acc, book) => {
                acc[book.publishYear] = (acc[book.publishYear] || 0) + 1;
                return acc;
            }, {});

            let distributionOutput = "";
            for (const year in yearDistribution) {
                distributionOutput += Year ${year}: ${yearDistribution[year]} book(s)<br>;
            }

            alert(`Total number of books: ${totalBooks}
            Number of borrowed books: ${borrowedBooks}
            Year-wise distribution of books:
            ${distributionOutput}`);
        }
    </script>
    <div>
        <button onclick="displayBookInfo()">Display Books</button>
        <button onclick="addBook()">Add Book</button>
        <button onclick="removeBook()">Remove Book</button>
        <button onclick="searchBooksByTitleOrAuthor()">Search Book by Title or Author</button>
        <button onclick="generateStatistics()">Generate Reading Statistics</button>
    </div>
    <div id="book-info"></div>
</body>
</html>
