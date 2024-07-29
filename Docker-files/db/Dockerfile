FROM mysql:8.0.33
LABEL project="kelvin"
LABEL Author="kelvin1"

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD="welkom01"
ENV MYSQL_DATABASE="accounts"

# Add SQL script to initialize the database

ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql
