# Beckn Protocol Server

## Introduction

Protocol Server is a service that helps the application connect to ONEST Network. It follows the [Beckn Protocol](https://beckn.network/protocol) and makes it more accessible for the applications to get started quickly. Any network participant can run this server and connect to ONEST Network.

## Features

* Connects a client application with the ONEST network.
* Acts as BAP Adaptor in case of Beckn Application Platform.
* Acts as BPP Adaptor in case of Beckn Provider Platform.
* Validates each request as per the Beckn Network’s Open API schema.
* Generates signatures for the outgoing requests and validates signatures for the incoming requests.
* Stores log for each process.
* Comes with key generation scripts for the Network participants.

## Architecture

There would 2 instances of Protocol Server that is running. One is `Client` facing and the other is `Network` facing.\
\
**In the case of BAP**\
\
`Client` facing Protocol Server manages building the context, validating the request body as per the Standard Beckn Open API schema, listens to the Message Queue, Aggregates the results in the case of Synchronous mode and forwards the results to the client side application as a webhook callback.

`Network` facing Protocol Server manages forwarding the request to the respective Participant or Beckn Gateway (BG). Also it validates the incoming requests from Participants & BG as per the Standard Beckn Open API schema and then validates the signature sent from the clients to ensure the data integrity.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

**In the case of BPP**\
\
`Client` facing Protocol Server listens to the Message Queue and forwards the request to client side application, exposes an endpoint where the client side application can send the results to the network which is again validated against the Standard Beckn Open API schema and pushed to the network facing Protocol Server.

`Network` facing Protocol Server also listens to the Message Queue and forwards the request to the respective Participant or BG. Also it validates the incoming requests from Participants & BG as per the Standard Beckn Open API schema and then validates the signature sent from the clients to ensure the data integrity.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Installation

* Docker version 20.10 or above

### Download

As the Protocol Server repository is Public, clone the repository and checkout to master branch.\
\
[Repository Link](https://github.com/beckn/protocol-server)

```
1. git clone https://github.com/beckn/protocol-server.git
2. git checkout master
3. cd protocol-server
```

### Install

You can utilize Docker to deploy the MongoDB, RabbitMQ and Redis services. We've included an illustrative docker-compose file located in `docker/docker-compose.yaml`.

To set things up effortlessly, run the `setup.sh` command. This command not only copies the Follow file to your home directory but also generates a `docker_data` directory. Within this directory, you'll find the `docker-compose.yaml` file for configuring the aforementioned services.

Additionally, here's a list of files included for your reference:

* `deploy-bap.sh`
* `deploy-bpp.sh`
* `default-bap-client.yml`
* `default-bap-network.yml`
* `default-bpp-client.yml`
* `default-bpp-network.yml`

Feel free to explore and use these resources as needed for your setup.

Please set the user name and password as per requirement in docker-compose.yaml file inside docker\_data directory.

```
bash setup.sh
```

Go to docker\_data directory and run the below command to start redis, rabbit-mq and mongo-db containers.

```
docker-compose up -d
```

### Update Configuration Files which we have copied to home directory

*   In the BAP Client and BAP Network codebases, update the `~/default-bap-client.yml` and `~/default-bap-network.yml` file with the following values:

    * Private Key: Copy the private key of your participant.
    * Public Key: Copy the public key of your participant.
    *   Use the Registry  lookup API to get the `subscriber id`, `subscriber url` and `unique key` .



        ```
        curl --location 'https://sandbox.onest.network/onest/lookup' \
        --header 'Content-Type: application/json' \
        --data '{
            "country": "IND",
            "type":"BAP"
        }'
        ```



    * Subscriber ID: Get using registry lookup API
    * Subscriber URI: Get using registry lookup API
    * Unique Key: Get using registry lookup API
    * Registry URL: `https://sandbox.onest.network/onest`
*   In the BPP Client and BPP Network codebases, update the `~/default-bpp-client.yml` and `~/default-bpp-network.yml` file with the following values:

    * Private Key: Copy the private key of your participant.
    * Public Key: Copy the public key of your participant.
    *   Use the Registry  lookup API to get the `subscriber id`, `subscriber url` and `unique key`.



        ```
        curl --location 'https://sandbox.onest.network/onest/lookup' \
        --header 'Content-Type: application/json' \
        --data '{
            "country": "IND",
            "type":"BPP"
        }'
        ```



    * Subscriber ID: Get using registry lookup API
    * Subscriber URI: Get using registry lookup API
    * Unique Key: Get using registry lookup API
    * Registry URL: `https://sandbox.onest.network/onest`
    * WebhookURL: The endpoint URL of your service the hosts protocol APIs like search, on\_search etc.

### Run

#### Docker Deployment

Execute `~/deploy-bap.sh` file to deploye the the BAP Client and Network.

Execute `~/deploy-bpp.sh` file to deploye the the BPP Client and Network.

#### PM2 Deployment

For PM2 deployment you need to git clone protocol-server four times to setup the BAP Client and Network and BPP Client and Network. Then copy `~/default-bap-client.yml` and `~/default-bap-network.yml` to config directory in respective git clone directory of BAP Client and Network. Also copy `~/default-bpp-client.yml` and `~/default-bpp-network.yml` to config directory in respective git clone directory of BPP Client and Network.

After configuration, Protocol Server can be run as below.

To run the instance in Development Mode (For Debug Purposes):

```
npm run dev
```

To run the instance in Production Mode:

```
npm i -g pm2
pm2 start ecosystem.config.js
```

