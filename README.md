# Infraestructure

# Workshop

In order to start all the application that will be covered in the workshop, including the needed infrastructure, just run the [docker-compose](docker-compose.yml) located in the root file.
First time, you will need to pull all the images (it will take some time): ```docker-compose pull``` at the root folder of this repo.
Afterwards just write the command  ```docker-compose up -d``` at the root folder of this repo to start the following (it could take a minute after that command finishes start all the apps async):

* [Pact-broker](http://localhost:9292): Open your browser with url http://localhost:9292
* [Web-app](http://localhost:12220): Open your browser with url http://localhost:12220
* Books-service: Endpoints exposed in localhost:32800
  * [get all books](http://localhost:32800/api/books) -> http://localhost:32800/api/books (use postman, insomnia, etc...)
  * [get books by author](http://localhost:32800/api/books/byauthor?firstName=Lisa&lastName=Crispin) http://localhost:32800/api/books/byauthor?firstName=Lisa&lastName=Crispin (use postman, insomnia, etc...)
* Testers-service: Endpoints exposed in localhost:32801
  * [get all testers](http://localhost:32801/api/testers) -> http://localhost:32801/api/testers (use postman, insomnia, etc...)
* Activity-service: This service just read from a Kafka topic and log a message each time the endpoint in Testers service is called.
  * Access the logs for the container by:
    * ```docker ps | grep activity-service``` -> note the container id, for example 0fa89fb99408
    * ```docker logs --follow <containerId>``` -> example ```docker logs --follow 0fa89fb99408```
* Kafka: connect your apps to localhost:9092


This repo intends to collect docker-compose files needed to set up the infrastructure needed for a workshop.

Some of the docker-compose files used here are not mine:

* Pact-broker: Thanks to the pact-foundation =>  https://github.com/pact-foundation/pact-broker-docker/blob/master/docker-compose.yml
* Apache Kafka: https://github.com/confluentinc/cp-all-in-one/blob/6.0.0-post/cp-all-in-one-community/docker-compose.yml


## Architecture of the demo
![Demo Arch](https://github.com/romansegador/Infrastructure/raw/master/Workshop%20Arch.jpg)


## Repositories

- Web-app: https://github.com/romansegador/web-app
- Books Service: https://github.com/romansegador/books-service
- Testers Service: https://github.com/romansegador/testers-service
- Activity Service: https://github.com/romansegador/activity-service

## If you want to try Contract Testing

You don't need kafka runnig. You only need the Pact Broker started.
Examples are:
- Web-app: Consumer example in angular (producer is Books service)
- Books-Service: Producer example in Spring boot (REST)
- Testers-Service (Spring boot): 
  - Consumer example (REST) for call to Books Service.
  - Producer example (Messaging-Kafka). Event emmited for each call to the exposed endpoint.
- Activity-service: Consumer example for Kafka (Spring boot).


### Presentation

Workshop Presentation: https://github.com/romansegador/Infrastructure/blob/master/Contract%20Testing.pdf
