# Devops

# TD part 1 Docker
Create a 3-tiers app:
- HTTP server
- Backend API
- Database

##Download the containers images
The PostgreSQL object-relational database system provides reliability and data integrity.
- docker pull postgres

OpenJDK is an open-source implementation of the Java Platform, Standard Edition
- docker pull openjdk

The Apache HTTP Server Project
- docker pull httpd

Database management in a single PHP file.
- docker pull adminer

## Create The database :

Database folder:
    Dockerfile
    
    FROM postgres:11.6-alpine
    
    ENV POSTGRES_DB=db \
        POSTGRES_USER=usr \
        POSTGRES_PASSWORD=pwd
Creates the postgres DB container image

With docker terminal go to the Dockerfile folder and run :
 
    docker build -t raph-tp1/database .
   
  Builds the image and calls it raph-tp1/database from the . folder
  
     docker network create devops
     
  Creates a network called devops. It will allow containers to communicate with each other.
  
    docker run -p 5432:5432 --network=devops --name tp1-database raph-tp1/database 
    
  Creates a DB container out of the image with the name 'tp1-database' and adds it to the devops network
  
 - On a new terminal :
 
 
     docker run --network=devops --link tp1-database:db -p 8080:8080 adminer  
 Creates a admirer that helps visualise the DB at URL= 192.168.99.101:8080
    
## Why should we run the container with a flag -e to give the environment variables ?
