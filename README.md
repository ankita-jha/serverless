[![Build AMI and Deploy](https://github.com/ankita-jha-cloud/webapp)](https://github.com/ankita-jha/infrastructure)

# Product Management System 🛒

This Node.js application is a Product Management System that allows users to create, update, and delete products. It includes user authentication using basic HTTP authentication with email and password.

## Technologies Used 🚀

- **Node.js**: Server-side JavaScript runtime.
- **Express**: Web application framework.
- **Sequelize**: ORM for database interactions.
- **bcrypt**: Password hashing and verification.
- **AWS SDK**: Interacts with Amazon Simple Notification Service (SNS).
- **Winston**: Logging framework.
- **CSV Parser**: Processes CSV files for user account management.
- **StatsD**: Collects custom application metrics.

## Database 🗃️

The application uses Sequelize to interact with the relational database, which includes tables for products and users.

## API Endpoints 🌐

### Health Check

- `GET /healthz`: Verifies the database connection.

### Product Endpoints

- `GET /v1/products`: Retrieve all products.
- `GET /v1/products/:id`: Retrieve product details by ID.
- `POST /v1/products`: Create a new product with validations:
  - Name: Non-empty string.
  - Price: Positive number.
  - Quantity: Positive integer.
  - Description: String.
- `PUT /v1/products/:id`: Update a product with the same validations as creation.
- `DELETE /v1/products/:id`: Delete a product.

## Authentication 🔐

Basic HTTP authentication with email and password encoded in base64 is used for user authentication.

## Product Submission and SNS Integration 📤

On product creation or update, a message is published to an AWS SNS topic for notification or integration with other services.

## Logging 📝

Winston is used for logging to the console and a file (`app.log`).

## CSV Processing 📊

The application includes a function (`processCSVFile`) for reading and processing CSV files to create or update user accounts.

## Configuration ⚙️

Configuration settings are managed via environment variables.

```env
DB_HOST=127.0.0.1
DB_USER=your-user
DB_PASSWORD=your-password
DB_NAME=your-dbname
PORT=3000
CSVPATH=path-to-your-csv
accessKeyId=your-aws-access-key-id
secretAccessKey=your-secret-access-key
region=us-east-1
topicarn=your-topic-arn
