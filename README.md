# Spring Boot RabbitMQ Producer

A lightweight Spring Boot application that sends employee information to RabbitMQ as JSON messages.

## About

This project exposes a REST endpoint to publish `Employee` objects to a RabbitMQ direct exchange. It includes:

- Spring Boot 3.5 application
- RabbitMQ integration via `spring-boot-starter-amqp`
- A durable main queue with dead-letter routing
- JSON message conversion using Jackson
- A simple REST producer endpoint

## Features

- `GET /employee-rabbitmq/producer` publishes employee data to RabbitMQ
- Uses `mainExchange` and routing key `main`
- Sends messages to `main.queue`
- Dead-lettered messages route to `deadLetter.queue`

## Run Locally

From the `jms` directory:

```bash
./mvnw spring-boot:run
```

The application runs on port `8087` by default.

## Example Request

```bash
curl "http://localhost:8087/employee-rabbitmq/producer?empName=Alice&empId=E001&salary=75000"
```

## Configuration

RabbitMQ connection and server settings are configured in `src/main/resources/application.properties`.

