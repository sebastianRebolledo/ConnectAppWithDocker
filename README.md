# ConnectAppWithDocker

This repository is about Docker and create DockerFile and Docker-Compose of an anithing app
This app need connect with basedata mongo.
![index](https://user-images.githubusercontent.com/43484703/113097724-0bef2300-91bd-11eb-9e70-2325dd538583.jpg)

First I created Dockerfile :
How the applciation is developed with node i have to have the last version of node, that is version 14 = From node:14
Second, the dependecies of app are copied into directory /usr/src/ on container
third, I specific directori of work 
fourth,I bring dependecis of app running npm install
five,Copy all of files of application to directory /usr/src/ of container
six, I expose of port that application will running
seven,I write default commands that run when the container is running 
First I created image of application. The name of image is application

![dockerfile](https://user-images.githubusercontent.com/43484703/113099421-88830100-91bf-11eb-8ac5-8e5ff7d6de98.png)
I created of image with this command with name applicacion.
$ docker build -t applicacion .

And then, I created container with images. I do a portwarding between port of container and port of my host.
$ docker run -d -p 3000:3000 --name app applicacion

![Captura de pantalla de 2021-03-31 01-25-24](https://user-images.githubusercontent.com/43484703/113099761-18c14600-91c0-11eb-8777-b54b61062133.png)

After, I downloaded image of mongo 
$ docker pull mongo

DOCKER COMPOSE:
The images I created earlier are no longer needed when I create the dockercompose file, I just wanted to show something of the process.

I created of docker-compose.yml
I write version of compose file and services of application with some parameters.

Services of componen the applciation is the containers app and db and ther images:
Firts, the firts , the container will call app and the image is applicacion.
I configure of environment of container and I defined variable envoronment MONGO_URL and I especify that app depends of container db or service db.
![Captura de pantalla de 2021-03-31 02-15-52](https://user-images.githubusercontent.com/43484703/113105480-3b0a9200-91c7-11eb-9e25-559c71408c7c.png)

I configure ports and expose container with port 3000 of host machine with port of container .
And then, I especified service db with image mongo

![compose](https://user-images.githubusercontent.com/43484703/113105183-ec5cf800-91c6-11eb-8293-348e4cbe8aa8.jpg)

Finally, I execute comands:
$ docker-compose up -d 
With comand $docker ps I saw caontainers running
![Captura de pantalla de 2021-03-31 02-18-23](https://user-images.githubusercontent.com/43484703/113105764-93419400-91c7-11eb-8fd2-2bc13a6669bf.png)

And I verify funcionally of application on broweser:
![Captura de pantalla de 2021-03-31 02-20-43](https://user-images.githubusercontent.com/43484703/113105894-b9673400-91c7-11eb-986c-b25624cc9c23.png)




