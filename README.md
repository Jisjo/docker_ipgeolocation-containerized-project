# Docker IP Geo Location Containerized Project

## About the project

This is a simple project to get IP geolocation from the https://ipgeolocation.io/ using their API services. We have implimentaed the project with three layer.

- Frontend / GUI
- API service
- Backend.

## Features

### Frontend / GUI

It is an application code in Flask which displays the information of the given IP address (like Continent Name, Continent Code, Country Name, ISP and cache information) in a user-friendly interface.

### API service

It is an application code in Flask which display all the IP information in JSON format. 

Once the service get an IP request the code will fetch the details from https://ipgeolocation.io/. The API request required an api_key provdided by https://ipgeolocation.io/. To secure the key I have stored the key in AWS secure manager and the code will use while procesing api request. 


### Backend

It is a REDIS database for caching purpose which stores the IP and its location based on key-value structure.

The API service code will pass a copy of fectced data to backend. So that the backend will server if the user request for same data. It will be more faster. 

# Architecture

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Diagram.png)

## Building Docker images

For deploying the 3 layer flask application, we need to build custom images for Frontend and API service using a Dockerfile.

I have created a Docker files for each container and you find the same from the repo. The new build containers placed at docker hub.

## Provisioning

The API_KEY in the application is stored as a secret in AWS secret manager.

![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot(3).png)
![image](https://github.com/Jisjo/docker_ipgeolocation-containerized-project/blob/main/Screenshot(4).png)


# Docker compose 

