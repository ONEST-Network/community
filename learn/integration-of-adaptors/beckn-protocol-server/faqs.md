# FAQs

* What is webhook URL in config?

&#x20;**Ans:** It is the endpoint of BAP/BPP internal System API (POST), to which protocol server will send the API payload.&#x20;

* Does the protocol server append the API action as a path to the webhook URL when it invokes the same?

**Ans:** No

* What should be done if a participant want to be on multiple domains (learning-experiences / work-opportunities / financial-support / expert-connect) and/or multiple roles (seeker/provider)?

**Ans:** A Protocol Server with same role will work for multiple domains. Register with same participant ID in required domains and use the same in protocol server configuration.&#x20;

* How does network server and client server connects together?

**Ans:** Network and client server communicates through RabbitMQ.

* Can we use other than default ports for Network and Client server?

**Ans:** Yes, can be changed in the default.yml file.
