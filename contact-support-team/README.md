
# Contact Support Microservice

This Docker image provides a microservice for handling contact messages and form submissions. It allows retrieving a contact message and submitting a contact form.

Contact Support Microservice includes database integration, which relies on environment variables to establish a connection with a MongoDB database for storing and retrieving contact messages.

### Building the Image

to build the Docker image, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Run the following command to build the image:
   ```bash
   docker build -t contact-support-microservice:1.0.0 .
   ```
   This command will build the Docker image using the provided Dockerfile and tag it as `contact-support-microservice:1.0.0`.



### API Endpoints

- `GET /api/contact-message`: Retrieves a contact message.
- `POST /api/contact-submit`: Submits a contact form.

## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.