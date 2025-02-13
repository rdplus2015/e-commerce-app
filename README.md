# E-commerce Platform with Docker Compose

This project provides a fully containerized e-commerce platform using Docker Compose. It includes multiple microservices, each responsible for a specific part of the platform, such as user authentication, product management, order processing, and more.

## Prerequisites

- Docker installed on your system.
- Docker Compose installed (if not, follow the [official guide](https://docs.docker.com/compose/install/)).

## Getting Started
    
2.  Clone the repository containing the `docker-compose.yml` file.

1.  Build each image by following the documentation for each service, which will show you how to build the images.

3.  Navigate to the directory where the `docker-compose.yml` file is located.
    
4.  Run the following command to start all services:


   ```bash
   docker-compose up -d
   ```
This will start all the microservices and their associated databases in detached mode.

4.  Access the e-commerce UI at `http://localhost:4000`.
    

## Services Overview

-   **E-commerce UI** (React, Tailwind CSS)
    
    -   The frontend application.
    -   Accessible at `http://localhost:4000`.
-   **Contact Support Microservice** (Node.js, Express, MongoDB)
    
    -   Handles customer support messages.
    -   Accessible at `http://localhost:8000`.
-   **Shipping and Handling Microservice** (Java, Spring Boot, PostgreSQL)
    
    -   Calculates shipping fees.
    -   Accessible at `http://localhost:8080`.
-   **Product Catalog Microservice** (Node.js, Express, MongoDB)
    
    -   Manages product data.
    -   Accessible at `http://localhost:3001`.
-   **Order Management Microservice** (Python, FastAPI, PostgreSQL)
    
    -   Handles orders and cart management.
    -   Accessible at `http://localhost:9090`.
-   **Product Inventory Microservice** (Go, Gin, PostgreSQL)
    
    -   Manages product inventory.
    -   Accessible at `http://localhost:3002`.
-   **Profile Management Microservice** (Node.js, Express, MongoDB, JWT)
    
    -   Handles user authentication and profiles.
    -   Accessible at `http://localhost:3003`.


## Running Containers Individually

If you prefer to run containers individually, ensure they are connected to the same Docker network, pass all necessary arguments, create Dockerfiles for the databases, and run the containers.


## Environment Variables

Each microservice requires specific environment variables to function correctly. These are defined in the `docker-compose.yml` file. Refer to the individual service documentation for details.

## Volumes

Docker volumes are used to persist data for databases:

-   MongoDB volumes for `contact-support`, `shipping`, `product-catalog`, and `order-management`.
    
-   PostgreSQL volume for `product-inventory`.
    
-   MySQL volume for `profile-management`.

## Stopping the Services

To stop all services, run:
```bash
docker-compose down
```

This will stop and remove all containers, networks, and volumes defined in the `docker-compose.yml` file.

## License

This project is licensed under the **MIT License.**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.
