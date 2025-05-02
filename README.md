# Banking System

### Short Description

The goal of the project is to create an API for a banking system that allows users to transfer funds to their own or other accounts and use ATMs.

System managers will be able to view various types of reports.

The project includes several modules. Each module can be considered as an independent system, but some modules depend on the existence of other modules. Therefore, their implementation should be done sequentially.

### Modules

- Internet Banking
    - Operator
    - User
- ATM Client
    - Card Authorization
    - ATM Operations
- Reports
    - User Statistics
    - Transaction Statistics

### Internet Banking

Internet Banking should be a web application that allows bank operators to register users, create bank accounts for them, and add cards to the accounts.

**Operator**

The operator should be able to register individuals by entering the following information:

- First Name *
- Last Name *
- Personal Number *
- Date of Birth *
- Email *
- Password *

When creating a bank account for a user, the operator should be able to specify the following information:

- IBAN (IBAN validation should be performed during registration. The operator should not be able to create an account with an invalid IBAN)
- Amount (the amount of money in the account)
- Currency (should be a selectable field. Possible values: GEL, USD, EUR)

When registering a card, the operator should specify the following information:

- Card Number
- First and Last Name
- Card Expiry Date (Year, Month)
- 3-digit CVV code (for online payments)
- 4-digit PIN code (for ATM withdrawals)

**User**

Registered users should be able to view the accounts and cards created for them by the operator.

From Internet Banking, the user should be able to perform two types of transactions:

- Transfer funds between their own accounts, with a transfer fee of 0%
- Transfer to another bank account, with a transfer fee of 1% + 0.5 (GEL/USD/EUR)

When transferring funds, the exchange rates of the account currencies should be taken into account. If the currency of one account differs from the currency of the other account, the amount should be converted based on a predefined exchange rate.

### ATM Client

For the ATM client, an API should be created where the user can perform various operations after card authorization.

**Card Authorization**

To perform any operation on the ATM, card authorization is required.

For this, the user must enter the card number and PIN code.

Authorization should not be successful if the card is expired.

**ATM Operations**

After authorization, the following operations should be possible:

- View Balance
- Withdraw money in GEL, USD, or EUR
- Change PIN code

The ATM withdrawal fee should be 2%, and a maximum of 10,000 GEL can be withdrawn within 24 hours.

### Reports

Bank managers should be able to view the following types of reports (the API should return results in JSON format):

- User Statistics
    - Number of users registered this year
    - Number of users registered in the last year
    - Number of users registered in the last 30 days
- Transaction Statistics
    - Number of transactions made in the last 1 month/6 months/1 year
    - Volume of income from transactions in the last 1 month/6 months/1 year (in GEL/USD/EUR)
    - Average income from one transaction (in GEL/USD/EUR)
    - Number of transactions in the last month by days (chart)
    - Total amount of money withdrawn from ATMs

### Database
![image](https://github.com/user-attachments/assets/15fa0346-4874-475e-9cc2-91548aefd0e4)

### Clean Architecture

The project follows the principles of Clean Architecture to ensure separation of concerns and maintainability. The architecture is divided into several layers:

- **Domain Layer**: Contains the core business logic and entities.
- **Application Layer**: Contains the application services and business rules.
- **Infrastructure Layer**: Contains the implementation of external services, repositories, and data access.
- **Presentation Layer**: Contains the API controllers and user interface.

### Web API

The project provides a Web API for interacting with the banking system. The API is built using ASP.NET Core and follows RESTful principles. The API includes the following endpoints:

- **Authentication**: Endpoints for user authentication and authorization.
- **Internet Banking**: Endpoints for managing users, accounts, and cards.
- **ATM Client**: Endpoints for card authorization and ATM operations.
- **Reports**: Endpoints for generating various reports and statistics.

### Technologies

The project uses the following technologies:

- **ASP.NET Core**: For building the web API.
- **Entity Framework Core**: For data access and ORM.
- **Dapper**: For executing raw SQL queries.
- **Serilog**: For logging.
- **Swagger**: For API documentation.
- **JWT**: For authentication and authorization.
- **SQL Server**: For the database.

### Architectural Principles

The project follows these architectural principles:

- **Separation of Concerns**: Different layers handle different responsibilities.
- **Dependency Injection**: Dependencies are injected to promote loose coupling.
- **SOLID Principles**: The code adheres to SOLID principles to ensure maintainability and scalability.
- **Clean Code**: The code is written in a clean and readable manner.
