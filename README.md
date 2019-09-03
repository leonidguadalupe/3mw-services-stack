# 3mw-services-stack

## Introduction
This repo holds the outer folder structure of the services used for this app.

The docker-compose file has the services and configurations to run the containers. nginx service is also attached here for proxying through backend and frontend.

## Setup

* clone this repository
```bash
git clone https://github.com/leonidguadalupe/3mw-services-stack.git services
```
* change directory to services
```bash
cd services
```
* clone backend repository
```bash
git clone https://github.com/leonidguadalupe/3mw-backend-service.git
```
* clone frontend repository
```bash
git clone https://github.com/leonidguadalupe/3mw-frontend-service.git
```
* clone monitoring repository if available
```bash
git clone https://github.com/<repo>/3mw-monitoring-service.git
```
* build the containers
```bash
docker-compose build
```
* run docker compose
```bash
docker-compose run
```
* go to the backend container, cd to django folder and run migrate
```bash
docker exec -it -u 0 3mw_services_backend_1 /bin/sh
cd src/3mw_backend_service
python manage.py migrate
```
Note: I personally didn't automate this process as it's kinda dangerous to automate the migration process. I believe it is something that should be done manually. However, it all depends on practice and also when we need to do rolling deployment which we really need this kind of automation

Also, there's a big possibility that this will give an error especially if the monitoring service is not yet added. the compose file depends on the monitoring service which will be provided later. By any case that the monitoring service is not available yet, please delete the monitoring service and the depend clause on the docker compose file.

