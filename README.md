# README for Flask-on-Docker
This respository creates a web app that allows users to upload and view media files. The app runs in Docker containers, and uses the Flask's python web development framework and a Postgres database for user information. Nginx acts as a reverse proxy for the app, and Gunicorn is used as a WSGI server to handle client requests. The app serves static files, like ```hello.txt``` in the ```project/static``` subfolder, as well as user-uploaded files, as shown in this screen recording. 

![Uploading flask_on_docker_media_upload.gif…]()


https://github.com/westondcrewe/flask-on-docker/assets/123044932/eaad61b2-7842-4ee5-b232-c274df07ab37

