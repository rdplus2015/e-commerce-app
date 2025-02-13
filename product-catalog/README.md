# Product Catalog Microservice

This Docker image provides a microservice for managing a product catalog. It allows retrieving all products and fetching a single product by its ID.

the Product Catalog Microservice includes database integration, which relies on environment variables to establish a connection with a MongoDB database for storing and retrieving product data.

## Building the Image

If you want to build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Run the following command to build the image:
   ```bash
   docker build -t product-catalog-microservice:1.0.0 .
   ```
   This command will build the Docker image using the provided Dockerfile and tag it as `product-catalog-microservice:1.0.0`.

### API Endpoints

- `GET /api/products`: Retrieves all products.
- `GET /api/products/:id`: Retrieves a single product by its ID.


## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.