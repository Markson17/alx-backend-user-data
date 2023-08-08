## 0x00-personal_data

### Introduction
This project contains a Python function called `filter_datum`, which obfuscates log messages by replacing certain field values. The function uses regular expressions (`re.sub`) to perform the substitutions with a single regex.

### Function Signature
```
def filter_datum(fields: List[str], redaction: str, message: str, separator: str) -> str:
    """
    Obfuscates log message by replacing occurrences of certain field values.

    Args:
        fields (List[str]): A list of strings representing all fields to obfuscate.
        redaction (str): A string representing by what the field will be obfuscated.
        message (str): A string representing the log line.
        separator (str): A string representing by which character is separating all fields in the log line (message).

    Returns:
        str: The obfuscated log message.
    """
```

## 1. Log formatter

### Introduction
This part of the project contains a class `RedactingFormatter`, which is a custom log formatter. The formatter accepts a list of fields as a constructor argument and filters values in incoming log records using the `filter_datum` function. The values for fields in the specified list are redacted in the log output.

### Class Signature
```
class RedactingFormatter(logging.Formatter):
    """
    Redacting Formatter class that filters specified fields in log records.

    Attributes:
        REDACTION (str): The string used for redaction.
        FORMAT (str): The log record format string.
        SEPARATOR (str): The character separating fields in the log message.

    Methods:
        format(record: logging.LogRecord) -> str:
            Formats the log record with redacted values for specified fields.
    """
```

## 2. Create logger

### Introduction
In this part, the `get_logger` function is implemented, which returns a logging.Logger object. The logger is named "user_data" and only logs up to the `logging.INFO` level. It does not propagate messages to other loggers. The logger has a `StreamHandler` with the `RedactingFormatter` as the formatter.

### Function Signature
```
def get_logger() -> logging.Logger:
    """
    Returns a logging.Logger object with specific configuration.

    Returns:
        logging.Logger: The configured logger.
    """
```

### Constant
```
PII_FIELDS = ["name", "email", "phone", "ssn", "password"]
```

## 3. Connect to secure database

### Introduction
This part of the project demonstrates connecting to a secure holberton database to read a users table. The database credentials are stored as environment variables on the server: `PERSONAL_DATA_DB_USERNAME` (default "root"), `PERSONAL_DATA_DB_PASSWORD` (default empty string), `PERSONAL_DATA_DB_HOST` (default "localhost"), and `PERSONAL_DATA_DB_NAME`.

### Function Signature
```
def get_db() -> mysql.connector.connection.MySQLConnection:
    """
    Returns a connector to the database.

    Returns:
        mysql.connector.connection.MySQLConnection: The database connector object.
    """
```

## 4. Read and filter data

### Introduction
The `main` function in this part retrieves all rows in the `users` table from the database and displays each row under a filtered format using the logger "user_data."

## 5. Encrypting passwords

### Introduction
The `hash_password` function is implemented to hash passwords using the bcrypt package. The function returns a salted, hashed password as a byte string.

### Function Signature
```
def hash_password(password: str) -> bytes:
    """
    Hashes the password using bcrypt.

    Args:
        password (str): The password to hash.

    Returns:
        bytes: The salted, hashed password.
    """
```

## 6. Check valid password

### Introduction
The `is_valid` function is implemented to validate passwords by checking if they match the hashed password using bcrypt.

### Function Signature
```
def is_valid(hashed_password: bytes, password: str) -> bool:
    """
    Validates the password by checking if it matches the hashed password.

    Args:
        hashed_password (bytes): The hashed password.
        password (str): The password to check.

    Returns:
        bool: True if the password is valid, False otherwise.
    """
```