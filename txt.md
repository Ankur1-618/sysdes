
# System Design Presentation for Utility Bills Notification and Payment System

## Slide 1: Title slide

## Slide 2: Problem statement

We need to build a product that can automatically retrieve customer utility bills based on customer data (ex-name, mobile number, etc) and Utility bill provider details (eg Insurance number, gail/electricity bill consumer number etc) with periodic schedule and notify customer with bill details for payment. Customer can also pay the bills using the product.

## Slide 3: Use cases

Customer Mobile bill is generated on 10th of every month. Our product will retrieve mobile bill details from the mobile operator using mobile service provider API on 10th of every month and then send reminder to the customer for the payment.
Customer Electricity bill is generated on 15th of every month. Our product will retrieve electricity bill details from the service provider using service provider API on 15th of every month and then send reminder to the customer for the payment.
Customer recharges prepaid mobile for 3-month plan. After 3 months remind customer for recharge with recharge plan details.

## Slide 4: Expected solution

Product should be able to onboard new customer and store customer data needed to retrieve utility bills.
Product should be able to register new utility providers and store details like API details of service provider etc
Product should be able to retrieve customer bills details based on the bill generation schedule and send reminders/notifications to customer

## Slide 5: Design considerations

## Assumptions made while designing
The system will have access to the customer's utility bill account information.
The system will have access to the utility bill provider's API.
The system will have access to a third-party payment API.
Physical/Logical design as applicable (High level design)
The system will be designed as a microservices architecture.
Modules, components, services
Customer Service
Utility Provider Service
Bill Retrieval Service
Notification Service
Payment Service
Proposed technology stack and frameworks
Programming language: Python
Web framework: Django
Database: PostgreSQL
Message broker: RabbitMQ
API Gateway: Kong
Non-functional aspect (scalability, reliability, security)
Scalability: The system should be able to handle a large number of customers and transactions. This will be achieved by using a microservices architecture and by horizontally scaling the microservices.
Reliability: The system should be highly reliable. This will be achieved by replicating the database and by using a message broker to ensure that messages are delivered reliably.
Security: The system should be secure. This will be achieved by using encryption to protect sensitive data and by implementing authentication and authorization mechanisms.

## Slide 6: Key advantages of the solution

Scalability
Reliability
Security

## Slide 7: Risks

Integration challenges with utility bill providers
Third-party payment API outages
Security breaches

## Slide 8: Alternate approaches

Monolithic architecture: This would be simpler to design and implement, but it would be less scalable and reliable.
Serverless architecture: This would be even more scalable than a microservices architecture, but it would be more complex to design and implement.

## Slide 9: Deployment Architecture and security

The system will be deployed on a cloud platform such as AWS or Azure. The microservices will be deployed in containers and managed by a container orchestration platform such as Kubernetes. The database will be deployed on a highly available managed database service such as Amazon RDS or Azure SQL Database.

The system will be secured using the following measures:

All communication between the microservices will be encrypted using TLS.
All sensitive data will be encrypted at rest and in transit.
Authentication and authorization mechanisms will be implemented to control access to the system.
The system will be monitored for security threats and vulnerabilities.

## Slide 10: Conclusion

This presentation has outlined a system design for a utility bills notification and payment system. The system is designed to be scalable, reliable, and secure. It will be implemented using a microservices architecture and deployed on a cloud platform.
