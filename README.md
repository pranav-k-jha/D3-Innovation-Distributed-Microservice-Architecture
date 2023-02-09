# Distributed-System-for-Ski-Sports-Industry

This project focuses on developing a distributed system for the digitalization of the ski industry. The system uses RFID lift ticket readers to record the time of the ski ride and the skier's ID at participating ski resorts. The data collected from the resorts will be analyzed to answer questions such as the most heavily used lifts, the skiers who ride the most lifts, and the average number of lifts skiers ride per day. 

The server side uses a Java Servlet hosted on a Web server such as Tomcat or Jetty. A multithreaded Java client will be built to upload 10K lift ride events to the server as quickly as possible. The client will generate lift ride events with random parameters and handle errors if any 5XX or 4XX response codes are received. On completion, the programs will print out the number of successful requests, run time, and throughput. The performance will be profiled and analyzed, including mean and median response time, 99th percentile response time, and standard deviation.

### Import To Eclipse Java EE Edition

1. Download the zip of this repo and unzip it.

2. Import the project into eclipse as a maven project.

   ![import](img/import.gif)

3. Config Run for development.

   ![](img/jettyrun.gif)

4. Config Run for Deployment

   ![deprun](img/deprun.gif)

5. Access servlet.

   ![image-20230115133718047](img/get.png)

   As you have the servlet at `org.example.controller.HelloServlet.java`.



### CMD

#### To develop the project.

``` bash 
mvn jetty:run
```

> The server config for development is at `pom.xml:86`.
>
> Feel free to configure it.



#### To deploy the project.

``` bash
mvn clean install exec:exec
```
> The server config for deployment is in `org.example.EmbeddingJettyStarter`.
>
> Feel free to configure it.



### Configuration of Jetty

#### Configure in coding

In `org.example.EmbeddingJettyStarter`, you can directly change the port or the context path by:

``` java
Server server = new Server(8080);		// change the port number 
// ...
context.setContextPath("/new_context");   // change the context path
// ...
```

Then you can access the servlet by:

http://localhost:8080/new_context/HelloServlet

At the same time, please make sure your servlet's annotation value mapping is valid for the context path:

``` java
@WebServlet(name = "HelloServlet", value = "HelloServlet")
```

Do not add the root in the front:

``` java
@WebServlet(name = "HelloServlet", value = "/HelloServlet")
```
