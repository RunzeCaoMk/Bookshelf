# stackFinal Integration instruction

This project contains the following components: Persistence: A paging MongoDB database running in a docker container and deployed to AWS via Lightsail.

Microservice: Quarkus microservice with complete CRUD operations compiled to jvm-jar and running in a docker container deployed to AWS via Lightsail on the same Lightsail instances as MongoDB.

AWS Lambda: Integrate your awsContact lambda with your Vaadin-Spring or Android application, deployed to AWS via SAM, and configured to use API-Gateway and SES.

Cognito User Pools: This app integrates user management using Cognito User Pools and is able to scale to an infinite number of users. In practice, this will mean saving the user's email as a field in each of the mongo records, and then when querying the DB, filtering only those records that match that user's email.

Vaadin Web Client: This is a favorite web application with full CRUD (create, read, update, delete) operations on the Google Book model. It integrates a 3rd party RESTful and searchable API -- Google Book API. Once the user finds a favorite item, he may add/delete/update that item in a list of items displayed in the app.

## vaadin-app

### local
To run from the command line, use `mvn` and open http://localhost:8088 in your browser.
make sure to add 'QUARKUS_BASE_URL :: https://container-service-1.fksmr75ckui3s.us-east-2.cs.amazonlightsail.com' to the IntelliJ confuguration

### remote
//to build a war archive, change packaginug to war war //run the following 
'$mvn clean package -Pproduction'
Upload to Elastic Beanstalk and set the environment variable 
'QUARKUS_BASE_URL :: https://container-service-1.fksmr75ckui3s.us-east-2.cs.amazonlightsail.com'
To use the remote app, please use the link below
https://Stackfinalvaadin-env.eba-xfzkqmcm.us-east-1.elasticbeanstalk.com

## Quarkus
This project uses Quarkus, the Supersonic Subatomic Java Framework.

### local
#### To use MongoDB locally:
```shell script
docker run -ti --rm -d -p 27017:27017 mongo:4.0
```
#### To run locally:
You can run the application in dev mode that enables live coding using:
```shell script
./mvnw compile quarkus:dev
```

### remote
#### To use MongoDB remotely:
Use Lightsail - MongoDB with Image 'mongo:4.0' and port and protocol '27014', 'HTTP'
#### To run remotely:
```shell script
docker build -f src/main/docker/Dockerfile.jvm -t {yourDockerHubID}/{a-name-you-like} .
docker upload {yourDockerHubID}/{a-name-you-like}
```
Use Lightsail - Quarkus with Image '{yourDockerHubID}/{a-name-you-like}' and port and protocol '8080', 'HTTP'

To test the remote microservice, please use the link below
https://container-service-1.fksmr75ckui3s.us-east-2.cs.amazonlightsail.com
