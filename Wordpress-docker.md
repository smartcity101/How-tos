## One site

```bash
version: "3.3"

services:
  db:
    image: mysql:5.7
    volumes:
      - /path/to/db_data:/var/lib/mysql
    container_name: wp-db
    restart: always
    ports:
      - "3306:3306"
    environment:
      MYSQL_DB_NAME: wordpress
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress


  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - /path/to/wordpress_data:/var/www/html
    ports:
      - "8001:80"
    container_name: wp
    restart: always
    environment:
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
```
