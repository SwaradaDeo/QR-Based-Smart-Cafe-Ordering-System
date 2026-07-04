# ☕ QR-Based Smart Café Ordering and Management System

A web-based application that digitalizes and automates the entire café ordering process. Customers scan a unique QR code placed on their table to access a digital menu, place orders, and pay — while the café admin manages everything in real time through a centralized dashboard.

---

## 📌 Overview

Traditional cafés rely on printed menus and manual order-taking, which leads to slow service, billing errors, and zero visibility into order status or business data. This project replaces that process with a contactless, self-service ordering system:

1. Customer scans a table's QR code → digital menu opens in the browser (no app install).
2. Customer registers/logs in, browses categorized items, adds to cart, and places the order.
3. The order instantly appears on the admin dashboard with table number, items, and total bill.
4. Admin updates the order status (`New → Preparing → Ready → Completed`), records payment, and tracks business reports.

---

## ✨ Features

### Customer
- Scan QR code for instant, automatic table identification
- Register / Login
- Browse categorized digital menu with images, descriptions & prices
- Add to cart, update quantities, remove items
- View itemized bill before placing order
- Place order with instant on-screen confirmation
- View order history and current order status
- Choose payment method (Cash / UPI / Card)
- Submit star ratings & written feedback
- Send messages via contact form
- View/download order receipt

### Admin
- Secure role-based admin login
- Real-time dashboard of all active orders
- Manage café tables and generate/assign QR codes
- Manage menu categories and items (add/edit/delete/availability)
- View and update order status
- Record and track payment status
- View and manage customer feedback & contact messages
- Business reports — total orders, total revenue, daily activity
- View list of registered customers

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript (ES6) |
| Backend | Java JDK 21, Servlet/JSP (Jakarta EE 10) |
| Database | MySQL 10.4.32 |
| Web Server | Apache Tomcat 10.1 |
| Architecture | MVC (Model-View-Controller) |
| QR Code Generation | ZXing (Zebra Crossing) Library |
| DB Connectivity | JDBC |

---

## 🏗️ Architecture

The system follows the **MVC** design pattern:

- **Model** — Java POJOs (`User`, `MenuItem`, `Order`, `Payment`, etc.)
- **View** — JSP pages rendering the HTML interface
- **Controller** — Java Servlets (`LoginServlet`, `RegisterServlet`, `MenuServlet`, `CartServlet`, `OrderServlet`, `PaymentServlet`, etc.) handling requests, business logic, and DAO calls

### Database Schema (`cafe_db`)
10 relational tables connected via foreign keys:

`users`, `tables`, `categories`, `menu_items`, `cart`, `orders`, `order_items`, `payments`, `feedback`, `contact_messages`

Key relationships:
- `User` 1—M `Order`
- `Table` 1—M `Order`
- `Category` 1—M `MenuItem`
- `Order` 1—M `OrderItem`
- `Order` 1—1 `Payment`
- `User` 1—M `Cart`, `User` 1—M `Feedback`

---

## 💻 System Requirements

**Server-side**
- OS: Windows 10+ / Linux
- Java JDK 21, Jakarta EE 10 (Servlet/JSP)
- Apache Tomcat 10.1
- MySQL 10.4.32
- RAM: 4 GB+, Processor: Intel Core i3+

**Client-side**
- Browser: Chrome / Firefox (v100+)
- Smartphone/Tablet/Laptop with camera (for QR scanning)
- RAM: 2 GB+

---

## 🚀 Getting Started

### Prerequisites
- JDK 21
- Apache Tomcat 10.1
- MySQL 10.4.32
- An IDE (Eclipse / IntelliJ IDEA) supporting Jakarta EE

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/qr-smart-cafe.git
   cd qr-smart-cafe
   ```

2. **Create the database**
   - Create a MySQL database named `cafe_db`
   - Run the provided SQL script (`/db/cafe_db.sql`) to create the 10 tables

3. **Configure DB connection**
   Update credentials in `DBConnection.java`:
   ```java
   private static final String URL = "jdbc:mysql://localhost:3306/cafe_db";
   private static final String USER = "root";
   private static final String PASSWORD = "root";
   ```

4. **Deploy**
   - Import the project into your IDE as a Dynamic Web Project / Maven project
   - Deploy on Apache Tomcat 10.1
   - Access via `http://localhost:8080/cafe/`

5. **Generate Table QR Codes**
   - Log in as admin → Tables & QR → Add Table → QR code is auto-generated (ZXing) and can be printed

---

## 📂 Project Modules

| Module | Description |
|---|---|
| User / Auth | Registration, login, role-based access |
| QR & Table | Table creation, QR generation, table identification |
| Category & Menu | CRUD for categories and menu items |
| Cart | Add/update/remove items, view cart summary |
| Order | Place order, view confirmation, admin order management |
| Payment | Record and verify payment per order |
| Feedback | Star ratings and comments |
| Contact | Customer messages to café |
| Reports | Revenue, order counts, daily summaries |

---

## ⚠️ Limitations

- No real online payment gateway integration (payments are recorded manually)
- No real-time push updates — customer must refresh to see order status changes
- No native mobile app (web-based only)
- Single café/branch support only
- No inventory/stock tracking
- No email/SMS notifications
- No OTP/email verification at registration
- Passwords are not hashed with a strong algorithm (e.g., bcrypt) in the current version

---

## 🔮 Proposed Enhancements

- Online payment gateway integration
- Real-time order tracking (WebSockets)
- Android/iOS mobile app
- Multi-branch café management
- Inventory & stock management
- Email/SMS notifications
- AI-based food recommendations
- OTP-based verification & stronger password encryption
- Online table reservation system
- Advanced sales & analytics dashboard

---

## 📚 References

1. Herbert Schildt – *Java: The Complete Reference*
2. Murach – *Java Servlets and JSP*
3. Jon Duckett – *HTML and CSS*
4. David Flanagan – *JavaScript: The Definitive Guide*
5. Ian Gilfillan – *MySQL: The Complete Reference*
6. Apache Tomcat Documentation
7. MySQL Documentation
8. Oracle Java Documentation
9. W3Schools
10. MDN Web Docs

---

## 👩‍💻 Author

**Swarada Suhas Deo**

---

## 📄 License

This project was developed for academic purposes as part of the MCA curriculum at Savitribai Phule Pune University (SPPU).
