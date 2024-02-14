 
# Flask App with MySQL Docker Setup

This is a simple Flask app that interacts with a MySQL database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend.

1. Clone git repo
	`git clone <repo url>`
2. Build dockerfile
	`docker build -t flask-app .`
3. Create network
	`docker network create two-tire-app-nw`
4. Run mysql container
	`docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=test@123 -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --name mysql --network two-tire-app-nw mysql:latest`
5. Enter into mysql container
  `docker exec -it <container id> bash`
6. Enter password to enter into mysql shell
	`mysql -u root -p`
7. Create database
	`CREATE DATABASE default_db;`
8. Create table

```
  CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);

```
9. Create container for todo-app


	`docker run -d -p 5000:5000 -e MYSQL_HOST=mysql -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --name flask-container4 --network two-tire-app-nw flask-app:latest`
10. Run on localhost


	`http://localhost:5000/`

