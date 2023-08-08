# 0x01-Basic_authentication 

This repository contains a simple API with Basic Authentication functionality. The API includes endpoints to manage user data and ensure secure access to resources. Below are the steps to set up and run the API on your local machine.

## Prerequisites

- Python 3.x
- Flask framework

## Getting Started

1. Clone this repository to your local machine:

```bash
git clone https://github.com/<your-username>/alx-backend-user-data.git
cd alx-backend-user-data/0x01-Basic_authentication
```

2. Install the required dependencies:

```bash
pip3 install -r requirements.txt
```

3. Start the server:

```bash
API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
```

The API will now be accessible at `http://0.0.0.0:5000`.

## Endpoints

### /api/v1/status

This endpoint returns the status of the API.

```bash
curl "http://0.0.0.0:5000/api/v1/status"
```

### /api/v1/users

This endpoint requires Basic Authentication. It returns a list of user data.

```bash
curl "http://0.0.0.0:5000/api/v1/users" -H "Authorization: Basic <base64_credentials>"
```

Replace `<base64_credentials>` with your Base64-encoded email and password.

## Authentication

The API uses Basic Authentication for secure access. To authenticate, include an `Authorization` header with the value `Basic <base64_credentials>`. Replace `<base64_credentials>` with your Base64-encoded email and password.

## Error Handling

The API has error handlers for different HTTP status codes, including unauthorized (401) and forbidden (403) access. It also handles missing resources gracefully.

## Custom Authentication

The API supports different authentication mechanisms. You can switch between `Auth` and `BasicAuth` by setting the `AUTH_TYPE` environment variable.

## Additional Features

- The API includes methods to handle user credentials, authorization headers, and user objects based on the provided credentials.
- The API supports password strings containing colons.
- The API supports excluding paths using wildcards in the `require_auth` method.



