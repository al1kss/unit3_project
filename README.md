![dd](https://github.com/user-attachments/assets/21aa52c9-d205-4657-a756-9f1e1c3acc35)
# Unit 3: Restaraunt Manager

## Criteria A: Planning

## Problem definition
The owner of "NomNom" has observed a noticeable dip in customer satisfaction and order accuracy, primarily due to an outdated system that relies on phone orders and manual entry. Without a centralized digital record, errors occur frequently—from incorrect orders to miscommunications between the front of house and kitchen. This disjointed process not only leads to delays and disputes over order details but also prevents efficient tracking of customer interactions and order histories. The need for a robust system that automates order processing and streamlines communication between customers and staff has become critical to restore operational efficiency and enhance customer trust.

## Proposed Solution
I propose developing an intuitive, cross-platform application designed to streamline the ordering process for a modern pizza restaurant. The app will feature a dynamic graphical user interface that enables customers to effortlessly browse a visually rich menu, customize their pizzas, and place orders with confidence. Every order will be securely recorded, ensuring complete transparency and accuracy, while updates are sent directly to the kitchen and delivery teams, reducing errors and enhancing efficiency.

Python is the ideal language for this project because of its inherent versatility across both Intel x86 and ARM architectures and its strong support on multiple operating systems. Its extensive library ecosystem accelerates development, making it easier to integrate additional features and maintain the application over time.

For the graphical interface, the solution leverages the Kivy framework combined with KivyMD. Kivy’s adaptive design ensures the app looks and performs well on devices with different screen sizes and resolutions, which is critical for delivering a consistent user experience. Meanwhile, KivyMD introduces Material Design components that offer a sleek, modern appearance along with intuitive touch-friendly interactions. This combination not only simplifies the development process but also minimizes unexpected behavior, ensuring a stable and polished final product.

Data management is addressed with SQLite, a robust relational database that is well-suited for handling the app’s complex and interconnected data—from customer profiles and order histories to detailed menu information. SQLite’s lightweight, embedded nature guarantees rapid data access even in environments with limited connectivity, and its serverless design helps keep operating costs low while ensuring scalability as the restaurant expands.

Overall, this solution provides a secure, efficient, and user-friendly platform that improves order accuracy, enhances customer satisfaction, and streamlines operations for both the front of house and the back kitchen.

## Success Criteria
1. Robust Authentication System:
The app must include secure login and registration for both customers and staff, ensuring access is limited to verified users.

2. Intuitive Menu and Order Placement:
Users are able to view detailed descriptions of pizzas, choose from various customization options, and easily place their orders, reducing the likelihood of order discrepancies.

3. Immediate Staff Notice:
Kitchen and delivery staff should receive real-time change on the app when an order is placed, enabling them to prepare and dispatch orders promptly.

4. Modification of Food Listings:
The admin account can add or edit food listings through the pizza app

5. Secure and Efficient Data Storage:
All transaction data, including user credentials, order details, and menu information, must be securely stored in an SQLite database. This ensures data integrity, easy retrieval, and minimal risk of unauthorized access.



# Criterion B: Design


## Record of Tasks
| Task No |                                                Planned Action                                                |                                                Planned Outcome                                               | Time Estimate | Target Completion Date | Criterion |
|:-------:|:------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------:|:-------------:|:----------------------:|:---------:|
| 1       | Define project requirements and scope for a food ordering system with admin controls                         | Clear objectives for both user (ordering) and admin (order management) functionalities                       | 1 hour        | Feb 28                 | A         |
| 2       | Design database schema for users, menu, and orders (login.sql, menu.sql, orders.sql)                         | A robust, normalized database structure supporting secure login, dynamic menus, and order tracking           | 1 hour        | March 1                | A         |
| 3       | Implement secure login screen using encrypted passwords and role differentiation (user vs. admin)            | Users can securely log in and the system correctly identifies admin users for additional functionalities     | 1.5 hours     | March 1                | A         |
| 4       | Create a registration screen with validations to prevent duplicate usernames/emails                          | New users can register with error handling for empty or duplicate fields                                     | 1.5 hours     | March 1                | A         |
| 5       | Develop the Main Screen to dynamically load menu items from the menu database                                | A responsive menu display with KivyMD cards representing each pizza item                                     | 2 hours       | March 2                | B         |
| 6       | Integrate an “Add Pizza” card for admin users on the Main Screen                                             | Admins can add new pizzas to the menu directly from the Main Screen                                          | 1 hour        | March 2                | B         |
| 7       | Build the Cart Screen to manage item addition, removal, and quantity updates                                 | Users can easily manage their cart and view the total price before checkout                                  | 2 hours       | March 2                | B         |
| 8       | Develop the checkout process that assigns a unique ticket number and saves orders to orders.sql              | Orders are correctly recorded in the database with a unique identifier and default status ("Awaiting")       | 1 hour        | March 2                | A         |
| 9       | Create the Admin Orders Screen to display all orders (sorted newest first)                                   | Admins have a clear, chronological list of all orders for review and management                              | 2 hours       | March 3                | A         |
| 10      | Integrate an order status dropdown using MDDropdownMenu in each row to update status                         | Admins can change an order's status (from "Awaiting" to "done") directly from the order list                 | 4 hours       | March 3                | A         |
| 11      | Implement the update_order_status function to modify the status in the orders database                       | Real-time updates of order status in the database ensure that changes are immediately reflected in the UI    | 1 hour        | March 4                | A         |
| 12      | Debug and fix the order_data handling in OrderItemRow by padding missing fields with default values          | Prevent IndexError by ensuring every order_data list contains all 7 expected elements before being displayed | 1 hour        | March 4                | A         |
| 13      | Refactor and standardize the UI across login, menu, cart, and admin orders screens                           | A consistent and user-friendly design throughout the application                                             | 1 hour        | March 5                | B         |
| 14      | Test all user flows—registration, login, menu navigation, cart management, checkout, and admin order updates | Identify and fix bugs to ensure a stable and reliable application                                            | 2 hours       | March 5                | B         |
| 15      | Integrate error handling and user feedback for data input and screen transitions                             | Enhanced robustness and improved user experience with clear error messages                                   | 1 hour        | March 6                | B         |
| 16      | Document key coding techniques, design decisions, and database interactions used throughout the project      | A detailed record for future reference and for stakeholders to understand the code architecture              | 1.5 hours     | March 8                | B         |
| 17      | Record a demonstration video showing the application’s functionality from both the user and admin views      | A concise demo that clearly illustrates all core features and interactions of the application                | 1 hour        | March 9                | C         |
| 18      | Review and add inline comments to clarify complex sections of the code                                       | Improved code readability and easier maintenance for future developers                                       | 45 minutes    | March 10               | C         |
| 19      | Optimize SQL queries used for loading menu items and orders to improve performance                           | Faster data retrieval leading to a more responsive application                                               | 1 hour        | March 11               | B         |
| 20      | Working on UML, System Diagram for Criterion B                                                               | Clear diagrams for easy program underdansting                                                                | 4 hours       | March 11               | B         |
| 21      | Conduct a final review meeting with the client to demonstrate the completed application and gather feedback  | Client approval and confirmation that the application meets all defined success criteria                     | 1 hour        | March 11               | A         |


# Criterion C: Development

### 1. Secure and Efficient Data Storage – #Success Criteria 5
To meet success criterion 5, I ensured that all transaction data—including user credentials, menu information, and order details—is securely stored in an SQLite database. This strategy guarantees data integrity, facilitates easy retrieval, and minimizes the risk of unauthorized access.

My project utilizes separate SQLite databases to logically partition different types of data:

#### User Authentication (login.sql):
The 'user' table stores user credentials and role information. This table enforces uniqueness for usernames and emails while using role-based access to distinguish between regular users and administrators. For example:
```.py
CREATE TABLE IF NOT EXISTS user(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT UNIQUE,
    email TEXT UNIQUE,
    password VARCHAR(256),
    type TEXT DEFAULT 'user'
);
```
#### Menu Data (menu.sql):
The 'menu' table holds details of each pizza item, such as the name, description, price, and image filename. This design ensures that menu items are unique and contain all the necessary details for display:
```.py
CREATE TABLE IF NOT EXISTS menu(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT UNIQUE NOT NULL,
    description TEXT NOT NULL,
    price REAL NOT NULL,
    image TEXT DEFAULT 'pizza.png'
);
```
#### Order Details (orders.sql):
The 'orders' table records every order made by users. Each order includes the user ID, user email, item name, official price, a generated ticket number, and a default status of “Awaiting”. This structure allows for efficient order tracking and enables admin users to update the order status:
```.py
CREATE TABLE IF NOT EXISTS orders(
    order_id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER,
    user_email TEXT,
    item_name TEXT,
    item_price REAL,
    ticket_number TEXT,
    status TEXT DEFAULT 'Awaiting'
);
```
#### I used AutoIncrement for all IDs since, AutoIncrement is a feature in SQL that allows you to automatically generate unique values for a column when new rows are inserted into a table
#### Password Security
To safeguard user credentials, I implemented password hashing using a custom module named 'secure_password'. This module provides two key functions:
- 'encrypt_password(password)': Hashes the plain-text password (using a secure SHA-256 algorithm) before storing it in the database.
- 'check_password(user_password, hashed_password)': Verifies the provided password during login by comparing its hash with the stored hash.
For example, during registration:
```.py
password_hash = encrypt_password(password)
db.run_save(f"INSERT INTO user(username, email, password) VALUES ('{username}', '{email}', '{password_hash}')")
```
And during login:
```.py
user_info = db.search(f"SELECT * FROM user WHERE username='{username}'")
if user_info and check_password(user_password=password, hashed_password=user_info[0][3]):
    print("Login successful!")
```
This method protects sensitive data by ensuring that even if the database is compromised, actual passwords remain undisclosed.
#### Data Integrity and Retrieval
- Accurate Billing:
-- When an order is placed, the system fetches the official price from the 'menu.sql' database to ensure accurate billing.
- Role-based Access:
-- The user type stored in the 'user' table facilitates role-based access control, ensuring that only admins can access certain features (e.g., updating order statuses).
- Transaction Consistency:
-- The checkout process writes order data to 'orders.sql' with a unique ticket number and default status, ensuring that each order is recorded reliably.
