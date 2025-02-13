# Shipping and Handling Microservice

This Docker image provides a microservice for calculating shipping fees based on product categories and time of day. It also provides a shipping explanation and returns all shipping fees for products.

the Shipping and Handling Microservice includes MongoDB integration. It now relies on environment variables to establish a connection with a MongoDB database for storing and retrieving product data.

## Building the Image

If you want to build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Run the following command to build the image:
  ```bash
  docker build -t shipping-and-handling:1.0.0 .
  ```
  This command will build the Docker image using the provided Dockerfile and tag it as `shipping-and-handling:1.0.0`.

### API Endpoints

- `GET /shipping-fee?product_id=<product_id>`: Calculates the shipping fee for a product based on its ID.
- `GET /shipping-explanation`: Provides a sophisticated explanation of the shipping fee calculation.
- `GET /all-shipping-fees`: Returns all shipping fees for products.


## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.