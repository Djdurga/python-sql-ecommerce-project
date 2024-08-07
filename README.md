# Python MySQL Connection Guide

This guide provides instructions on how to connect Python (using Anaconda) to MySQL Workbench and extract data.

## Prerequisites

1. **Python**: Make sure you have Python installed. It's recommended to use Anaconda for managing your Python environment.
2. **MySQL Workbench**: Ensure that MySQL Workbench is installed and running, with access to the database you want to connect to.
3. **MySQL Connector**: Install the MySQL Connector using pip.

   ```bash
   pip install mysql-connector-python

   import mysql.connector
```bash
try:
    connection = mysql.connector.connect(
        host='your_host',         # e.g., 'localhost' or IP address
        user='your_username',     # MySQL username
        password='your_password', # MySQL password
        database='your_database'  # Database name
    )

    if connection.is_connected():
        print("Connection successful")

        cursor = connection.cursor()
        cursor.execute("SELECT * FROM your_table")
        results = cursor.fetchall()

        for row in results:
            print(row)

except mysql.connector.Error as err:
    print(f"Error: {err}")

finally:
    if connection.is_connected():
        cursor.close()
        connection.close()
        print("MySQL connection is closed")


