# Introduction to .Net Aspire
 Introduction to .Net Aspire, by BPB Publications

Reference Architecture
This book offers a hands-on, practical application built using a microservices architecture pattern. The application centers around an E-Shop application, enabling users to submit orders and receive shipments.
The figure in the following shows the architecture of the solution that we will build throughout the book's chapters (refer to Figure 1.12).
The main components of the solution are as follows:
•	Web application UI (frontend) developed using React. The user interface allows customers to browse different products, create orders, and view order statuses. The front end communicates with backend services to fetch and update product information in real-time.
•	Warehouse API (backend), developed using .NET, handles inventory management. When a request is made to the warehouse API, it will read the warehouse status from the warehouse and the current pending orders from the order database. It will make sure to remove items coming from the pending orders from the available stock in the warehouse.
•	Create order API (backend), developed using Golang. When a request is made to the create order API, it will create a new order in the order database and set it to pending. Additionally, it publishes messages to a Pub or Sub messaging system, initiating the order processing pipeline.
•	Payment API (backend) developed using Python. It listens for events from the Pub or Sub system, and when a request is made to the payment API, it will set the order status to processing.
•	Shipping API (backend) developed using Node.js. Once an order is marked as paid, this service is responsible for preparing the shipment, and it will update the status to be completed in the orders database.

