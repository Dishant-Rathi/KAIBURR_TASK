# Task 1

**NOTE:** [README First](/README.md)

### Requirements

- Java
- Maven
- Spring Boot (Framework)
- MongoDB
- Docker

#### Dependencies

- spring-boot-starter-web
- spring-boot-starter-data-mongodb
- spring-boot-maven-plugin

## Building steps

1. Open the folder `/task1` in your favourite IDE ( VS Code :heart:)
Wait for few minutes while the IDE loads and completes necessary pre-build tasks.

2. Run `mvn clean install`
This will build and install the artifacts in to the local repository.
Required jar file will be created inside `/target` folder.

3. Run the application by clicking `Run` option or pressing `F9`
SpringBoot application server will load and start on port `8080` of the `localhost`.

- GET servers	`localhost:8081/servers/getServer`
Returns a list of "server" objects.

- GET server	by ID	`localhost:8081/servers/getServer?id=<ID>`
Returns a  "server" object matching with ID.

- GET servers	by Name	`localhost:8081/servers/getServer?name=<Nmae>`
Returns a list of "server" objects matching with Name.

- DELETE server	`localhost:8081/servers/deleteServer?id=<ID>`
Deletes a  "server" object matching with ID.

## RestController interface extends MongoRepository

```java
List<Server> findAll();
    
Optional<Server> findById(String Id);
    
void createOrUpdateServer(Server server);
    
void deleteServerById(String Id);
    
List<Server> findByName(String name);
```

## Containerizing the app

`Dockerfile` contains all the commands required to build the app image

`
FROM openjdk:8-alpine
EXPOSE 8081
ADD target/demo.jar demo.jar
ENTRYPOINT ["java", "-Dspring.data.mongodb.uri=mongodb://mongod:27017/servers", "-jar", "/demo.jar"]
`

1. Run the following command to build docker image
`sudo docker build -t <container_image_name> .`
This will create the app container image and add to you local repository.

2. To Run the app from container, run the following command
`sudo docker run -p 80:80 <container_image_name>`
SpringBoot application server will load and start on port `8080` of the `localhost`
You will see application logs in the terminal.

**Note:** The docker-compose part is Documented in Task3

## Consuming APIs

### Using Postman

Run the following created collection to Test and consume the APIs

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/5ff40fbad3968a1b28b0)

**NOTE:** *The above collection is created and tested for `http://127.0.0.1:8081/servers/` endpoint*

### Screenshots

![PutPostManIO](/screenshots/save%20data.png)

![GetAllServerPostManIO](/screenshots/get%20all%20data.png)

![GetServByIdPostManIO](/screenshots/get%20data%20using%20ID.png)

![UpdateOrPutData](/screenshots/update%20data.png)

![DelPostManIO](/screenshots/delete%20data.png)

### Using WebUIForms

**NOTE:** *This part is Documented in Task4*

**If run into problem, do not hesitate to comment or connect :smile: !**
