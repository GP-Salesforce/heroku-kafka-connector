# heroku-kafka-connector
This repo serves as an example of how you can run Kafka Connect on Heroku Dynos. This Example is tested on Heroku Prviate Space and uses Heroku Kafka Private Standard 0 Plan and a Confluent Kafka Connector.

## Architecture 
- Heroku Dyno
- Heroku Kafka
- Confluent Kafka Connector

## Setup
1. Create an Heroku App
2. Setup a Heroku Kafka addon
3. Add a key-value on Config Vars at Heroku App
   - ```TRUSTSTORE_PASSWORD``` : Set a Truststore Password
   - ```KEYSTORE_PASSWORD``` : Set a Keystore Password
5. Add these Buildpacks
   - ```https://github.com/amiel/heroku-buildpack-apt#feature/support-adding-keys```
   - ```heroku/jvm```
6. Download the kafka connect jdbc jar from	[here](https://www.confluent.io/hub/confluentinc/kafka-connect-jdbc) and put it in your folder. It's not recommended to deploy a jar directly, so beware.
7. Deploy to your heroku app

## How does the code work
The Heroku Apt Buildpack installs the confluent kafka connector and the certs are made from the config vars. The ```start-distributed```is used to start the connector with the configs in it.
