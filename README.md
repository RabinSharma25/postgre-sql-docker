# postgre-sql-docker
Setting up postgreSQL in remote server using docker and configuring it for remote access 

# In local 
1. Building the docker image from he dockerfile
- sudo docker build -t my-postgres-image -f postgresDockerFile .

2. running the docker image 
- sudo docker run --name my-postgres-container -e POSTGRES_USER=myuser -e POSTGRES_PASSWORD=mypassword -e POSTGRES_DB=mydb -p 5432:5432 -d my-postgres-image

# In remote server

1. First build the image in your local 
2. push the docker image to docker hub
 - login to docker 
   - docker login
 - create a docker tag 
   - docker tag my-postgres-image rabinsh/my-postgres-image:latest
 - push the image to docker hub
   - docker push rabinsh/my-postgres-image:latest
3. Now login to your remote server and pull the image from docker hub
   - docker pull rabinsh/my-postgres-image
4. run the image 
   - sudo docker run --name my-postgres-container -e POSTGRES_USER=myuser -e POSTGRES_PASSWORD=mypassword -e POSTGRES_DB=mydb -p 5432:5432 -d rabinsh/my-postgres-image
 