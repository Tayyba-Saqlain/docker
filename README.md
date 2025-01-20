# docker

# Technical Documentation: Dockerized Microservices Project

## Introduction

This technical documentation provides an overview of a Dockerized microservices project composed of four services: one for the database and three others for different tasks. The project uses Docker Compose to orchestrate and manage these services.

### Project Structure

The project consists of the following services:

1. **MongoDB Service (`mongo-db`):** This service runs a MongoDB container, serving as the database for the other microservices. It is configured with authentication using a root username and password and mounts a volume to persist data.

2. **Content Service (`content-service`):** This microservice is responsible for handling content-related tasks. It communicates with the MongoDB database to manage content-related data. It exposes port 3001 for external communication.

3. **Interaction Service (`interaction-service`):** The interaction service is responsible for managing user interactions with the system. It communicates with the MongoDB database to store interaction-related data. It exposes port 3002 for external communication.

4. **User Service (`user-service`):** This microservice deals with user-related tasks and manages user data. It communicates with the MongoDB database for user data storage. It exposes port 3003 for external communication.

## Deployment Requirements

To deploy and run this project successfully, ensure that the following requirements are met:

1. **Docker:** Docker must be installed on the host machine where you intend to run this project.

2. **Docker Compose:** Docker Compose is required to manage and orchestrate the multiple containers. Ensure Docker Compose is installed and available on the host machine.

3. **Project Source Code:** The source code for each microservice should be available in the specified directories (`content-service`, `interaction-service`, and `user-service`). These source code directories should contain the necessary Dockerfiles and application code.

## Configuration

### MongoDB Configuration

- The MongoDB service (`mongo-db`) is configured with the following environment variables:

  - `MONGO_INITDB_ROOT_USERNAME`: Set to `"root"` for the root user.
  - `MONGO_INITDB_ROOT_PASSWORD`: Set to `"example"` for the root user's password.

### Microservices Configuration

Each of the three microservices (`content-service`, `interaction-service`, and `user-service`) is configured with a `DATABASE_URL` environment variable. This variable specifies the MongoDB connection string, including the authentication credentials:

- `DATABASE_URL`: Specifies the connection URL for the respective microservice to connect to MongoDB. It uses the root username and password to authenticate and connects to the appropriate database.

## Deployment

To deploy the project and start the microservices, follow these steps:

1. Clone the project repository to your local machine, ensuring you have the necessary source code for each microservice.

2. Navigate to the directory containing the `docker-compose.yml` file.

3. Open a terminal window in the project directory and run the following command to start the Docker containers:

 `-d` flag runs the containers in detached mode, allowing them to run in the background.

## Accessing Services

You can access the microservices through their respective endpoints as mentioned below. The services communicate with the MongoDB database using the provided connection strings.

1. Wait for the containers to start. You can check the container logs using `docker-compose logs` to monitor their status.

2. Once the containers are running, the microservices will be accessible as follows:

- Content Service: [http://localhost:3001](http://localhost:3001)
- Interaction Service: [http://localhost:3002](http://localhost:3002)
- User Service: [http://localhost:3003](http://localhost:3003)

## Maintenance

To stop and remove the containers, use the following command:


This will stop and remove the containers, but it will not delete the persistent MongoDB data, as it is stored in a volume (`mongo-db-data`).

## Conclusion

This documentation provides an overview of a Dockerized microservices project with a MongoDB database and three distinct microservices. By following the deployment instructions and ensuring the prerequisites are met, you can successfully run and manage these microservices on your local or remote environment.
