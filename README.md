# Docker IP Geo Location Containerized Project

## About the project

This is a simple project to get IP geolocation from the https://ipgeolocation.io/ using their API services. We have implemented the project with three-layer.

- Frontend / GUI
- API service
- Backend.

## Features

### Frontend / GUI

It is an application coded in Flask which displays the information of the given IP address (like Continent Name, Continent Code, Country Name, ISP, and cache information) in a user-friendly interface.

### API service

It is an application coded in Flask which displays all the IP information in JSON format. 

Once the code gets an IP request the code will fetch the details from https://ipgeolocation.io/ using API. The API request required an api_key provided by https://ipgeolocation.io/. To secure the key I have stored the key in AWS secure manager and the code will use while processing API requests. 

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot(3).png)
![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot(4).png)


### Backend

It is a REDIS database for caching purposes which stores the IP and its location based on key-value structure.

The API service code will pass a copy of fetched data to the backend. So that the backend will server if the user request for same data. It will be more faster. 

# Architecture

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Diagram.png)

## Building Docker images

For deploying the 3 layer flask application, we need to build custom images for the Frontend and API service using a Dockerfile.

I have created Docker files for each container and you find the same from the repo. The new build containers are placed at docker hub.


# Run the containers

You can either deploy the containers manually using docker commands or using docker-compose. I will be deploying this application using docker-compose.

```
docker-compose up -d
```
# Result

You can access the front end of main application in the GUI format - http://<domain.com>/ip/1.1.1.1

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot-1.png)

You may also access the RAW JSON contents using the format - http://<domain.com>:8080/api/v1/1.1.1.1

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot-2.png)
  
  
> replace <domain.com> with your instance IP address or connected domain name.
> Also, replace 1.1.1.1 with IP you want to check the geolocation.
