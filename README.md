# Project README: Python Microservices with Docker, MySQL, and RabbitMQ

## Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Prerequisites](#prerequisites)
4. [Setup and Installation](#setup-and-installation)
5. [Configuration](#configuration)
6. [Running the Services](#running-the-services)
7. [Testing](#testing)
8. [Usage](#usage)
9. [Troubleshooting](#troubleshooting)
10. [Contributing](#contributing)
11. [License](#license)

## Introduction
This project demonstrates the implementation of a microservices architecture using Python, Docker, MySQL, and RabbitMQ. The microservices communicate asynchronously via RabbitMQ, and data is stored in a MySQL database. Each microservice is containerized using Docker to ensure portability and ease of deployment.

## Project Structure
```
project-root/
│
├── services/
│   ├── service1/
│   │   ├── app/
│   │   │   ├── __init__.py
│   │   │   ├── main.py
│   │   │   └── ... (other Python modules)
│   │   ├── Dockerfile
│   │   ├── requirements.txt
│   │   └── ...
│   ├── service2/
│   │   ├── app/
│   │   │   ├── __init__.py
│   │   │   ├── main.py
│   │   │   └── ... (other Python modules)
│   │   ├── Dockerfile
│   │   ├── requirements.txt
│   │   └── ...
│   └── ... (additional services)
│
├── docker-compose.yml
├── README.md
└── .env
```

## Prerequisites
Ensure you have the following installed on your system:
- Docker
- Docker Compose
- Python 3.8+
- RabbitMQ
- MySQL

## Setup and Installation

### Step 1: Clone the Repository
```bash
git clone https://github.com/karansinghthkur/python-microservices.git
cd your-repo-name
```

### Step 2: Create a .env File
Create a `.env` file in the root directory of the project and add the necessary environment variables. Example:
```env
MYSQL_ROOT_PASSWORD=your_mysql_root_password
MYSQL_DATABASE=your_database_name
MYSQL_USER=your_mysql_user
MYSQL_PASSWORD=your_mysql_password

RABBITMQ_DEFAULT_USER=your_rabbitmq_user
RABBITMQ_DEFAULT_PASS=your_rabbitmq_password
```

### Step 3: Build and Run Docker Containers
Use Docker Compose to build and start the containers.
```bash
docker-compose up --build
```

This command will build the Docker images and start all the containers defined in `docker-compose.yml`.

## Configuration
Each service has its own configuration files, typically located in the `app/` directory within the service folder. Adjust these configurations as needed to fit your environment and requirements.

## Running the Services
Once the Docker containers are up and running, the microservices will be accessible according to the ports specified in the `docker-compose.yml` file. Verify that the services are running by visiting their respective endpoints.

## Testing
To test the services, you can use tools like Postman or cURL to make requests to the service endpoints. Additionally, unit and integration tests can be added to each service's `tests/` directory and run using a testing framework like pytest.

### Example Command to Run Tests:
```bash
docker-compose exec service1 pytest app/tests
```

## Usage
1. **Service Interaction:** The microservices interact with each other via RabbitMQ for message passing.
2. **Database Operations:** Services perform CRUD operations on the MySQL database.
3. **Endpoints:** Access service endpoints to perform specific operations (e.g., GET, POST requests).

### Example API Request:
```bash
curl -X POST http://localhost:8000/api/v1/resource -d '{"key":"value"}'
```

## Troubleshooting
- **Container Logs:** Check the logs of individual containers for error messages.
  ```bash
  docker-compose logs service1
  ```
- **Database Issues:** Ensure MySQL credentials are correctly set in the `.env` file.
- **Message Queue Issues:** Verify RabbitMQ is running and accessible using the provided credentials.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request.

### Steps to Contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Create a new Pull Request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Feel free to reach out with any questions or issues you encounter. Happy coding!
