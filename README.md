# DynamoDB_Testing

### First create a new java maven project in any IDE or VS Code image and name the project as **DynamoDB_Testing**

### Create a new java file as provided in this project
```
src/main/java/com/example/HelloWorldHandler.java
```
### Create a new html file as provided in this project
``` 
src/main/java/com/example/index.html
```
### Import the required AWS Java dependencies in pom.xml i.e provided in the root directory

### Run the below command to package all the required dependencies in a .jar file an it will create a target folder in the root directory
```
mvn clean package
```

### Login to AWS Console Management

```
pip3 install -t Serverless_Project_Using_Selenium_Python/seleniumLayer/selenium/python/lib/python3.6/site-packages selenium==2.37
```

### Provide the name for Selenium layer and Lambda function 
(Replace ```PROJECT_NAME``` with user-defined name) 
```
sed -i 's/project1/PROJECT_NAME/g' Serverless_Project_Using_Selenium_Python/seleniumLayer/serverless.yaml
sed -i 's/project1/PROJECT_NAME/g' Serverless_Project_Using_Selenium_Python/lambda/serverless.yaml
```

### Configure AWS profile
```
aws configure set aws_access_key_id "AWS_ID";
aws configure set aws_secret_access_key "AWS_ACCESS_KEY";
aws configure set region "us-east-1";
aws configure set output "json";
aws configure set aws_profile "PROFILE_ID";
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
