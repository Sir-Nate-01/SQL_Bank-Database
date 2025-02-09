# SQL_Bank Database

## Overview
This repository contains the design and implementation of a robust database system for a financial institution. The system is designed to address the bank's challenges in data management, security, and decision-making processes. Built using MySQL, this database ensures strong consistency, high availability, and scalability to support the bank's operations and future growth.

## Key Features
Centralized Data Management: Transition from decentralized spreadsheet-based data management to a centralized, secure database system.
Entity-Relationship Model: A well-defined ER diagram with six core entities: Clients, Accounts, Transactions, Loans, Employees, and Branches.
Relational Database Design: Implementation of schemas with primary and foreign keys to ensure data integrity and relationships.
SQL Queries and Stored Procedures: Includes SQL queries for data retrieval, updates, and stored procedures for account creation and funds transfer.
ACID Compliance: Ensures reliable and consistent financial transactions through Atomicity, Consistency, Isolation, and Durability.
CAP Theorem Alignment: Prioritizes Consistency and Availability (CA) to meet the bank's operational needs.

## Repository Structure
mysql-bank-database/
├── README.md                   # Project overview and documentation
├── er_diagram/                 # Contains the Entity-Relationship Diagram (ERD)
├── sql_scripts/                # SQL scripts for table creation, queries, and stored procedures
│   ├── create_tables.sql       # Script to create all database tables
│   ├── insert_data.sql         # Script to populate tables with sample data
│   ├── select_queries.sql      # Example SELECT queries for data retrieval
│   ├── update_queries.sql      # Example UPDATE queries for data modification
│   ├── new_account_creation.sql # Stored procedure for account creation
│   └── funds_transfer.sql      # Stored procedure for funds transfer
├── evaluation/                 # Documentation on ACID properties and CAP theorem

### Entity-Relationship Diagram (ERD)
The ERD outlines the relationships between the six core entities:
Client: Stores customer details (ID, Name, Date of Birth, Address, Email).
Accounts: Tracks account information (ID, Type, Balance, IBAN, Open Date, Client_ID).
Transactions: Records financial transactions (ID, Type, Amount, Transaction_Date, Source_Acc_ID, Destination_Acc_ID).
Loans: Manages loan details (ID, Type, Amount, Interest Rate, Client_ID).
Employees: Tracks employee information (ID, Name, Position, Email, Telephone, Branch_ID).
Branch: Stores branch details (ID, Name, Contact, Address, Branch Manager).

ER Diagram for the database (https://drive.google.com/file/d/1qhXTbXIvCf6oz9L3uWjw1mGfaoyB9P58/view?usp=sharing)
Reverse Engineering for the database (https://drive.google.com/file/d/1fs6cAi2crfiip1z5SziFB-1EYa6N_mEk/view?usp=sharing).

### SQL Implementation

#### Table Creation
The database schema includes the following tables:Client ,Accounts, Transactions, Loans, Employees and Branch.Each table is created with appropriate data types, primary keys, and foreign keys to enforce relationships.

#### Actions Performed:
Client Table: Created to store customer details (https://drive.google.com/file/d/13lcEAJSCvJFq3jFIM_J_jWj-wrGegr7l/view?usp=sharing).
Accounts Table: Tracks accounts associated with clients(https://drive.google.com/file/d/1WG6bEOBoQ0nz50f07IGE2O9h9oJu2TkR/view?usp=sharing).
Transactions Table: Records all financial transactions(https://drive.google.com/file/d/1BQ5x-dgCHpJRUCLqyZm5KQf3L8x4fGGl/view?usp=sharing).
Loans Table: Manages loan information for clients(https://drive.google.com/file/d/1Kq1gEIgKZCkYgE7g5lzL-WgfnPKWl-LN/view?usp=sharing).
Employees Table: Stores employee details and their associated branches(https://drive.google.com/file/d/1bRkuSYKfnAy1Ajkfuq8UvxoN0hW7XRYM/view?usp=sharing).
Branch Table: Contains information about each branch, such as branch manager and contact details(https://drive.google.com/file/d/1d39HtNyHOliFQXzbK-eawOC6cWsK-qmZ/view?usp=sharing).

### SQL Queries
Select Query: Retrieve all customer service officers( SELECT * FROM Employees WHERE Position = 'Customer Service Officer'; ).
Join Query: Retrieve clients with a balance of at least €5,000 (SELECT c.ID, c.Name, a.Balance
FROM Client c
JOIN Accounts a ON c.ID = a.Client_ID
WHERE a.Balance >= 5000;
 ).
Update Query: Update the branch manager for Berlin Zone B( UPDATE Branch
SET Branch_Manager = 'Xabi Alonso'
WHERE Name = 'Berlin Zone B'; ).

### Stored Procedures
New Account Creation: Ensures clients cannot exceed the limit of three active accounts.It checks account limit before allowing new account creation(https://drive.google.com/file/d/1YlW4Tq8BFyhciCBxC7JBTe5WGbKYS3gz/view?usp=sharing).
Funds Transfer: Ensures secure and consistent funds transfer between accounts.It executes a secure transaction between two accounts, ensuring sufficient balance before processing (https://drive.google.com/file/d/1yBE7pxFspo5DT40bqysci_GLwTTgohAE/view?usp=sharing).

Evaluation
ACID Properties
The database system adheres to ACID properties:

Atomicity: Ensures transactions are completed in full or not at all.
Consistency: Maintains accurate account balances and enforces system constraints.
Isolation: Allows concurrent transactions without interference.
Durability: Ensures transaction records persist even after system failures.
CAP Theorem
The system prioritizes Consistency and Availability (CA), aligning with Natcom Bank's operational needs. This choice ensures reliable financial transactions and high service availability, even as the bank scales.

Contact
For any questions or inquiries regarding this project, please contact: www.linkedin.com/in/nathan-nortey-63bb03113

