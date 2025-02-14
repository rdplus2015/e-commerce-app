# E-commerce Platform with Docker Compose

This project provides a fully containerized e-commerce platform using Docker Compose. It includes multiple microservices, each responsible for a specific part of the platform, such as user authentication, product management, order processing, and more.

## Part 1: Local environment context

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

-   **E-commerce UI** (Node.js)
    
    -   The frontend application.
    -   Accessible at `http://localhost:4000`.
-   **Contact Support Microservice** (Flask)
    
    -   Handles customer support messages.
    -   Accessible at `http://localhost:8000`.
-   **Shipping and Handling Microservice** (Go)
    
    -   Calculates shipping fees.
    -   Accessible at `http://localhost:8080`.
-   **Product Catalog Microservice** (Node.js)
    
    -   Manages product data.
    -   Accessible at `http://localhost:3001`.
-   **Order Management Microservice** (Spring Boot)
    
    -   Handles orders and cart management.
    -   Accessible at `http://localhost:9090`.
-   **Product Inventory Microservice** (Flask)
    
    -   Manages product inventory.
    -   Accessible at `http://localhost:3002`.
-   **Profile Management Microservice** (Node.js)
    
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

## Part 2: Deployment on AWS with EC2 and Docker Compose with Persistent Storage

## **1. Launch an EC2 Instance**

### **Step 1: Choose an AMI**

-   Go to the **AWS EC2 Console**.
    
-   Click on **Launch Instance**.
    
-   Select **Ubuntu 22.04 LTS** as the AMI.
    

### **Step 2: Choose Instance Type**

-   Select **t2.micro** (Free Tier eligible) or a larger instance if needed.
    

### **Step 3: Configure Instance Details**

-   Leave most settings as default.
    
-   Ensure **Auto-assign Public IP** is enabled.
    

### **Step 4: Add Storage**

-   Root volume: **20GB gp3** (default).
    
-   Add an additional **EBS volume** for database persistence:
    
    -   Size: **5GB+** (adjust as needed).
        
    -   Type: **gp3**.
        
    -   Attach it to `/mnt/data` (we will mount it later).
        

### **Step 5: Configure Security Groups**

Create a security group with the following rules:


| Protocol   | Port Range | Source    | Purpose                 |
| ---------- | ---------- | --------- | ----------------------- |
| SSH        | 22         | Your IP   | Secure SSH access       |
| HTTP       | 80         | 0.0.0.0/0 | Web server access       |
| HTTPS      | 443        | 0.0.0.0/0 | Secure web traffic      |
| Custom TCP | 4000  | 0.0.0.0/0 | Allow ecommerce-ui (UI of the app) service port|

- Click **Launch**.
- Select or create a new key pair to access the instance via SSH.

## **2. Connect to the EC2 Instance**

```bash
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```

## **3. Attach and Mount the Additional EBS Volume**

### **Step 1: Identify the volume**

```bash
lsblk
```

Find the new volume (e.g., `/dev/xvdf`).

### **Step 2: Format the volume**

```bash
sudo mkfs -t ext4 /dev/xvdf 
```

### **Step 3: Create a mount point and mount the volume**

```bash
sudo mkdir -p /mnt/data
sudo mount /dev/xvdf /mnt/data
```

### **Step 4: Ensure Persistence After Reboot**

- Add the following line to `/etc/fstab`:

```bash
sudo nano /etc/fstab
```

```bash
/dev/xvdf  /mnt/data  ext4  defaults,nofail  0  0 # add this in the file 
```

## **4. Install Docker & Docker Compose**

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io
sudo systemctl enable --now docker
```

### **Install Docker Compose**

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## **5. Deploy Your Application with Docker Compose**

-   Clone your project repository.
    
-   Configure persistent volumes in `docker-compose.yml` by adding `/mnt/data/` before the volume name inside each service. For example:

  ```sh
  volumes:
        - /mnt/data/postgres_product_inventory_data:/var/lib/postgres/data # Persist PostgreSQL data to a volume
  ```
-   Build all images as explained earlier.
-   Start the containers:
```bash
docker-compose up -d
```

- Verify the Deployment with this command `docker ps`

- Access the application via `http://your-ec2-public-ip:4000`


## License

This project is licensed under the **MIT License.**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.

