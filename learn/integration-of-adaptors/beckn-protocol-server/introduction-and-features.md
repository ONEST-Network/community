# Introduction & Features

Protocol Server is a service that helps the application connect to ONEST Network. It follows the [Beckn Protocol](https://beckn.network/protocol) and makes it more accessible for the applications to get started quickly. Any network participant can run this server and connect to ONEST Network.

## Features

* Connects a client application with the ONEST network.
* Acts as BAP Adaptor in case of Beckn Application Platform.
* Acts as BPP Adaptor in case of Beckn Provider Platform.
* Validates each request as per the Beckn Network’s Open API schema.
* Generates signatures for the outgoing requests and validates signatures for the incoming requests.
* Stores log for each process.
* Comes with key generation scripts for the Network participants.

### Note

[Protocol Server](https://starterpack.onest.network/learn/integration-of-adaptors/beckn-protocol-server) is a reference implementation of a network adaptor. It is not mandatory to use the protocol server. you can build your own network adaptor to connect to the ONEST network.
