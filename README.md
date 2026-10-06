# KemanaDuitku API

**KemanaDuitku** is a mobile expense-tracking application that helps users record and understand their daily spending.

This repository contains the **Golang backend API** used by the KemanaDuitku iOS and Android applications.

## Overview

The KemanaDuitku API provides the backend services required by the mobile application.

The API is responsible for:

* User authentication
* User management
* Expense management
* Expense categories
* Wallet/account management
* Budget management
* Spending summaries
* Financial data persistence
* Business logic
* API validation

## Tech Stack

* **Go**
* REST API
* JSON
* PostgreSQL
* Docker

Additional infrastructure and services may be added as the application evolves.

## Repository

* Mobile App: `kemanaduitku-app`
* Backend API: `kemanaduitku-api`

## Project Structure

```text
kemanaduitku-api/
├── cmd/
│   └── api/
├── internal/
│   ├── config/
│   ├── handler/
│   ├── middleware/
│   ├── model/
│   ├── repository/
│   ├── service/
│   └── ...
├── migrations/
├── docs/
├── tests/
├── Dockerfile
├── go.mod
├── go.sum
└── README.md
```

The project structure may evolve as the API grows.

## Requirements

Before starting development, install:

* Go
* PostgreSQL
* Docker
* Git

Verify the Go installation:

```bash
go version
```

## Getting Started

Clone the repository:

```bash
git clone <repository-url>
cd kemanaduitku-api
```

Download dependencies:

```bash
go mod download
```

## Configuration

Configuration should be provided through environment variables or environment-specific configuration files.

Example:

```env
APP_ENV=development
APP_PORT=8080

DATABASE_URL=postgres://user:password@localhost:5432/kemanaduitku

JWT_SECRET=change-me
```

**Do not commit secrets, credentials, or production configuration to the repository.**

## Running Locally

Start the required dependencies, such as PostgreSQL.

Then run the API:

```bash
go run ./cmd/api
```

The API will be available at:

```text
http://localhost:8080
```

The actual port and API base path may depend on the application configuration.

## Database

KemanaDuitku uses PostgreSQL for persistent data storage.

Database migrations are stored in:

```text
migrations/
```

Migration tooling will be documented here once the project migration workflow is finalized.

## API

The API follows REST principles and uses JSON for request and response payloads.

Example API structure:

```text
/api/v1
```

Potential endpoints include:

```text
POST   /api/v1/auth/register
POST   /api/v1/auth/login

GET    /api/v1/expenses
POST   /api/v1/expenses
GET    /api/v1/expenses/:id
PUT    /api/v1/expenses/:id
DELETE /api/v1/expenses/:id

GET    /api/v1/categories
POST   /api/v1/categories

GET    /api/v1/budgets
POST   /api/v1/budgets

GET    /api/v1/summary
```

The API contract will be documented as the endpoints are implemented.

## API Documentation

API documentation will be maintained using an API specification such as OpenAPI.

Planned documentation:

```text
/docs
```

Once available, the development API documentation will be accessible from the configured API server.

## Testing

Run all tests:

```bash
go test ./...
```

Run tests with the race detector:

```bash
go test -race ./...
```

Run tests with coverage:

```bash
go test ./... -cover
```

## Code Quality

Format the code:

```bash
gofmt -w .
```

Run static analysis:

```bash
go vet ./...
```

Additional linting tools may be introduced as the project grows.

## Docker

Build the Docker image:

```bash
docker build -t kemanaduitku-api .
```

Run the container:

```bash
docker run --env-file .env -p 8080:8080 kemanaduitku-api
```

For local development, Docker Compose may be introduced to run the API and PostgreSQL together.

## Environments

The project is expected to have separate environments:

```text
Development
    ↓
Staging
    ↓
Production
```

Example API environments:

```text
Development
https://api-dev.kemanaduitku.com

Production
https://api.kemanaduitku.com
```

Environment-specific credentials and secrets must never be committed to Git.

## Git Workflow

Recommended branch naming:

```text
main
develop
feature/<feature-name>
fix/<issue-name>
refactor/<description>
```

Example:

```text
feature/add-expense-api
feature/user-authentication
fix/expense-validation
refactor/expense-service
```

## Commit Messages

Use clear and concise commit messages.

Examples:

```text
feat: add expense creation endpoint
feat: add user authentication
feat: add monthly spending summary
fix: validate expense amount
fix: prevent duplicate expense records
refactor: separate expense service from repository
test: add expense service tests
docs: update API documentation
```

## Roadmap

Potential backend features:

* [ ] User authentication
* [ ] User profile
* [ ] Expense CRUD
* [ ] Expense categories
* [ ] Wallet/account management
* [ ] Monthly budgets
* [ ] Recurring expenses
* [ ] Spending summaries
* [ ] Search and filtering
* [ ] Data export
* [ ] Cloud synchronization
* [ ] Notifications
* [ ] Financial insights
* [ ] API documentation
* [ ] Automated CI/CD

## Security

Security is a core requirement of the API.

The API should:

* Never store plaintext passwords
* Hash passwords using a secure password hashing algorithm
* Validate all incoming requests
* Authenticate protected endpoints
* Authorize access to user-owned resources
* Protect sensitive configuration
* Use HTTPS in production
* Avoid exposing sensitive information in logs
* Apply appropriate rate limiting
* Validate database queries and user input

## License

License information will be added when the project is ready for release.
