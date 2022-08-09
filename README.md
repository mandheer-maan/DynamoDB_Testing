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
1. 
```

### Prepare chrome related drivers (in .zip file)
```
cd Serverless_Project_Using_Selenium_Python;
chmod +x install.sh;
./install.sh
```

### Deploy Selenium Layers
```
cd seleniumLayer;
serverless deploy 
```


### Deploy Lambda Function
```
cd ../lambda;
serverless deploy 
```

### Start Testing
   - Go to **/lambda** directory  

```
serverless invoke --function hello
```

### You should get Response as below

``` json
{
"statusCode": 200,
"body": "Headless Chrome Initialized, Page title Home | Neami    National"
}
```

## Project Hierarchy
```
── /seleniumLayer/  # lambda layers
  ├── /selenium  lambda layer of selenium lib
  │  └──/python/      # python libs
  │   └── /lib/    
  │     └── /python3.6/*    
  ├── /chromedriver/    # lambda layer of headless Chrome 
  │ ├── /chromedriver   # chrome driver
  │ └── /headless-chromium # headless chrome binary
  └── /serverless.yaml     
── /lambda/            # lambda function
  ├── /handler.py      # source code of lambda function 
  └── /serverless.yaml # serverless config\
  
  ```
  
- **For Reference go through [this link](https://github.com/yai333/Selenium-UI-testing-with-AWS-Lambda-Layers).** :thumbsup:
