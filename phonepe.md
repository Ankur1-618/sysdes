## Scaling Requirements — Capacity Estimation
Let’s assume —

Total number of users: 200 million

Daily active users (DAU): 50 million

Number of transactions per user per day: 5

Total number of transactions per day: 250 million

Considering a read-heavy system with a read-to-write ratio of 100:1:

Total number of transactions read per day: 100 * 250 million = 25 billion

## Storage Estimation:

Assuming an average transaction size of 1 KB: Total storage per day: 250 million * 1 KB = 250 GB/day

For the next 3 years: 250 GB * 365 days * 3 years = 273.75 TB

Requests per second: 250 million / 24 hours / 3600 seconds = 2,880 requests/second

Horizontal Scalability: The system should be able to handle a high volume of concurrent transactions by scaling horizontally across multiple servers.

Performance Optimization: The system should be optimized for low latency and high throughput to ensure quick and seamless transactions.

Fault Tolerance: PhonePe’s system should be designed to handle failures gracefully, ensuring uninterrupted service availability.

Data Replication: To distribute the load and ensure data availability, the system should employ data replication techniques across multiple data centers.

## Data Model — ER requirements
Users:

### Fields:
User_id: Int (Primary Key)
Username: String
Email: String
Password: String
Transactions:

### Fields:
Transaction_id: Int (Primary Key)
User_id: Int (Foreign Key referencing Users)
Amount: Float
Timestamp: DateTime
Status: String
User: Represents a registered user of the PhonePe platform.

Bank Account: Stores the details of the user’s linked bank accounts.

Transaction: Represents a financial transaction between users or merchants.

Merchant: Represents a registered merchant on the PhonePe platform.

Digital Wallet: Stores the balance and transaction history of a user’s digital wallet.

Notification: Stores the notifications related to transactions, offers, and other relevant information for users.

## High Level Design
Assumptions:

The system is read-heavy, with more users checking their transaction history and account balances than performing transactions.
High availability and reliability are crucial.
Latency should be kept low, aiming for a response time of approximately 350ms.
Main Components:
Mobile Client: Users access the PhonePe system via the mobile application.
Application Servers: Handle read, write, and notification operations.
Load Balancer: Routes and directs requests to the appropriate servers.
Cache (Memcache): Caches frequently accessed data using a Least Recently Used (LRU) algorithm to improve response times.
CDN (Content Delivery Network): Improves latency and throughput by caching and delivering static content closer to the users.
Database: Stores user data, transaction records, and other relevant information.
Storage (e.g., HDFS, Amazon S3): Stores media files, such as user profile pictures and transaction-related documents.

## Services

### User Service:

Handles user registration, authentication, and profile management.
Provides functionality to update user information and reset passwords.

### Transaction Service:

Handles the creation, retrieval, and processing of user transactions.
Ensures transaction integrity, security, and consistency.

### Balance Service:

Manages user account balances and provides functions for checking balances, adding funds, and withdrawing funds.

### Notification Service:

Sends transaction-related notifications and updates to users.
Handles push notifications and email notifications.

### Security Service:

Implements security measures such as encryption, token-based authentication, and fraud detection.

### Analytics Service:

Collects and analyzes user behavior data to derive insights and improve the user experience.
Provides reports and visualizations on transaction patterns, popular services, and user preferences.

Mobile App: The user interacts with the PhonePe system through a mobile application, which serves as the primary interface.

Frontend Servers: Handle user requests, authentication, and serve the user interface.

API Gateway: Acts as a central entry point for all requests, routing them to the appropriate backend services.

Microservices: Backend services are designed as independent microservices to enhance scalability and maintainability.

Load Balancers: Distribute incoming traffic across multiple instances of backend services to handle high user loads.

Caching: Implements caching mechanisms to improve performance and reduce database load for frequently accessed data.

Asynchronous Processing: Utilizes message queues and event-driven architecture to handle time-consuming tasks asynchronously.

Transaction Service: Manages the processing and validation of user transactions.

User Service: Handles user authentication, registration, and profile management.

Notification Service: Responsible for sending transaction notifications and other relevant updates to users.

Banking Interface: Connects with various banking partners to facilitate fund transfers and account management.

Database: Stores user data, transaction history, and other relevant information.
