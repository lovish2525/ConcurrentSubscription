# MyApp

MyApp is a web application built with Go, PostgreSQL, and Redis. It provides user authentication, subscription plans, and more.

## Features

- User registration and authentication
- Subscription plans
- Session management with Redis
- Database migrations with Goose

## Requirements

- Go 1.19+
- PostgreSQL
- Redis

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/myapp.git
    cd myapp
    ```

2. Set up the environment variables:

    ```sh
    export DSN="host=localhost port=5432 user=postgres password=password dbname=concurrency sslmode=disable timezone=UTC connect_timeout=5"
    export REDIS="127.0.0.1:6379"
    ```

3. Run the database migrations:

    ```sh
    make migrate
    ```

4. Build the application:

    ```sh
    make build
    ```

5. Run the application:

    ```sh
    make run
    ```

## Usage

- Access the application at `http://localhost:80`
- Register a new user or log in with the default admin user:
    - Email: `admin@example.com`
    - Password: `password`

## Makefile Commands

- `make build`: Build the application binary
- `make run`: Build and run the application
- `make clean`: Clean the build artifacts
- `make start`: Alias for `make run`
- `make stop`: Stop the running application
- `make restart`: Restart the application
- `make test`: Run all tests
- `make migrate`: Run database migrations
- `make migrate-down`: Rollback database migrations

## Project Structure

- `cmd/web`: Main application entry point
- `migrations`: Database migration files
- `data`: Data models and database interactions

## License

This project is licensed under the MIT License.

## Flow Diagram

```mermaid
graph TD
    A[Start] --> B[Initialize Database]
    B --> C[Initialize Session]
    C --> D[Create Loggers]
    D --> E[Set Up Application Config]
    E --> F[Create Mailer]
    F --> G[Listen for Mail]
    E --> H[Listen for Shutdown]
    E --> I[Listen for Errors]
    E --> J[Serve Web Application]
    J --> K[HTTP Server Starts]
    K --> L[Handle Web Requests]
    H --> M[Shutdown Application]
    I --> N[Log Errors]
    G --> O[Send Mail]