# Library Management System - JDBC Connection

## Overview
This Java program establishes a connection to a MySQL database for a Library Management System. The system allows users to **log in, register, and manage books** by adding, deleting, updating, and retrieving book details.

## Features
- **User Authentication**  
  - Login with a username and password.
  - Signup with security questions for password recovery.
  - Check if a username is already taken.
- **Book Management**  
  - Add a new book to the library.
  - Remove a book by ID or name.
  - Update book details.
  - Retrieve book details by ID or name.

## Technologies Used
- Java
- MySQL
- JDBC

## Database Schema
### Users Table (`users`)
| Column            | Type         | Description             |
|------------------|-------------|-------------------------|
| `id`            | INT (Primary Key) | Unique user ID |
| `name`          | VARCHAR(255) | Full name of the user |
| `username`      | VARCHAR(255) (Unique) | Login username |
| `password`      | VARCHAR(255) | Encrypted password |
| `security_question` | VARCHAR(255) | Security question for account recovery |
| `answer`        | VARCHAR(255) | Answer to the security question |

### Books Table (`books`)
| Column      | Type         | Description             |
|------------|-------------|-------------------------|
| `book_id`  | INT (Primary Key) | Unique book identifier |
| `category` | VARCHAR(255) | Genre/category of the book |
| `name`     | VARCHAR(255) | Title of the book |
| `author`   | VARCHAR(255) | Author of the book |
| `copies`   | INT         | Number of available copies |

## Setup Instructions
### Prerequisites
- Install MySQL and create a database named **`library_db`**.
- Create the **`users`** and **`books`** tables using the schema above.
- Ensure **MySQL JDBC Driver** is included in the project dependencies.

### Running the Project
1. Clone or download the project.
2. Open the project in an IDE (Eclipse, IntelliJ, etc.).
3. Update the MySQL connection details in `JDBC_Connection.java`:
   ```java
   private static final String URL = "jdbc:mysql://127.0.0.1:3306/library_db";
   private static final String USER = "root";
   private static final String PASSWORD = ""; // Replace with your MySQL password
   ```
4. Compile and run the Java application.

## Usage
### User Authentication
- **Login:** Call `login(username, password)` to authenticate users.
- **Signup:** Use `signup(name, username, password, securityQuestion, answer)` to register a new user.
- **Check Username:** Call `isUsernameTaken(username)` to prevent duplicate usernames.

### Book Management
- **Add a Book:** Call `addBook(bookId, category, name, author, copies)`.
- **Remove a Book:** Call `removeBookByIdOrName(bookId, bookName)`.
- **Update Book Details:** Use `updateBook(bookId, category, name, author, copies)`.
- **Retrieve Book Details:** Call `getBookDetailsByIdOrName(bookId, bookName)`.

## Notes
- Passwords are stored in plain text. Consider using encryption for better security.
- SQL queries are executed using `PreparedStatement` to prevent SQL injection.

## License
This project is open-source and free to use under the MIT License.


