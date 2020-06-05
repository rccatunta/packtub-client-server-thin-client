# Server

This project represents the server within a server-client architecture.

You can run the project using the main class:

- BankingApplication

You can visit the API documentation using the provided swagger ui:
    
`
http://localhost:8080/swagger-ui.html
`


This project also contains the client that can be later consumed.
First check what your IP address is and the replace it in the BankClient file

```java
public static final String SERVICE_BASE_URL = "http://192.168.100.4:8080/";
```

Later, inside the banking-client project, run the following gradle task

```js
$ ../gradlew install
```

It will publish the artifact in the maven local repository so can later us it.

## Tests of functionality
You can test the functionality of this project using this command in Windows 
``curl -H "Content-Type: application/json" -X POST -d "{"""username""":"""rene""","""password""":"""rene"""}" http://localhost:8080/api/public/auth``
If you have Linux or MacOS you have to execute this command
``curl -H "Content-Type: application/json" -X POST -d '{"username":"rene","password":"rene"}' http://localhost:8080/api/public/auth``

After that, the application will return a **Token**, put this token in TOKEN_GOES_HERE, without any quotation marks
``curl -H "x-auth-token: TOKEN_GOES_HERE" -X GET http://localhost:8080/api/secure/balance``

## Common Problems
One conmmon problem occurs when you have the port 8080 is already used. You can discover which application uses this port, executing the following command in Administrator CMD.
``netstat -naob | findstr "8080" ``
After that you can identify the PID of the process and kill it, using Task Manager
