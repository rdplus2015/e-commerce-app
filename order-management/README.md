# Order Management Microservice

This Docker image provides a Spring Boot application for managing user orders in an e-commerce platform. It allows adding products to a cart, calculating cart totals, and processing purchases.

the Order Management Microservice includes MongoDB integration, which relies on environment variables to configure the MongoDB connection and other application settings.

## Building the Image

To build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Build the image using the following command:
   ```bash
   docker build -t order-management:1.0.0 .
   ```

## API Endpoints

- `POST /api/orders/{userId}/cart`: Adds a product to the user's cart.
- `GET /api/orders/{userId}/cart/subtotal`: Retrieves the cart subtotal for the user.
- `GET /api/orders/{userId}/cart/shipping`: Retrieves the shipping total for the user's cart.
- `GET /api/orders/{userId}/cart/total`: Retrieves the total cart value including shipping for the user.
- `POST /api/orders/{userId}/purchase`: Processes the purchase of the user's cart.
- `GET /api/orders/{userId}/cart`: Retrieves all items in the user's cart.

## Environment Variables

The container requires the following environment variables to be set:

- `PRODUCT_INVENTORY_API_HOST`: The URL of the product inventory microservice.
- `PRODUCT_CATALOG_API_HOST`: The URL of the product catalog microservice.
- `SHIPPING_HANDLING_API_HOST`: The URL of the shipping and handling microservice.

These variables are used by the application to communicate with the necessary microservices to fetch product details, inventory status, and shipping information.

## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.