# README for Flask-on-Docker
## Overview
This repository creates a web app that allows users to upload and view media files. The app is containerized in Docker and uses Flask's Python web development framework and a Postgres database for user information. Nginx acts as a reverse proxy for the app, and Gunicorn is used as a WSGI server to handle client requests. The app serves static files, like ```hello.txt``` in the ```project/static``` subfolder, as well as user-uploaded files, as shown in this screen recording. 

![CSCI143-HW3-ScreenRecord](https://github.com/westondcrewe/flask-on-docker/assets/123044932/42cd55a5-824f-464d-b02f-be6d2f580cde)

## Instructions
### Development
To run the development services of this project properly, the user should follow these steps and commands:
  1. From the root folder, run the following command to build and start your server
   ```
	$ docker-compose up -d --build
   ```
  2. Navigate to [http://localhost:5111](http://localhost:5111). You can use the ```curl``` or ```links``` commands to accomplish this directly in the terminal, but it is also possible to use a web browser. The output should be text in JSON formatting, like this:
  ```
{
	"hello": "world"
}
  ```
  3. Run the following commands to create and open a Postgres database
  ```
	$ docker-compose exec web python manage.py create_db
	$ docker-compose exec db psql --username=hello_flask --dbname=hello_flask_dev
  ```
  4. Exit out of the psql terminal environment with the command
  ```
	hello_flask_dev=# \q
  ```
  5. Navigate to [http://localhost:5111/static/hello.txt](http://localhost:5111/static/hello.txt) to ensure that the static file development is running properly. The output should be
  ```
	yo yo yo!
  ```
  6. Navigate to [http://localhost:5111/uploads](http://localhost:5111/uploads) to upload an image, and [http://localhost:5111/media/IMAGE_FILE_NAME](http://localhost:5111/media/IMAGE_FILE_NAME) to view the image. 
  7. Run the following command to shut down the development server.
   ```
	$ docker-compose down -v --remove-orphans
   ```

### Production
To run the production services of this project properly, the user should follow these steps and commands:
  1. Run the following command to build and start the services from the ```docker-compose.prod.yml``` file
```
$ docker-compose -f docker-compose.prod.yml up -d --build
```
  3. Navigate to [http://localhost:1337](http://localhost:1337), the output should be
```
{"hello":"world"}
```
  3. Run the following commands to create and open the Postgres database
```
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
$ docker-compose exec db psql --username=hello_flask --dbname=hello_flask_prod
```
  4. Exit out of the psql terminal environment with the command
```
hello_flask_prod=# \q
```
  5. Navigate to [http://localhost:1337/static/hello.txt](http://localhost:1337/static/hello.txt) to ensure that the static file development is running properly. The output should be
```
yo yo yo!
```
  6. Navigate to [http://localhost:1337/uploads](http://localhost:1337/uploads) to upload an image, and [http://localhost:1337/media/IMAGE_FILE_NAME](http://localhost:1337/media/IMAGE_FILE_NAME) to view the image
  7. Run the following command to shut down the development server.
```
$ docker-compose down -v --remove-orphans
```
