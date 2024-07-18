# STEP 1 Create a Docker Network
Create a Docker network to allow the containers to communicate with each other. This step is optional but helps in connecting containers easily.


```
docker network create network_name
```

# STEP 2 Run MySQL Container
Run a MySQL container with the desired configuration. Replace <password> with your preferred MySQL password.

```
docker run -d - name mysql-container - network=mynetwork -e MYSQL_ROOT_PASSWORD=<password> -p 3306:3306 mysql:latest
```

# STEP 3 Run phpMyAdmin Container
Run a phpMyAdmin container and link it to the MySQL container. Replace ` <password> with the MySQL password you set in Step 2.

```
docker run -d - name phpmyadmin-container - network=mynetwork -e PMA_HOST=mysql-container -e PMA_PORT=3306 -p 8080:80 phpmyadmin/phpmyadmin:latest
```

# STEP 4 Access phpMyAdmin

Open your browser and navigate to http://localhost:8080. Log in with the MySQL credentials you provided earlier.

## Notes:
- Make sure to replace <password> with a secure password of your choice.
- You can choose different ports for MySQL and phpMyAdmin if needed.
- The — network flag is used to connect containers to the same network, enabling them to communicate with each other using container names.
- Ensure that the MySQL container is running before starting the phpMyAdmin container.

By following these steps, you should have a running MySQL container and a phpMyAdmin container connected to it. You can manage your MySQL databases using phpMyAdmin through the web interface.