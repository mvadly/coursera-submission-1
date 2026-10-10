# ci-cd-final-project

## Project name
**ci-cd-final-project**

## Description
A **Node.js/Express.js Counter Service** microservice built as the final project for the **CI/CD Tools and Practices** course.

The project demonstrates a complete Continuous Integration / Continuous Delivery pipeline:

- **GitHub Actions** for CI: install dependencies, **lint with ESLint**, and **run unit tests with Jest** on every push to `main`.
- **Tekton** pipelines on OpenShift for CD: `cleanup` and `jest` tasks wired into an OpenShift Pipeline.
- Automated deployment of the counter service to an OpenShift cluster.

## Features
- RESTful API for managing counters
- In-memory storage
- Comprehensive error handling
- Security middleware (Helmet, CORS)
- Logging middleware
- Full test coverage with Jest
- Docker support
- Health check endpoint

## API Endpoints
- `GET /` - Service information
- `GET /health` - Health check
- `GET /counters` - List all counters
- `POST /counters/:name` - Create a new counter
- `GET /counters/:name` - Read a specific counter
- `PUT /counters/:name` - Increment a counter
- `DELETE /counters/:name` - Delete a counter

## Project structure
```text
.
├── .github/
│   └── workflows/
│       ├── README.md
│       └── workflow.yml        # GitHub Actions CI workflow (ESLint + Jest)
├── .tekton/
│   ├── README.md
│   └── tasks.yml               # Tekton Tasks: cleanup, jest
├── bin/
│   └── setup.sh                # Environment setup script
├── src/
│   ├── app.js                  # Express application
│   ├── middleware/
│   │   ├── errorHandler.js
│   │   └── logger.js
│   ├── routes/
│   │   └── counters.js
│   └── utils/
│       └── status.js
├── tests/
│   └── counters.test.js        # Jest unit tests
├── .eslintrc.js
├── .gitignore
├── Dockerfile
├── LICENSE
├── package.json
├── Procfile
└── README.md
```

## Setup
Install the project dependencies:

```bash
npm install
```

Run the service:

```bash
npm start
```

## Running the tests
Run the Jest unit tests:

```bash
npm test
```

Run the linter:

```bash
npm run lint
```

## CI/CD
- **.github/workflows/workflow.yml** - GitHub Actions workflow that runs the CI checks (ESLint linting and Jest unit tests).
- **.tekton/tasks.yml** - Tekton Tasks used by the OpenShift Pipeline: the `cleanup` task empties the workspace, and the `jest` task clones the repository, installs dependencies, and runs the Jest unit tests.

## License
Licensed under the Apache License. See [LICENSE](./LICENSE).