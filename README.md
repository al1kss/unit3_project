![dd](https://github.com/user-attachments/assets/21aa52c9-d205-4657-a756-9f1e1c3acc35)
**Fig 1** *Delivery man waiting to board a train*
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
1. The application provides a secure login and registration system that distinguishes between customer and staff accounts, ensuring only verified users can access features relevant to their role.
2. The application allows customers to browse a visually detailed menu, select from various customization options, and place orders confidently, reducing the risk of mistakes.
3. The application notifies kitchen and delivery staff in real time whenever a new order is placed, allowing immediate preparation and efficient dispatch.
4. The application enables the admin account to add food listings directly through the interface, ensuring the menu stays current without requiring separate tools.
5. The application stores all user credentials, orders, and menu data in an SQLite database, guaranteeing secure, efficient retrieval of information and preventing unauthorized access.



# Criterion B: Design
## System Diagram
![Project 1](https://github.com/user-attachments/assets/856454e9-b49a-491b-a471-1ba7603a3978) 
**Fig 2** *System diagram of proposed solution*

## UML Diagram
<img width="1378" alt="Screenshot 2025-03-14 at 16 07 36" src="https://github.com/user-attachments/assets/1803e822-90b4-4033-a6e0-22792b10afa4" />
**Fig 3** *UML Diagram of the classes*

## ER Diagram
<img width="738" alt="Screenshot 2025-03-14 at 16 27 11" src="https://github.com/user-attachments/assets/add44af0-ec35-4c8e-8b27-17541e7f9747" />
**Fig 4** *ER Diagram of the databases*

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
## Existing Tools
| Software/Development Tool    |
|------------------------------|
| Python                       |
| PyCharm                      |
| KivyMD                       |
| SQLite (relational database) |

| Libraries |
|-----------|
| Kivy      |
| KivyMD    |
| sqlite3   |
| requests  |
| json      |

## List of Techniques Used
1. Classes and Object-Oriented Programming
- To keep the code well-structured and readable (e.g., separate Screen classes for each UI screen)
2. Functions
- To encapsulate repeated logic (e.g., password hashing, database queries) and avoid code duplication
3. Conditional Statements (if-else)
- To handle user permissions (e.g., only admins can modify food listings)
4. Loops (for/while)
- For iterating through database records (e.g., displaying menu items or orders)
5. Relational Databases (SQLite)
- To store and retrieve data across multiple tables (user credentials, menu items, orders) with referential integrity
6. GUI Development (Kivy/KivyMD)
- To create a visually consistent interface with Material Design components for a modern look
7. Real-Time Updates
- To notify staff of new orders (e.g., staff sees an updated order screen instantly)

## Development
### Code Organization and Database Setup
All screens inherit from `MDScreen` in KivyMD, and each screen is a class in the main Python file (e.g., `MainScreen`, `LoginScreen`, `AdminOrdersScreen`). The root `MDApp` subclass manages the application’s flow and connects to the `pizza.kv` file, which defines the UI layout. Below is an example of how I declared the screens in `pizza.kv`:
```.kv
ScreenManager:
    LoginScreen:
        name: "LoginScreen"
    MainScreen:
        name: "MainScreen"
    AdminOrdersScreen:
        name: "AdminOrdersScreen"
    # ...

```

### Multiple SQLite Tables vs. Single Database File
To keep the application secure, I use different databases so if one database gets hacked, the other will still be secure. Furthermore, to maintain clarity and logical separation, my application uses multiple tables (and, in practice, multiple `.sql` files) rather than a single giant table. This design keeps user credentials, menu items, and orders in distinct schemas, avoiding data collisions and allowing easier modifications. For example:
- `login.sql`: Manages user credentials, roles, and secure password storage
- `menu.sql`: Stores menu items (pizza name, description, price, image)
- `orders.sql`: Records placed orders, linking them to user accounts and statuses
A single relational database engine (SQLite) handles these tables seamlessly, ensuring referential integrity (e.g., an order references a valid user ID).

### Success Criterion 1: Secure Login & Registration
>“The application provides a secure login and registration system that distinguishes between customer and staff accounts.”
Implementation
```.py
class LoginScreen(Screen):
    def try_login(self):
        username = self.ids.uname.text
        password = self.ids.passwd.text
        # Query user table from login.sql
        result = db.search(f"SELECT * FROM user WHERE username='{username}'")
        if result and check_password(user_password=password, hashed_password=result[0][3]):
            print("Login successful!")
            # Distinguish admin vs. user
            user_type = result[0][4]  # e.g., 'admin' or 'user'
            if user_type == "admin":
                self.manager.current = "AdminOrdersScreen"
            else:
                self.manager.current = "MainScreen"
        else:
            # Show invalid credentials dialog
```
Why multiple roles?
- Admins can modify the menu and update orders
- Regular users can only place orders
Why a separate `login.sql`?
- Prevents accidental mixing of user data with menu or order records
- Easier to enforce constraints (unique username/email, role-based checks)
#### Password Hashing
A `secure_password` library ensures that plain-text passwords are never stored. During registration:
```.py
hash_pass = encrypt_password(passwd)
db.run_save(f"INSERT INTO user(username, email, password, type) VALUES ('{uname}', '{email}', '{hash_pass}', 'user')")
```
#### Secure Password library
```.py
from passlib.context import CryptContext

#Create an object of the class cryptocontext
pwd_config = CryptContext(schemes=["pbkdf2_sha256"],
                          default="pbkdf2_sha256",
                          pbkdf2_sha256__default_rounds=30000
                          )

#this function receives the unsafe password
# and returns the hashed password

def encrypt_password(user_password):
    return pwd_config.hash(user_password)

def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)
```
This step reduces the risk of data breaches




### Success Criterion 2: Intuitive Menu & Order Placement
>“The application allows customers to browse a visually detailed menu, select customization options, and place orders.”
Implementation
```.py
class MainScreen(Screen):
    def on_pre_enter(self, *args):
        self.load_menu()

    def load_menu(self):
        # Fetch menu items from menu.sql
        items = db.search("SELECT name, description, price, image FROM menu")
        self.ids.menu_list.clear_widgets()
        for name, desc, price, img in items:
            card = HeritageFoodCard()
            card.ids.pizza_name.text = name
            card.ids.pizza_desc.text = desc
            card.ids.pizza_price.text = f"from {price} сом"
            card.ids.pizza_image.source = img
            # Binding card press to add-to-cart logic
            card.bind(on_release=self.add_to_cart)
            self.ids.menu_list.add_widget(card)
        if LoginScreenReal.current_user_type == "admin":
            self.ids.menu_list.add_widget(AddPizzaCard())

class HeritageFoodCard(Factory.MDCard):
    """Pizza item card with 'Add to cart' button."""
    pass

class AddPizzaCard(Factory.MDCard):
    """Pizza item card with 'Add to cart' button."""
    pass
```
```.kv
<HeritageFoodCard@MDCard>:
    size_hint_y: None
    height: dp(120)
    md_bg_color: 0.15, 0.15, 0.15, 1
    radius: [15, 15, 15, 15]
    elevation: 2
    padding: dp(10)
    spacing: dp(10)
    orientation: "horizontal"

    # Circularpizza image on the left
    # Using FitImage so it resizes nicely.
    FitImage:
        id: pizza_image
        size_hint: None, None
        size: dp(100), dp(100)
        radius: [40, 40, 40, 40]  # round corners to mimic a circle
        keep_ratio: True
        allow_stretch: True

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(2)

        MDLabel:
            id: pizza_name
            text: "Pizza Name"
            font_style: "Subtitle1"
            theme_text_color: "Custom"
            text_color: 1, 1, 1, 1

        MDLabel:
            id: pizza_desc
            text: "Description"
            font_style: "Caption"
            theme_text_color: "Custom"
            text_color: 0.8, 0.8, 0.8, 1

        MDLabel:
            id: pizza_price
            text: "from 295 JPY"
            font_style: "Body2"
            theme_text_color: "Custom"
            text_color: 1, 0.6, 0, 1

<AddPizzaCard@MDCard>:
    size_hint_y: None
    height: dp(120)
    md_bg_color: 0.2, 0.2, 0.2, 1
    radius: [15, 15, 15, 15]
    elevation: 2
    padding: dp(10)
    spacing: dp(10)
    orientation: "vertical"
    on_release: app.root.get_screen("MainScreen").show_add_pizza_dialog()

    MDBoxLayout:
        size_hint_y: None
        height: dp(100)
        spacing: dp(10)
        MDIconButton:
            icon: "plus"
            theme_text_color: "Custom"
            text_color: 1, 1, 1, 1
            size_hint: None, None
            size: dp(100), dp(100)
```
Here I used Heritage that acts as `MDCard`, so that I don't have to create a lot of code just to add one more pizza. Furthermore this is more optimized so the program can run on any system.

Why did I separate `menu.sql`?
- Menu data is distinct from user credentials and order transactions
- Updates to the menu do not risk overwriting user or order info

GUI
Using KivyMD’s `MDCard` + `FitImage` for each pizza item provides a modern, visually appealing layout.

### Success Criterion 3: Immediate Staff Notice
>“The application notifies kitchen and delivery staff in real time when an order is placed.”
Implementation
```.py
class AdminOrdersScreen(Screen):
    def on_pre_enter(self, *args):
        self.load_orders()

    def load_orders(self):
        self.ids.orders_list.clear_widgets()
        # Query orders from orders.sql
        query = "SELECT order_id, user_email, item_name, item_price, ticket_number, status FROM orders ORDER BY order_id DESC"
        rows = db.search(query)
        for order in rows:
            order_card = OrderItemRow(order_data=order)
            self.ids.orders_list.add_widget(order_card)
```
Whenever a new order is placed in the `MainScreen`, the staff’s `AdminOrdersScreen` is updated to show the new order:
```.py
def place_order(self):
    # Insert into orders.sql
    db.run_save(f"INSERT INTO orders(user_id, user_email, item_name, item_price, ticket_number) VALUES(...)")
    # Real-time update
    # If staff is already on AdminOrdersScreen, they see the new order upon screen refresh or on_pre_enter
```
Why did I use multiple tables?
- Each order references user info (by ID or email).
- Using `orders.sql` avoids mixing with menu or user credentials, preventing confusion.

### Success Criterion 4: Modification of Food Listings
>“The application enables the admin account to add or edit food listings through the pizza app.”
Implementation
```.py
class MainScreen(Screen):
    def load_menu(self):
        items = db.search("SELECT ... FROM menu")
        for name, desc, price, img in items:
            # ...
        if current_user_type == "admin":
            # Show AddPizzaCard for admin only
            self.ids.menu_list.add_widget(AddPizzaCard())

class AddPizzaCard(MDCard):
    def on_release(self):
        # Pop-up for admin to enter name, desc, price
        # Insert into menu.sql
        db.run_save(f"INSERT INTO menu(name, description, price, image) VALUES(...)")
```
Motivation
- Admins frequently update the menu (new items, promotions, etc.)
- This design ensures that only authorized staff can modify the `menu` table

### Success Criterion 5: Secure & Efficient Data Storage
>“All user credentials, order details, and menu information are stored in an SQLite database, ensuring data integrity and minimal unauthorized access.”
Implementation
#### Multiple Database Tables
1. User Table (login.sql)
```.sql
CREATE TABLE IF NOT EXISTS user(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT UNIQUE,
    email TEXT UNIQUE,
    password VARCHAR(256),
    type TEXT DEFAULT 'user'
);
```
2. Menu Table (menu.sql)
```.sql
CREATE TABLE IF NOT EXISTS menu(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT UNIQUE NOT NULL,
    description TEXT NOT NULL,
    price REAL NOT NULL,
    image TEXT DEFAULT 'pizza.png'
);
```
3. Orders Table (orders.sql)
```.sql
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
Why not a single table?
- A single table would become unwieldy, forcing repeated columns for user data, menu items, and order details
- Proper normalization across multiple tables reduces redundancy and avoids anomalies when inserting or updating records
- If one of the tables gets hacked the other tables will still be stored securely
#### Password Hashing
```.py
hashed_pass = encrypt_password(password)
db.run_save(f"INSERT INTO user(username, email, password) VALUES ('{uname}', '{email}', '{hashed_pass}')")
```
Ensures stolen database files do not reveal raw passwords
#### Transaction Accuracy
When an order is placed, the official price is fetched from `menu.sql` to ensure consistent billing:
```.py
price_db = db.search(f"SELECT price FROM menu WHERE name='{item_name}'")
```
This approach avoids relying on user-inputted prices



### Credits:
1. https://stackoverflow.com/questions/63783442/how-to-make-a-kivymd-page-navigation-and-insert-some-categories-at-the-main-menu (used for debugging)
2. https://kivymd.readthedocs.io/en/1.1.1/components/button/#mdiconbutton (code for all icon navigation)
3. https://www.istockphoto.com/en/search/2/image?mediatype=illustration&phrase=logo+funny+pizza (used to look for pizza pictures)
4. https://stackoverflow.com/questions/60387236/valueerror-kivymd-app-object-must-be-inherited-from-kivymd-app-mdapp (documentation)
5. https://kivymd.readthedocs.io/en/latest/themes/theming/ (documentation)
6. https://chatgpt.com (used to generate pizza details in sql databases)
