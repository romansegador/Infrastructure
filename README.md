
# Infraestructure
This repo intends to collect docker-compose files needed to set up the infrastructure needed for other workshops.

I'm not the author of any of this files, just adding here to make it easy to access:

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

## If you want to run all the apps

1. Start Kafka
2. Start Books Service
3. Start Testers Service (Needs Kafka & Books service running)
4. Start Web-app (Needs Books Service running)
5. Start Activity Service (Needs Kafka Running)


### Presentation

Workshop Presentation: https://github.com/romansegador/Infrastructure/blob/master/Contract%20Testing.pdf
