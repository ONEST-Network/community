# Installation

### Pre-requisites

* Docker version 20.10 or above ([setup guide](https://docs.docker.com/desktop/))

### Infra Requirements:

2 CPU, 8GB RAM - Ubuntu&#x20;

### Installation

1. Go to the root path (`~/`) in your system and clone this [repository](https://github.com/ONEST-Network/protocol-server).

```sh
git clone https://github.com/ONEST-Network/protocol-server.git
cd protocol-server
git checkout master
```

2. Run below command to configuration, docker, shell scripts files to root(\`\~/\`) path. Following are the   file that will be copied: `deploy-bap.sh, deploy-bpp.sh, default-bap-client.yml, default-bap-network.yml, default-bpp-client.yml, default-bpp-network.yml, docker_data/docker_compose.yaml`

```sh
bash setup.sh
```

3. Go to docker\_data directory and run docker command.

```sh
cd ~/docker_data
docker-compose up -d
```

4\. Update the client and network server configuration by following below setups:&#x20;

**For BAP:**

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

&#x20; **For BPP:**

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
    * Webhook URL: The endpoint URL of your service the hosts protocol APIs like search, on\_search etc.

5. After making the changes in configuration files, run the below commands to create bap/bpp client and network docker containers:       &#x20;

* Execute `~/deploy-bap.sh` file to deploy the BAP Client and Network.
* Execute `~/deploy-bpp.sh` file to deploy the BPP Client and Network.

#### For PM2 Deployment

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

