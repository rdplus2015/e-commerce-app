# Product Inventory Microservice

This Docker image provides a microservice for managing product inventory. It allows retrieving inventory for all products, fetching inventory for a single product by its ID, and reducing the quantity of a product when an order is placed.

the Product Inventory Microservice includes PostgreSQL integration. It now relies on environment variables to establish a connection with a PostgreSQL database for storing and retrieving inventory data.

## Building the Image

If you want to build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Run the following command to build the image:
   ```bash
   docker build -t product-inventory-microservice:1.0.0 .
   ```
   This command will build the Docker image using the provided Dockerfile and tag it as `product-inventory-microservice:1.0.0`.


### API Endpoints

- `GET /api/inventory`: Retrieves inventory for all products.
- `GET /api/inventory/<product_id>`: Retrieves inventory for a single product by its ID.
- `POST /api/order/<product_id>`: Reduces the quantity of a product by 1 when an order is placed.


### API Endpoints

- `GET /api/products`: Retrieves all products.
- `GET /api/products/:id`: Retrieves a single product by its ID.


## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.