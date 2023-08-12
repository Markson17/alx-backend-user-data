# Session Authentication README

This repository contains code for implementing session-based authentication for the User endpoints of an API. The code is organized into different files and directories to achieve this functionality.

## Prerequisites

Before you begin, make sure you have the following dependencies installed:

- Python 3.x
- Flask
- Other required libraries as specified in the project

## Project Structure

The project is structured as follows:

- **api/v1/auth**: Contains authentication classes and methods.
  - **auth.py**: Defines the Auth class and session_cookie method.
  - **basic_auth.py**: Contains the BasicAuth class for basic authentication.
  - **session_auth.py**: Contains the SessionAuth class for session-based authentication.

- **api/v1**: Contains API related code.
  - **app.py**: Initializes the Flask app and handles routes.
  - **views/users.py**: Implements User endpoints (GET, POST, PUT, DELETE).
  
- **models**: Contains the User model.

## Credits

This project was created as part of an assignment for a course. Credits to the authors involved.

