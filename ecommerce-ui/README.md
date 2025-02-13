# E-commerce UI

This Docker image provides a React application with a Node.js server for an e-commerce user interface. The application connects to six different microservices to provide the optimal e-commerce experience.


## Building the Image

If you want to build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.

2. Navigate to the directory where the Dockerfile is located.

3. Run the following command to build the image:
   ```bash
   docker build -t ecommerce-ui:1.0.0 .
   ```

   This command will build the Docker image using the provided Dockerfile and tag it as `ecommerce-ui:1.0.0`.
## Environment Variables

The container requires the following environment variables to be set:

- `REACT_APP_PROFILE_API_HOST`: The URL of the profile management microservice.
- `REACT_APP_PRODUCT_API_HOST`: The URL of the product catalog microservice.
- `REACT_APP_INVENTORY_API_HOST`: The URL of the product inventory microservice.
- `REACT_APP_ORDER_API_HOST`: The URL of the order management microservice.
- `REACT_APP_SHIPPING_API_HOST`: The URL of the shipping and handling microservice.
- `REACT_APP_CONTACT_API_HOST`: The URL of the contact support team microservice.

The application uses the provided environment variables to construct the full URL for making requests to the respective microservices. Each variable should be set to the scheme and hostname of the corresponding service, such as REACT_APP_PROFILE_API_HOST=http://profile-management. The application will then append the appropriate port and path, like :3003/api/update, to complete the URL and send the request to the specified microservice container.

## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.