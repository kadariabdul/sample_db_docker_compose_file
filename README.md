# Docker Compose Setup

This repository contains a Docker Compose configuration file to set up a multi-container environment with MySQL, phpMyAdmin, MongoDB, and PostgreSQL.

## Services

- **db (MySQL):**
  - Image: mysql:latest
  - Environment:
    - MYSQL_DATABASE: admin
    - MYSQL_USER: admin
    - MYSQL_PASSWORD: admin
    - MYSQL_ROOT_PASSWORD: admin
  - Volume: db_data

- **phpmyadmin:**
  - Image: phpmyadmin/phpmyadmin:latest
  - Environment:
    - PMA_HOST: db
    - MYSQL_ROOT_PASSWORD: admin
  - Port: 8080 (Mapped to container port 80)
  - Network: app-network

- **mongodb:**
  - Image: mongo:6-jammy
  - Port: 27078 (Mapped to container port 27017)
  - Volume: dbdata6
  - Network: app-network

- **postgresql:**
  - Image: postgres:latest
  - Environment:
    - POSTGRES_DB: admin
    - POSTGRES_USER: admin
    - POSTGRES_PASSWORD: admin
  - Volume: postgres_data
  - Network: app-network

## Usage

1. Make sure you have Docker and Docker Compose installed on your machine.

2. Clone this repository:
   ```bash
   git clone https://github.com/kadariabdul/sample_db_docker_compose_file.git
   ```

3. Navigate to the project directory:

    ```bash
    cd sample_db_docker_compose_file
    ```
4. Run the following command to start the services in the background:

    ```bash
    sudo docker-compose up -d
    ```

5. Access phpMyAdmin at http://localhost:8080 using the credentials (Username: admin, Password: admin).

## Notes
The provided configurations use default credentials. For a production environment, it is recommended to update passwords and other sensitive information.

Customize the configurations in the docker-compose.yml file according to your requirements.

Ensure that the necessary ports (8080, 27078, etc.) are available and not already in use on your machine.

Feel free to raise issues or contribute to improve this setup.
