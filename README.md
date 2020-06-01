# Movie Fun!

Smoke Tests require server running on port 8080 by default.

## Build WAR ignoring Smoke Tests

```
$ mvn clean package -DskipTests -Dmaven.test.skip=true
```

## Run Smoke Tests against specific URL

```
$ MOVIE_FUN_URL=http://moviefun.example.com mvn test
```
## Amazon S3 SDK
This project programaticaly connects with an Amazon S3 instance to store images for album covers.

Good Tutorial: https://javatutorial.net/java-s3-example

## User-Defined Services /w Pivotal
Pivotal allows you to persist 3rd-party credentials without exposing them to a code repository.  These credentials will not be displayed in the Pivotal logs and can be used to login to 3rd-party sites.  Follow these steps:

1. Create a user-defined service using the Pivotal console.

2. Type in your 3rd-party credentials along with an endpoint (optional).  

3. **Bind** the service to your application.

The credentials will then be available to the application as an *environment variable*.  

## Environment Variables
In Linux environment (or Git Bash for Windows) you can setup environment variables that represent variables provided by Pivotal. 

From command-line type:

```
export VCAP_SERVICES='{"user-provided": [{"credentials": {"access_key_id": "minioadmin", "bucket": "moviefun", "secret_access_key": "minioadmin", "endpoint": "http://127.0.0.1:9000"}, "name": "photo-storage"}]}'
```
In the above example, a user is passing dummy VCAP_SERVICE information to the application.  These credentials are being used to login to a mock S3 server.

## S3 Simulation using Minio

To simulate use of an S3 bucket locally, you can run a Minio Server

1.) Download from: https://min.io/

2.) Execute following command
```
minio server ${directory_name}
```
All objects saved to mock S3 will be saved in `${directory_name}`
