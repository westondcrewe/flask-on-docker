# README for Flask-on-Docker
## Overview
This repository creates a web app that allows users to upload and view media files. The app is containerized in Docker and uses Flask's Python web development framework and a Postgres database for user information. Nginx acts as a reverse proxy for the app, and Gunicorn is used as a WSGI server to handle client requests. The app serves static files, like ```hello.txt``` in the ```project/static``` subfolder, as well as user-uploaded files, as shown in this screen recording. 

![CSCI143-HW3-ScreenRecord](https://github.com/westondcrewe/flask-on-docker/assets/123044932/42cd55a5-824f-464d-b02f-be6d2f580cde)

## Instructions
### Development
To run the development services of this project properly, the user should follow these steps and commands:
  1. From the root folder, run the command
   ```
	$ docker-compose up -d --build
   ```


### Production
To run the production services of this project properly, the user should follow these steps and commands:
  1. Create a file in the root folder with the command ```vim .env.prod.db``` to define user-specific environment variables. The file should contain the following lines:
	```POSTGRES_USER=<username>
	   POSTGRES_PASSWORD=<passwork>
	   POSTGRES_DB=<database_name>```
  2. Run the command ```docker-compose -f docker-compose.prod.yml up -d --build``` to build and start the services in the ```docker-compose.prod.yml``` file
  3. Run the command ```docker-compose -f docker-compose.prod.yml exec web python manage.py create_db``` to create the Postgres database
  4. Navigate to [http://localhost:1337/uploads](http://localhost:1337/uploads) to upload an image, and [http://localhost:1337/media/IMAGE_FILE_NAME](http://localhost:1337/media/IMAGE_FILE_NAME) to view the image
     
