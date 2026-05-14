# Library-management-system
# Library Management System

A full-stack web application for managing library operations, built with PHP using an MVC architecture. Supports role-based access for admins, librarians, and members, covering everything from book inventory to borrowing, fines, and digital books.

##  Built With

- **Backend:** PHP (custom MVC framework)
- **Database:** MySQL
- **Frontend:** PHP Views, HTML, CSS
- **Design Patterns:** Singleton, Observer

##  Features

**Book Management**
- Add, edit, delete, and search physical and digital books
- Track ISBN, author, publisher, category, and available copies
- Automatic copy count updates on borrow/return

**User & Member Management**
- Role-based access: Admin, Librarian, Member
- Member registration, editing, suspension
- Secure password hashing

**Borrowing & Transactions**
- Issue and return books
- Track issue date, due date, and return date
- Automatic overdue status detection
- Self-service book return for members

**Fines System**
- Automatic fine calculation for overdue returns
- Track unpaid fines and mark them as paid

**Reservations**
- Members can reserve unavailable books
- Notification system alerts members when a reserved book becomes available

**Digital Books**
- Upload and manage downloadable PDF books
- Members can access digital content through the platform

**Notification System (Observer Pattern)**
- Notifies reservation holders when a book is returned
- Extensible for email/SMS integration

##  Design Patterns

**Singleton** — ensures a single shared database connection across the entire application lifecycle, improving performance and consistency.

**Observer** — decouples the notification logic from the transaction flow. When a book is returned, `BookAvailabilitySubject` notifies all registered observers (e.g. `UserNotificationObserver`) without the controller needing to know the details.

##  Database Schema

| Table | Description |
|---|---|
| `books` | Physical book catalogue with copy tracking |
| `users` | All users with roles and status |
| `transactions` | Borrow/return records with dates and status |
| `fines` | Overdue fines linked to transactions |
| `reservations` | Member book reservation queue |
| `digital_books` | Uploaded PDF books |


##  Setup

**Requirements:** PHP, MySQL, Apache (with mod_rewrite enabled)

1. Clone the repo and place it in your web server's root directory
2. Import `lms_database.sql` into MySQL
3. Update database credentials in `App/Config/config.php`:
   ```php
   define("DB_HOST", "localhost");
   define("DB_USER", "your_username");
   define("DB_PASS", "your_password");
   define("DB_NAME", "lms_database");
   ```
4. Update the base URL in `config.php` to match your local setup
5. Visit `http://localhost/lib/public/` in your browser

**Default admin credentials:** set via `fix_admin_user.php` on first run.

---
*Academic project — Misr International University, Software Engineering coursework*
