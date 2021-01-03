## How to create MySQL database on docker
### Prepare for project
- Install docker on your host
- Create database data directory on your host
- Start mysql database container
  - docker run --detach --name=test-mysql --env="MYSQL_ROOT_PASSWORD=123456" --publish 6603:3306 --volume=C:\work\mytraining\mysql\data:/var/lib/mysql mysql
- Login to mysql container, and make below changes.
  * docker exec -it test-mysql bash
  * mysql -uroot -p
  * ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY '123456';
- Use Mysql-Front connect to above database with localhost:6063

- For more denials, check link https://severalnines.com/database-blog/mysql-docker-containers-understanding-basics