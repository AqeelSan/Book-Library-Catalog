<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Book Library Catalog</title>
    <!-- Link to a CSS theme (Bootstrap in this case) -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body {
            padding-top: 50px;
        }
        .jumbotron {
            background-color: #f8f9fa;
        }
    </style>
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top">
        <a class="navbar-brand" href="#">Book Library Catalog</a>
    </nav>

    <div class="container">
        <div class="jumbotron">
            <h1 class="display-4">Welcome to the Book Library Catalog</h1>
            <p class="lead">A simple C++ application to manage a collection of books.</p>
            <hr class="my-4">
            <p>This application allows users to add, remove, search, and display book details, as well as generate reading statistics.</p>
            <a class="btn btn-primary btn-lg" href="https://github.com/yourusername/book-library-catalog" role="button">View on GitHub</a>
        </div>

        <section>
            <h2>Features</h2>
            <ul>
                <li>Add new books to the library</li>
                <li>Remove books by their index</li>
                <li>Search for books by title or author</li>
                <li>Display information about all books</li>
                <li>Generate reading statistics, including the total number of books, number of borrowed books, and year-wise distribution</li>
            </ul>
        </section>

        <section>
            <h2>Usage</h2>
            <ol>
                <li><strong>Display Books:</strong> Shows the details of all books in the library.</li>
                <li><strong>Add Book:</strong> Allows you to add a new book by entering its details.</li>
                <li><strong>Remove Book:</strong> Removes a book by its index in the list.</li>
                <li><strong>Search Book by Title:</strong> Searches for a book by its title.</li>
                <li><strong>Search Book by Author:</strong> Searches for books by an author.</li>
                <li><strong>Generate Reading Statistics:</strong> Displays statistics of the library collection.</li>
                <li><strong>Exit:</strong> Exits the program.</li>
            </ol>
        </section>

        <section>
            <h2>Contributing</h2>
            <p>Contributions are welcome! Please follow these steps to contribute:</p>
            <ol>
                <li>Fork the repository.</li>
                <li>Create a new branch: <code>git checkout -b feature-branch</code></li>
                <li>Make your changes and commit them: <code>git commit -m "Add new feature"</code></li>
                <li>Push to the branch: <code>git push origin feature-branch</code></li>
                <li>Open a pull request and provide a detailed description of your changes.</li>
            </ol>
        </section>

        <section>
            <h2>License</h2>
            <p>This project is licensed under the MIT License. See the <a href="LICENSE">LICENSE</a> file for details.</p>
        </section>
    </div>

    <footer class="text-center mt-5">
        <p>&copy; 2025 Book Library Catalog</p>
    </footer>

    <!-- Optional JavaScript for Bootstrap components -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.2/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
