# Authentication Microservice

This Docker image provides an authentication microservice with user management functionality. It allows users to sign up, sign in, sign out, and update their profile information. It uses JSON Web Tokens (JWT) for authentication.

the Authentication Microservice includes MySQL integration. It now relies on environment variables to establish a connection with a MySQL database for storing and retrieving user data.

## Building the Image

If you want to build the Docker image yourself, follow these steps:

1. Clone the repository containing the application code.
2. Navigate to the directory where the Dockerfile is located.
3. Run the following command to build the image:
  ```bash
  docker build -t authentication-microservice:1.0.0 .
  ```
  This command will build the Docker image using the provided Dockerfile and tag it as `authentication-microservice:1.0.0`.


## API Endpoints

- `POST /api/signup`: Sign up a new user.
- `POST /api/signin`: Sign in an existing user.
- `POST /api/signout`: Sign out the currently authenticated user.
- `GET /api/protected`: Example of a protected route that requires authentication.
- `PUT /api/update`: Update the profile information of the authenticated user.


## License

This project is licensed under the **MIT License**

## Support

For issues or questions, please [open an issue](https://github.com/rdplus2015/e-commerce-app/issues) on the GitHub repository.