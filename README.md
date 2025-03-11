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
The `user` table stores user credentials and role information. This table enforces uniqueness for usernames and emails while using role-based access to distinguish between regular users and administrators. For example:
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
The `menu` table holds details of each pizza item, such as the name, description, price, and image filename. This design ensures that menu items are unique and contain all the necessary details for display:
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
The `orders` table records every order made by users. Each order includes the user ID, user email, item name, official price, a generated ticket number, and a default status of “Awaiting”. This structure allows for efficient order tracking and enables admin users to update the order status:
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
To safeguard user credentials, I implemented password hashing using a custom module named `secure_password`. This module provides two key functions:
- `encrypt_password(password)`: Hashes the plain-text password (using a secure SHA-256 algorithm) before storing it in the database.
- `check_password(user_password, hashed_password)`: Verifies the provided password during login by comparing its hash with the stored hash.
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
-- When an order is placed, the system fetches the official price from the `menu.sql` database to ensure accurate billing.
- Role-based Access:
-- The user type stored in the `user` table facilitates role-based access control, ensuring that only admins can access certain features (e.g., updating order statuses).
- Transaction Consistency:
-- The checkout process writes order data to `orders.sql` with a unique ticket number and default status, ensuring that each order is recorded reliably.


### 2. Modification of Food Listings – #Success Criteria 4
To meet success criterion 4, I implemented a system where only admin users can add or modify food listings in the pizza app. This ensures that regular users cannot alter the menu, maintaining control over available food options. Below is a detailed explanation of how this functionality is achieved.
#### Restricting Access to Admin Users
The system ensures that only admin users can modify the food menu using the `LoginScreenReal.current_user_type` variable. This variable stores the user type and determines if an "Add Pizza" button is displayed.

#### Admin-Only Add Button
In the `MainScreen` class, when loading the menu, the system checks whether the logged-in user is an admin:
```.py
if LoginScreenReal.current_user_type == "admin":
    container.add_widget(AddPizzaCard())
```
- If the current user is an admin, an instance of `AddPizzaCard` is added to the screen.
- If the user is not an admin, they do not see the button and cannot add new food items.

#### Adding a New Pizza Item
When an admin clicks the "Add Pizza" button, a pop-up (`MDDialog`) appears, allowing them to input details for a new pizza.
#### Pop-Up Dialog for Admins
The `show_add_pizza_dialog()` function constructs a form for adding new food items:
```.py
self.pizza_name = MDTextField(hint_text="Pizza Name")
self.pizza_desc = MDTextField(hint_text="Description")
self.pizza_price = MDTextField(hint_text="Price", input_type="number")
self.pizza_image = MDTextField(hint_text="Image Filename", text="pizza.png")
```
- Admins enter the name, description, price, and image filename of the pizza.
- Two buttons are present:
- `"Cancel"` – closes the pop-up.
- `"Add"` – calls the `add_pizza_to_db()` function to store the new pizza.

#### Storing the New Pizza in the Database
Once the admin submits the form, the `add_pizza_to_db()` function processes the data:
```.py
query = f"""
INSERT INTO menu (name, description, price, image)
VALUES ('{name}', '{description}', {price}, '{image}')
"""
db.run_save(query)
```

### Immediate Staff Notice - #Success Criteria 3
This functionality ensures that kitchen and delivery staff receive real-time updates on new orders, allowing them to prepare and dispatch items promptly. The implementation includes an admin order management screen that dynamically updates with the latest orders and enables staff to change order statuses.
#### Key Components
1. `OrderItemRow` Class (Order Representation)
2. `AdminOrdersScreen` Class (Order Management)
3. 
#### Kivy KV Layout for UI Representation
Explanation of `OrderItemRow`
```.py
class OrderItemRow(MDCard):
    order_data = ListProperty()
```

- The `OrderItemRow` class represents individual orders in the admin panel.
- The `ListProperty` stores order details (e.g., order ID, customer email, item name, price, ticket number, and status).
#### Initializing Order Data
```.py
 def __init__(self, order_data, **kwargs):
        padded_data = list(order_data)
        if len(padded_data) < 7:
            defaults = ["Unknown", "Unknown", "Unknown", "Unknown", 0, "Unknown", "Awaiting"]
            padded_data += defaults[len(padded_data):]
        kwargs["order_data"] = padded_data
        super().__init__(**kwargs)
```
- This method ensures that incomplete order data is padded with default values.
- The `kwargs` dictionary ensures that the parent class ('MDCard') is initialized correctly.
- Why this approach? It prevents crashes due to missing data and guarantees UI consistency.

#### Handling Order Status Changes
```.py
    def open_status_menu(self):
        if not self.menu:
            menu_items = [
                {"text": "Awaiting", "viewclass": "OneLineListItem", "on_release": lambda x="Awaiting": self.set_status(x)},
                {"text": "Done", "viewclass": "OneLineListItem", "on_release": lambda x="Done": self.set_status(x)},
            ]
            self.menu = MDDropdownMenu(
                caller=self.ids.status_dropdown,
                items=menu_items,
                width_mult=4,
            )
        self.menu.open()
```
- The `open_status_menu` method creates a dropdown menu to update an order’s status.
- Why a dropdown menu? It simplifies UI interaction, preventing manual text entry errors.

```.py
    def set_status(self, new_status):
        self.ids.status_dropdown.text = new_status
        self.menu.dismiss()
        App.get_running_app().root.get_screen("AdminOrdersScreen").update_order_status(self.order_data[0], new_status)
```
- Updates the UI to reflect the new status.
- Calls `update_order_status()` in `AdminOrdersScreen` to modify the database.
#### Explanation of AdminOrdersScreen
```.py
class AdminOrdersScreen(Screen):
    def on_pre_enter(self, *args):
        self.load_orders()
```
- Ensures that orders are refreshed whenever this screen is entered.
Loading Orders from Database
```.py
    def load_orders(self):
        container = self.ids.orders_list
        container.clear_widgets()
        db = DatabaseManager(name="orders.sql")
        query = """
            SELECT order_id, user_id, user_email, item_name, item_price, ticket_number, status
            FROM orders
            ORDER BY order_id DESC
        """
        orders = db.search(query)
        db.close()
        for order in orders:
            order_card = OrderItemRow(order_data=order)
            container.add_widget(order_card)
```
- This method fetches all orders from the database, sorts them by order_id (newest first), and populates the admin UI.
- Why sort by `order_id` DESC? Ensures that the most recent orders appear at the top.
Updating Order Status in Database
```.py
    def update_order_status(self, order_id, new_status):
        db = DatabaseManager(name="orders.sql")
        query = f"UPDATE orders SET status = '{new_status}' WHERE order_id = {order_id}"
        db.run_save(query)
        db.close()
        self.load_orders()
```
- Modifies the order’s status in the database.
- Why reload orders? To reflect the latest changes instantly on the UI.

### Explanation of KV File (UI Representation)
```.kv
<AdminOrdersScreen>:
    name: "AdminOrdersScreen"
    MDBoxLayout:
        orientation: "vertical"
        md_bg_color: 0.06, 0.06, 0.06, 1
```
- Defines the overall layout of the admin screen.
Orders List Container
```.kv
        ScrollView:
            MDBoxLayout:
                id: orders_list
                orientation: "vertical"
                size_hint_y: None
                height: self.minimum_height
                spacing: dp(8)
                padding: dp(8)
```
- Displays orders dynamically inside a scrollable container
Order Item Layou
```.kv
<OrderItemRow@MDCard>:
    orientation: "vertical"
    size_hint_y: None
    height: dp(120)
    md_bg_color: 1.0, 0.549, 0.0, 1
    padding: dp(10)
    spacing: dp(5)
```
- Each order appears as a colored card.
- Why `md_bg_color: 1.0, 0.549, 0.0, 1`? Uses an orange shade to indicate urgency.
Status Dropdown UI
```.kv
        MDDropDownItem:
            id: status_dropdown
            text: root.order_data[6]
            on_release: root.open_status_menu()
            size_hint_x: 0.5
```
- Enables quick status updates for each order
