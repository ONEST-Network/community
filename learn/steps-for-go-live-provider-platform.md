# Steps for Go Live: Provider Platform

### **Summary:**

This document highlights the steps to be followed by a provider platform for technical integration on the ONEST network in order to go live with their offerings. The first cohort within the ONEST network will go live with the discovery stage of the transaction. Discovery, Trust & Transact (Select, Order, Confirm, Fulfill, Post-fulfilment) are the three stages of an end-to-end transaction. Thus, post following the steps highlighted in the document, every provider platform will be able to make their offerings discoverable across seeker platforms present within the ONEST network. For any further steps within a transaction, the consumers will be routed to the respective provider platform.

### **Pre-reads:**

ONEST network is an implementation of the [DSEP protocol](https://github.com/beckn/DSEP-Specification), which is based on the [beckn protocol](https://becknprotocol.io/).

* Understand Beckn protocol: [https://developers.becknprotocol.io/docs/introduction/video-overview/](https://developers.becknprotocol.io/docs/introduction/video-overview/)&#x20;
* Understand the DSEP Protocol: [DSEP Tech Overview Videos Playlist](https://drive.google.com/drive/folders/18mwSy3u-MSj1FpU7i79e39h0x6ylins7)

***

### **Steps for technical integration:**

Before you begin, please ensure that you have filled out the "Join Us" form linked [HERE](https://onest.network/join-us) so that a person from our team can be in touch with you to support your integration journey.&#x20;

**Step 1:** Identify key use cases and user stories to start with, following an MVP for go-live on the ONEST network

* Example use case: There is an organisation A that creates a diverse range of educational content that is helping simplify K-12 education for students from all backgrounds. They upload this content on their own platform. Another organisation or individual looking for K-12 educational content need to find out about organisation A, visit their platform and search for the content based on the name, grade, subject and so on. But organisation A need more organisations and individuals to make use of this content. Thus, their key use case will be the discovery of educational courses hosted on their platform across all the seeker platforms on the ONEST network.

**Step 2:** Understand the APIs and the structures from the specifications and examples

* (Latest) [https://github.com/beckn/DSEP-Specification/tree/draft/examples](https://github.com/beckn/DSEP-Specification/tree/draft/examples)
* (Published earlier) [https://github.com/beckn/DSEP-Specification/tree/master/artefacts](https://github.com/beckn/DSEP-Specification/tree/master/artefacts)

***

**Step 3:** List down the data points that need to be shared as a response to a search request

* For example: Let’s take the example of the same organisation as highlighted in step 1. If there is a search request for a 9th grade math lesson from a seeker platform on the network. The organisation might want to respond back with the name of the course available with them pertaining to that lesson, the link to the course, an image/ thumbnail visually representing it and the name of the instructor or the organisation.

**Step 4:** Map the data points against the on\_search API call. Examples to help with the mapping are [available here](https://github.com/beckn/DSEP-Specification/tree/draft/examples).

***

**Step 5:** Register in the sandbox (https://sandbox.onest.network)

**Step 6:** Integrate On\_search API via Postman collection

* API call Samples and discovery protocol documentation: [https://dsep.sunbird.org/discovery-protocol-specifications/discovery-protocol](https://dsep.sunbird.org/discovery-protocol-specifications/discovery-protocol)
* DSEP Specification: [https://github.com/beckn/DSEP-Specification/tree/master/artefacts](https://github.com/beckn/DSEP-Specification/tree/master/artefacts)
* Open Source Beckn Adaptor (Protocol Server) [https://github.com/beckn/protocol-server](https://github.com/beckn/protocol-server)
* If you are facing any issues, please share your query on [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)
* Beckn Protocol Server is a service that helps the application connect to Beckn Network: Protocol server codebase: [https://github.com/beckn/protocol-server/tree/master](https://github.com/beckn/protocol-server/tree/master)
* Documentation on protocol server: [https://github.com/beckn/protocol-server/wiki](https://github.com/beckn/protocol-server/wiki)

**Step 7:** Test with reference seeker platforms (BAPs) on the sandbox

* The postman collections for testing with reference apps are here: [https://raw.githubusercontent.com/beckn/beckn-sandbox/main/artefacts/DSEP-PS-sandbox.postman\_collection.json](https://raw.githubusercontent.com/beckn/beckn-sandbox/main/artefacts/DSEP-PS-sandbox.postman\_collection.json)
* Hosted versions of the provider platform (BPP) and Seeker platform (BAP) can be used to test the implementations. Link for the hosted version for a Provider platform (BPP): [https://sandbox-bpp-network.becknprotocol.io](https://sandbox-bpp-network.becknprotocol.io/)
* Hosted version for a Seeker Application (BAP):[https://ps-bap-network.becknprotocol.io](https://ps-bap-network.becknprotocol.io/)
* Link to Sandbox: [https://github.com/beckn/beckn-sandbox/tree/main/artefacts](https://github.com/beckn/beckn-sandbox/tree/main/artefacts)

**Step 8:** Demo the end-to-end flow

**​​Step 9:** Implement signatures and validation as per spec.

* Guide to integrating to Beckn Gateway:

[https://github.com/sanjay95/BECKN-Integration-to-Gateway](https://github.com/sanjay95/BECKN-Integration-to-Gateway)

* sample code on generation of keys, signing and verification:

[https://github.com/beckn-on-succinct/beckn-sdk-java/blob/master/src/test/java/in/succinct/beckn/SampleUseCase.java](https://github.com/beckn-on-succinct/beckn-sdk-java/blob/master/src/test/java/in/succinct/beckn/SampleUseCase.java)

* Beckn Registry Documentation:

[https://beckn-registry.readthedocs.io/en/latest/index.html](https://beckn-registry.readthedocs.io/en/latest/index.html)

* Codes to be used for generating a pair of private key, public keys:
  * [https://registry.becknprotocol.io/crypto\_keys/generate/ed25519:256](https://registry.becknprotocol.io/crypto\_keys/generate/ed25519:256)
  * [https://registry.becknprotocol.io/crypto\_keys/generate/x25519:256](https://registry.becknprotocol.io/crypto\_keys/generate/x25519:256)
