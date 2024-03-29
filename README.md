# Backend developer: python code challenge
The purpose of this coding challenge is to see your coding style and level.
We are a small team, and we need developers/architects who can write and understand code.
Please don't feel intimidated if you don't know Kafka. You only need to be able to use Kafka, not be an expert.

You must write the code yourself, and you will be asked to explain it. 

## API-routes
Use python (3.6 or later) and a web-framework (we recommend flask, but you are free to choose whatever framework you like) to write a REST-API.
The API should handle the following two routes:

1. GET to `/` should return "OK"
2. POST to `/kafka` should receive a JSON payload (see example below). It must check that *username* is in the payload and that *username* is a string. Then it should publish a [kafka message](#kafka-message)

**Example, valid JSON-payload, notice that no other field than username is required**:

```json
{
  "username": "Espen",
  "age": 27,
  "company": "wheel.me",
  "code_level": "wannabe"
}
```

**Example invalid json payload (username missing)**
```json
{
  "first_name": "espen"
}
```

**Example invalid json payload (username is not a string)**
```json
{
  "username": 23,
  "company": "wheel.me"
}
```

### Kafka message
The Kafka message should have:
1. A key that is the username of the payload.
2. A value that is all the other fields of the payload.
3. The value should also contain a *timestamp* field which should be the timestamp when receiving the message

## Other requirements
1. The API should be runnable with docker-compose.
2. Kafka should run as a service with docker-compose.

Extra credits if:

1. Your code use type hints.
2. You write unit tests
3. You write an integration test
4. You create a readme.md or equivalent.
5. Your `kafka-topic` name is configurable by an environment variable
6. Your code is beautifully formatted

## Hints
* Checkout `landoop/fast-data-dev:cp3.3.0` for running kafka with docker.
* Checkout [confluent-kafka-python](https://github.com/confluentinc/confluent-kafka-python) for a python client for kafka

## Submission alternatives
1. Create a repository on Github and send us the link
2. Zip the project files and send them over email

