# **BASIC CRUD APP - PHP, MySQL**

Welcome to the **BASIC CRUD APP**! This is a simple yet robust web application that allows users to manage their profiles using basic CRUD (Create, Read, Update, Delete) operations. The app is built using **PHP**, **MySQL**, **HTML**, and **CSS**, making it an excellent example of how to build dynamic web applications with a secure backend.

---

## **Table of Contents**
- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Security Measures Implemented](#security-measures-implemented)
- [License](#license)

---

## **Introduction**

The **BASIC CRUD APP** is designed to provide a simple user interface where users can create, view, update, and delete their profile data. The project connects a **MySQL** database for storing user information and employs **PHP** for server-side logic. This application showcases how to effectively handle form data, interact with a database, and manage user sessions in a web environment.

The project also emphasizes **security**, ensuring that user data is protected from common web vulnerabilities. 

---

## **Features**

- **User Profile Management**: Users can create, update, and delete their profiles.
- **User Details Display**: View your profile in a clean and simple interface.
- **Secure Authentication**: Users can securely log in and access their dashboard.
- **Responsive Design**: The app is mobile-friendly and works on any screen size.
- **Easy Setup**: All necessary files and instructions for quick deployment.

---

## **Technologies Used**

- **Frontend**: HTML, CSS (with Flexbox), JavaScript
- **Backend**: PHP
- **Database**: MySQL
- **Security**: Prepared Statements, Password Hashing, Session Management, Input Validation
- **Additional Libraries**: None

---

## **Setup & Installation**

### Step 1: Clone the Repository

Clone the project repository to your local machine:

```bash
git clone https://github.com/yourusername/BASIC_CRUD_APP.git


Step 2: Install WAMP/XAMPP
If you don’t already have it, download and install WAMP or XAMPP, which will provide the necessary Apache server, MySQL, and PHP setup.

Step 3: Create the Database
Open phpMyAdmin (or MySQL Workbench).
Create a new database named blog1.
Import the db_schema.sql file from the project directory to create the required tables.
Step 4: Update Database Credentials
Open the db_connection.php file located in the includes/ folder.
Update the database connection details ($servername, $username, $password, and $dbname) to match your local MySQL configuration.
Step 5: Run the Application
Start your Apache and MySQL servers via WAMP/XAMPP.
Navigate to http://localhost/BASIC_CRUD_APP/ in your web browser.
Usage
Login: Users can log in using their credentials (create, update, and view profiles).
Dashboard: After logging in, users are directed to their dashboard where they can update their profile information.
Edit Profile: Users can edit their profile details such as name, email, etc.
Logout: Users can log out to secure their account.
Security Measures Implemented
💡 Security Measures Highlighted
The security of this application is a top priority. Several key security measures have been implemented to ensure the integrity of user data:

🔒 1. Prepared Statements for Database Queries
SQL Injection is prevented by using prepared statements. These statements ensure that user inputs are handled as data, not executable code. This is one of the most critical security practices to avoid harmful SQL queries.

Example:

php
Copy code
$stmt = $conn->prepare("SELECT * FROM users WHERE id = ?");
$stmt->bind_param("i", $user_id);
$stmt->execute();
🔐 2. Password Hashing
User passwords are hashed using PHP’s built-in password_hash() function. This ensures that passwords are never stored in plain text in the database, protecting sensitive user data.

Example:

php
Copy code
$hashed_password = password_hash($password, PASSWORD_DEFAULT);
During login, passwords are verified using password_verify() to ensure secure authentication.

🛡️ 3. Input Validation and Sanitization
User inputs are validated and sanitized using PHP’s built-in functions to prevent malicious data from entering the system. For example, emails are validated, and strings are sanitized to ensure no harmful code is executed.

Example:

php
Copy code
$username = filter_var($_POST['username'], FILTER_SANITIZE_STRING);
$email = filter_var($_POST['email'], FILTER_VALIDATE_EMAIL);
🔑 4. Session Management
Sessions are used to keep track of user authentication. Session IDs are unique for each user, and the session is securely destroyed during logout to prevent unauthorized access to the user dashboard.

Example:

php
Copy code
session_start();
if (!isset($_SESSION['user_id'])) {
    header('Location: login.php');
}
