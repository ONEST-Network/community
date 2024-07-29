# FAQs



<details>

<summary>Is it required to use Protocol Server as a network adaptor?</summary>

No, network participants can develop and use their own network adaptor as well.

</details>

<details>

<summary>Can i make customization in the protocol server?</summary>

Yes, customizations are allowed. As protocol server is a reference implementation and open source adaptors, features can be contributed.

</details>

<details>

<summary>can i deploy protocol server other than in docker?</summary>

&#x20; Protocol server can be deployed as PM2 deployment as well.

</details>

<details>

<summary>Can i use existing redis, mongodb, rabbitmq servers?</summary>

Yes, existing redis, mongodb, rabbitmq servers can be used.

</details>

<details>

<summary>default-bap-client.yml, default-bap-network.yml, default-bpp-client.yml, default-bpp-network.yml should be inside or outside the protocol server folder?</summary>

configuration files should be outside the protocol server folder.

</details>

<details>

<summary>How do we install the provider side of the protocol server?</summary>

In default-bap-client.yml and default-bpp-client.yml, set app.mode: BPP

</details>

<details>

<summary>How do we install the seeker side of the protocol server?</summary>

In default-bap-client.yml and default-bpp-client.yml, set app.mode: BAP

</details>

<details>

<summary>can i run the protocol server on some context path instead of base path "/"?</summary>

In deploy-bap.sh and deploy-bpp.sh, change the $HOME to the required context path and run the scripts.

</details>

<details>

<summary>What are the default ports for BAP client and network servers?</summary>

5001 and 5002

</details>

<details>

<summary>What are the default ports for BPP client and network servers?</summary>

6001 and 6002

</details>

<details>

<summary>Can i use other than default ports for Network and Client server?</summary>

Yes, can be changed in the default.yml file.

</details>

<details>

<summary>Do we need to expose both network and client server ip with a domain name?</summary>

Only network server IP should be exposed with a domain name, as it receives the requests.

</details>

<details>

<summary>How to connect the Protocol server to the Provider system?</summary>

In default-bap-client.yml, set the provider system end point as webhook url.

</details>

<details>

<summary>What is webhook URL in config?</summary>

It is the endpoint of BAP/BPP internal System API (POST), to which protocol server will send the API payload.&#x20;

</details>

<details>

<summary>Does the protocol server append the API action as a path to the webhook URL when it invokes the same?</summary>

No, action is available as part of the context object.

</details>

<details>

<summary>What should be done if a participant want to be on multiple domains (learning-experiences / work-opportunities / financial-support / expert-connect) and/or multiple roles (seeker/provider)?</summary>

Protocol Server with same role will work for multiple domains. Register with same participant ID in required domains and use the same in protocol server configuration.&#x20;

</details>

<details>

<summary>How does network server and client server connects together?</summary>

Network and client server communicates through RabbitMQ.

</details>

<details>

<summary>How to generate public and private keys?</summary>

Protocol server provides a script to generate the keys. Go to the protocol server folder and execute this command: npm run generate-keys.

</details>

<details>

<summary>How to get the subscriber id and url?</summary>

Using the registry lookup API, users can fetch the participant details, which includes the subscriber id and url.

</details>

<details>

<summary>Based on what criteria does the protocol server caches the request?</summary>

protocol server caches only the search requests based on msg id. If a search request with the same msg id is made a second time, the response is returned from the cache.

</details>

<details>

<summary>What kind of schema validation does the protocol server will do?</summary>

below are the validations done by protocol server:

1\. for the context object, it checks for schema (well-formedness) , mandatory fields, data types (incase if the field is populated) as per schema

2\. for message object, it only checks for the schema (well-formedness) and data types (incase if the field is populated).

</details>

