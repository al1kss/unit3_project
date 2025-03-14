![dd](https://github.com/user-attachments/assets/21aa52c9-d205-4657-a756-9f1e1c3acc35)
# Unit 3: Restaraunt Manager

## Criteria A: Planning

## Problem definition
The owner of "NomNom" has observed a noticeable dip in customer satisfaction and order accuracy, primarily due to an outdated system that relies on phone orders and manual entry. Without a centralized digital record, errors occur frequently—from incorrect orders to miscommunications between the front of house and kitchen. This disjointed process not only leads to delays and disputes over order details but also prevents efficient tracking of customer interactions and order histories. The need for a robust system that automates order processing and streamlines communication between customers and staff has become critical to restore operational efficiency and enhance customer trust.

## Proposed Solution
I propose creating a cross-platform computer application to streamline ordering and enhance operational efficiency at a modern pizza restaurant. To address the client’s need for portability, low cost, and future-proofing, I will use Python rather than compiled languages such as C, because while C is very fast and close to the hardware, it is less convenient for rapidly building user interfaces and requires manual memory management[^1]. Python, by contrast, is open-source, meaning there are no additional licensing fees[^2], and it runs on any operating system as long as Python is installed, making it well-suited if the store upgrades or relocates. Likewise, although Java is a popular choice for cross-platform development, it typically involves a separate runtime environment and is more closely associated with mobile or enterprise environments. Building the interface in Python will be done with the Kivy framework and its KivyMD extension[^3]: Kivy’s multi-platform support ensures that the interface will appear consistent and function smoothly on different screen sizes, while KivyMD’s Material Design components offer a clean, modern look that aligns with the restaurant’s brand image. Finally, I will store the restaurant’s data in SQLite rather than using flat-file formats such as CSV or JSON[^5], since the application must handle interconnected data (customer profiles, menu items, order histories) and benefit from SQL querying[^6]. Although server-based databases like MySQL or PostgreSQL were considered, SQLite is a better fit for a single-computer environment because it is serverless and lightweight, reducing overhead and maintenance costs while preserving relational capabilities.


[^1]: Merrill, Cache. "7 Important Reasons Why You Should Use Python." Zibtek, 1 September 2019, https://www.zibtek.com/blog/7-important-reasons-why-you-should-use-python
[^2]:Yakymiv, Volodymyr. "Choosing the Best Language for App Development: 7 Options to Consider." Forbytes, 3 November 2023, https://forbytes.com/blog/best-language-for-app-development
[^3]:"Kivy Tutorial." Free Learning Platform For Better Future, https://www.javatpoint.com/kivy#AdvantagesDisadvantages/
[^4]:"Building a Simple Application using KivyMD in Python." GeeksforGeeks, https://www.geeksforgeeks.org/building-a-simple-application-using-kivymd-in-python/
[^5]:"Should you use CSV, JSON, or SQL?." PythonHow, https://pythonhow.com/python-tutorial/miscellaneous/csv-json-or-sql/
[^6]:"AQLite Is Serverless." SQLite, https://www.sqlite.org/serverless.html
[^7]:"SqLite Advantages." Free Learning Platform For Better Future, https://www.javatpoint.com/sqlite-advantages-and-disadvantages
[^8]:Yugulalp, Serdar. "Why you should use SQLite." Infoworld, 13 February 2019, https://www.infoworld.com/article/3331923/why-you-should-use-sqlite.html 
[^9]: https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
[^10]: https://kivy.org/doc/stable/api-kivy.properties.html
[^11]: https://kivymd.readthedocs.io/en/latest/components/dialog/
[^12]: https://docs.python.org/3/library/threading.html

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
## Test Plan
| Test Case                                         | Procedure                                                                                                                                                                                                        | Planned Outcome                                                                                                                                                 | Success Criteria                                                                                                            |
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| 1 - Attempt Unauthorized Access to Orders Menu    | 1. Run the program.   2. Click on the Location icon without logging in.                                                                                                                                          | - The user remains on the same screen.   - A message appears: "Please log in as an admin to access orders."                                                     | The program prevents unauthorized users from accessing the Orders Menu                                                      |
| 2 - Login with Incorrect Credentials              | 1. Run the program.   2. Enter "admin" as the username and "wrong_password" as the password.   3. Click Login.                                                                                                   | - The login fails.   - A message appears: "Invalid username or password."                                                                                       | The system correctly denies access when incorrect credentials are provided                                                  |
| 3 - Login with Correct Admin Credentials          | 1. Run the program.   2. Enter "admin" as the username and "secure_password" as the password.   3. Click Login.                                                                                                  | - The login is successful.   - The Admin dashboard appears.                                                                                                     | The program allows the admin to log in with the correct credentials                                                         |
| 4 - Admin Access to Orders Menu via Location Icon | 1. Log in as "admin" with "secure_password".   2. Click on the Location icon.                                                                                                                                    | - The Orders Menu screen is displayed.   - The admin can view and manage orders.                                                                                | The system correctly allows access to the Orders Menu only for logged-in admins                                             |
| 5 - Logout and Attempt Re-entry to Orders Menu    | 1. Log in as "admin" with "secure_password".   2. Click the Logout button.   3. Click on the Location icon.                                                                                                      | - The user is prevented from accessing the Orders Menu.   - A message appears: "Please log in as an admin to access orders."                                    | The system correctly restricts access after logout                                                                          |
| 6 - User Account Should Not Access Orders Menu    | 1. Register a new non-admin user.   2. Log in using the new user credentials.   3. Click the Location icon.                                                                                                      | - The user remains on the same screen.   - A message appears: "Access denied: Admins only."                                                                     | The system prevents normal users from accessing the Orders Menu                                                             |
| 7 - Admin Access Persistence After App Restart    | 1. Log in as "admin" with "secure_password".   2. Close and restart the program.   3. Click on the Location icon.                                                                                                | - If session persistence is implemented, the Orders Menu appears.   - If not, the user is prompted to log in again.                                             | The system should either maintain the session or require re-login after restart                                             |
| 8 - Attempt Unauthorized Checkout                 | 1. Run the program and log in as a non-admin user (or a new user).   2. Add items to the cart.   3. Proceed to checkout.                                                                                         | - If the user is not logged in, they are redirected to the login screen.   - If the user is logged in (non-admin), they proceed as usual.                       | The system correctly enforces login before checkout                                                                         |
| 9 - Attempt Admin Checkout                        | 1. Run the program and log in as "admin" with "secure_password".   2. Add items to the cart.   3. Proceed to checkout.                                                                                           | - The checkout process works as expected.   - The order is placed successfully.                                                                                 | The system allows both admins and users to complete checkout                                                                |
| 10 - Checkout Access After Logout                 | 1. Log in as a normal user.   2. Add items to the cart.   3. Click Logout.   4. Try to proceed to checkout.                                                                                                      | - The user is redirected to the login screen.   - A message appears: "Please log in to proceed with checkout."                                                  | The system prevents logged-out users from checking out                                                                      |
| 11 - Redirection to Cart & Receiving Order Number | 1. Run the program.   2. Add items to the cart while not logged in (or logged out).   3. Attempt to checkout.   4. The system prompts for login.   5. Log in with valid user credentials (admin or normal user). | - After logging in, the user is automatically redirected back to their cart.   - The user sees a unique order number (#XX) displayed upon confirming the order. | The user can log in mid-checkout and still complete the order A unique order number is provided to retrieve the order later |

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

### Credits:
1. https://stackoverflow.com/questions/63783442/how-to-make-a-kivymd-page-navigation-and-insert-some-categories-at-the-main-menu
2. https://kivymd.readthedocs.io/en/1.1.1/components/button/#mdiconbutton (code for all icon navigation)
3. https://www.istockphoto.com/en/search/2/image?mediatype=illustration&phrase=logo+funny+pizza
4. https://stackoverflow.com/questions/60387236/valueerror-kivymd-app-object-must-be-inherited-from-kivymd-app-mdapp
5. https://kivymd.readthedocs.io/en/latest/themes/theming/
