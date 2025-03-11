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
