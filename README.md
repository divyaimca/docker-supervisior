# docker-supervisor

The docker was released keeping in mind, one daemon  per container which makes the container lightweight. Like suppose for running a web application, one container will serve database, one container will server as web server, one container  will server as  caching server connecting to DB.

So while writing a Dockerfile, the limitation  is : only one CMD  parameter can be be used inside it to run a single foreground process, the exit of which will stop the container.

But sometime we may face situations like to run more than one daemon process in a single container that is to setup the complete stack in a single container.

For this we can have two approaches:

1. A bash script that will run all the processes in backened in sequence but the last one should run with only & to run as a foreground process.
2. Using supervisor : Easy templatized way of managing multiple process in the container.
UseCase : I faced a situation where I have to run ssh,httpd,mysql in a single container and here is how I approached it with supervisor.

Now : 

1. docker-compose build (Build the docker image named mywebapp from the docker file)
2. docker-compose up ( will show all the processes started one after another)
3. connect to the coontainer from other terminals
