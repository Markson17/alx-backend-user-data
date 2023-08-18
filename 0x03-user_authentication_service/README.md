# User Authentication Service

This repository contains a set of Python scripts to implement a user authentication service using Flask and SQLAlchemy. The service provides functionality for user registration, login, logout, password reset, and profile management.

## Setup

1. Clone this repository to your local machine:
   ```
   git clone https://github.com/your-username/alx-backend-user-data.git
   cd alx-backend-user-data/0x03-user_authentication_service
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Run the Flask app:
   ```
   python app.py
   ```

The app will be available at http://0.0.0.0:5000.

## Usage

### 1. User Registration

To register a new user, send a POST request to `/users` with form data containing the `email` and `password` fields. If successful, the response will include the registered user's email and a success message.

Example:
```
curl -XPOST localhost:5000/users -d 'email=example@example.com' -d 'password=MySecretPwd'
```

### 2. User Login

To log in, send a POST request to `/sessions` with form data containing the `email` and `password` fields. If the login information is correct, a session will be created and a session ID cookie will be returned.

Example:
```
curl -XPOST localhost:5000/sessions -d 'email=example@example.com' -d 'password=MySecretPwd'
```

### 3. User Profile

To access a user's profile, send a GET request to `/profile` with a session ID cookie. The response will include the user's email.

Example:
```
curl -XGET localhost:5000/profile -b "session_id=<session_id>"
```

### 4. User Logout

To log out, send a DELETE request to `/sessions` with a session ID cookie. The session will be destroyed, and the user will be redirected to the home page.

Example:
```
curl -XDELETE localhost:5000/sessions -b "session_id=<session_id>"
```

### 5. Reset Password

To initiate a password reset, send a POST request to `/reset_password` with form data containing the `email` field. If the email is registered, a reset token will be generated.

Example:
```
curl -XPOST localhost:5000/reset_password -d 'email=example@example.com'
```

### 6. Update Password

To update the password using a reset token, send a PUT request to `/reset_password` with form data containing the `email`, `reset_token`, and `new_password` fields. If the reset token is valid, the password will be updated.

Example:
```
curl -XPUT localhost:5000/reset_password -d 'email=example@example.com' -d 'reset_token=<reset_token>' -d 'new_password=NewSecretPwd'
```

## Testing

To run end-to-end integration tests, create a `main.py` file in the same directory and copy the provided test functions. Replace the placeholders with appropriate values.

Run the tests using:
```
python main.py
```

If the tests run successfully, there will be no output.
