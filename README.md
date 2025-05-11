# Docker Compose for MySQL and phpMyAdmin

This repository contains a `docker-compose.yml` file to quickly set up and run MySQL with phpMyAdmin for database management.

## Prerequisites

- Docker installed on your system.
- Docker Compose installed.

## Usage

1. Clone this repository or copy the `mysql-docker-compose.yml` file to your project directory.
2. Open a terminal and navigate to the directory containing the `mysql-docker-compose.yml` file.
3. Run the following command to start the services:
    ```bash
    docker compose -f mysql-docker-compose.yml up -d --build
    ```
4. Access phpMyAdmin in your browser at [http://localhost:8080](http://localhost:8080).
5. Use the following credentials to log in:
    - **Server:** `mysql`
    - **Username:** `user`
    - **Password:** `root`

## Configuration

You can modify the `mysql-docker-compose.yml` file to change the MySQL root password, database name, or phpMyAdmin port.

## Stopping the Services

To stop and remove the containers, run:
```bash
docker compose -f mysql-docker-compose.yml down
```

## Example `docker-compose.yml`

```yaml

services:
  mysql:
     image: mysql:8.0
     container_name: mysql
     environment:
        MYSQL_ROOT_PASSWORD: example
     ports:
        - "3306:3306"
     volumes:
        - mysql_data:/var/lib/mysql

  phpmyadmin:
     image: phpmyadmin/phpmyadmin:latest
     container_name: phpmyadmin
     environment:
        PMA_HOST: mysql
        PMA_PORT: 3306
     ports:
        - "8080:80"

volumes:
  mysql_data:
```

## License

This project is licensed under the MIT License.  