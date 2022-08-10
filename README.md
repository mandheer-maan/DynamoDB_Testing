# DynamoDB_Testing

### First create a new java maven project in any IDE or VS Code Editor and name the project as **DynamoDB_Testing**

### Create a new java file as provided in this project
```
src/main/java/com/example/HelloWorldHandler.java
```
### Create a new html file as provided in this project
``` 
src/main/java/com/example/index.html
```
### Import the required AWS Java dependencies in pom.xml i.e provided in the root directory
```
<dependencies>
    <dependency>
      <groupId>com.amazonaws</groupId>
      <artifactId>aws-lambda-java-log4j2</artifactId>
      <version>1.5.0</version>
    </dependency>
    <dependency>
      <groupId>org.apache.logging.log4j</groupId>
      <artifactId>log4j-core</artifactId>
      <version>2.17.1</version>
    </dependency>
    <dependency>
      <groupId>org.apache.logging.log4j</groupId>
      <artifactId>log4j-api</artifactId>
      <version>2.17.1</version>
    </dependency>
    <dependency>
      <groupId>com.amazonaws</groupId>
      <artifactId>aws-lambda-java-core</artifactId>
      <version>1.2.1</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/com.amazonaws/aws-lambda-java-events -->
    <dependency>
        <groupId>com.amazonaws</groupId>
        <artifactId>aws-lambda-java-events</artifactId>
        <version>3.11.0</version>
    </dependency>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.4</version>
        <scope>test</scope>
    </dependency
</dependencies>
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>software.amazon.awssdk</groupId>
            <artifactId>bom</artifactId>
            <version>2.2.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

### Run the below command to package all the required dependencies in a .jar file an it will create a target folder in the root directory
```
mvn clean package
```

### Login to AWS Console Management and do the follwing steps 

```
1. Create a new Lambda function by selecting Java 8 on Amazon Linux 1 as runtime environment and Execution role as (Create a new role with basic Lambda permissions)
2. Create a new S3 Bucket and upload the jar file created in the target folder
3. Then, upload the jar file from s3 location into the Lambda function
4. Change the handler path as per requirement as in this case the path is com.example.HelloWorldHandler::handleRequest
5. Test the Lambda function by passing Event JSON as input parameters to the Lambda function
```
### Create an API Gateway with following steps 
```
1. Create a new API by clicking on Create API button and then click omn Build button under REST API
2. Name the API and select the Edge optimized from Endpoint Type drop-down and click Create API
3. Under Actions drop-down select Create Method and choose POST method and tick it.
4. Associate the Lambda function created before and save it
5. Then, Under Actions drop-down click on Enable CORS and replace the existing values
6. Deploy the API under API Actions from Actions drop-down, choose deployment stage i.e [New Stage] and name the Stage name like in my case i.e dev, then click on        Deploy
7. Copy the Invoke URL and use it in the index.html page
```

### Uploading files to S3 Bucket
```
1. Go to the bucket created earlier and upload index.html file into it
2. Then, make the file public using ACL by selecting it under the Actions drop-down.
3. Copy the Object URL under properties tab and then test it.
```
### Start Testing
   - Go to the above URL
   - Enter any text and then clcik on CALL API Button
   - Your desired response will come under Response from Lambda in index.html page


### You should get Response as below if you have entered the Description as "John"

``` json
"Hello from Lambda!{Input text=John}"
```

- **[URL Link](https://dynamodb-testing-bucket.s3.amazonaws.com/index.html)**
