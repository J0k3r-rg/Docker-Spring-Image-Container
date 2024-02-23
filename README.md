# Example for deploy a Spring app in Docker


When we finish the spring project we can create a container that is responsible for compiling and executing it

## DockerFile 

```DockerFile
FROM debian:11-slim

# We update and install what is necessary to run the application
RUN apt-get update && apt-get install -y openjdk-17-jdk maven

# cwe copy the project folder inside the image
COPY ./demo /app

# we are located inside the app folder
WORKDIR /app

# commands that will be executed when creating the container and running it
CMD ["mvn", "clean", "install", "-DskipTests", "exec:java", "-Dexec.mainClass=com.example.demo.DemoApplication"]

#we expose port 8080 of the app
EXPOSE 8080
```


### buil image

 ```docker build -f DockerFile -t <name-image> .```


### start container


 ```docker run -p 8888:8080 <name-image>```
