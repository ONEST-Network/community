# Steps for Go Live: Seeker Platform

**Summary:**\
This document highlights the steps to be followed by a seeker platform for technical integration on the ONEST network in order to go live with their offerings. The first cohort within the ONEST network will go live with the discovery stage of the transaction\[1]. Thus, post following the steps highlighted in the document, every seeker platform will be able to provide a view to the offerings from the provider platforms within the ONEST network on their platform. For any further steps within a transaction, the consumers will be routed to the respective provider platform.\
\
**Pre-reads:**

ONEST network is an implementation of the [DSEP protocol](https://github.com/beckn/DSEP-Specification), which is based on the [beckn protocol](https://becknprotocol.io/).

* Understand beckn protocol:\
  [https://developers.becknprotocol.io/docs/introduction/video-overview/](https://developers.becknprotocol.io/docs/introduction/video-overview/)
* Understand DSEP Protocol:
  * [https://dsep.sunbird.org/](https://dsep.sunbird.org/)
  * DSEP Tech Overview Videos: [HERE](https://drive.google.com/drive/folders/18mwSy3u-MSj1FpU7i79e39h0x6ylins7?usp=sharing)

**Steps for technical integration:**\
**Step 1:** Identify key use cases and user stories to start with, following an MVP for go-live on the ONEST network

* Example use case: There is an organisation C that needs more number of offerings on their platform for their existing userbase or to attract more users. Such an organisation’s key usecase will be enabling the discoverability of learning and livelihood opportunities offered by provider platforms on ONEST network. Thus, they can join as a seeker platform and make all the offerings of the provider platforms discoverable on their platform.

**Step 2:** Understand the APIs and the structures from the specifications and examples

* Examples are available here: [https://github.com/beckn/DSEP-Specification/tree/master/artefacts](https://github.com/beckn/DSEP-Specification/tree/master/artefacts)

**Step 3:** List down the data points that will be sent as part of the search request

* For example: Let’s take the example of the same organisation as highlighted in step 1. If a user comes to the platform by Organisation C and searches for courses, the user may want to search by grade/ age group of students for whom the course is offered, the duration of the course, the topics covered and so on. These data points that need to be sent to the provider platforms as part of the Search request are listed. This will help the provider platforms respond with the relevant content as part of the on-search response.

**Step 4:** Map the data points against the search API call\
Examples to help with the mapping:

* search for courses:

[https://github.com/beckn/DSEP-Specification/tree/master/artefacts/beckn%20specifications/courses-training/search](https://github.com/beckn/DSEP-Specification/tree/master/artefacts/beckn%20specifications/courses-training/search)

* search for scholarships:

[https://github.com/beckn/DSEP-Specification/tree/master/artefacts/beckn%20specifications/scholarships-grants/search](https://github.com/beckn/DSEP-Specification/tree/master/artefacts/beckn%20specifications/scholarships-grants/search)

**Step 5:** Register in the sandbox registry (https://sandbox.onest.network)

Please refer to **Reference Document** -> **Onboarding Document** after logging in to understand the steps for onboarding in the sandbox.

The sandbox registry URL to be used for lookups is [https://sandbox.onest.network/onest/](https://sandbox.onest.network/onest/)&#x20;

<pre data-title="Example registry lookup that returns the BGs in the network"><code><strong>curl --location --request POST 'https://sandbox.onest.network/onest/lookup' \
</strong>--header 'Content-Type: application/json' \
--data-raw '{
    "country": "IND",
    "type":"BG"
}'
</code></pre>

**Step 6:** Integrate search API via Postman collection

* API call Samples and discovery protocol documentation: [https://dsep.sunbird.org/discovery-protocol-specifications/discovery-protocol](https://dsep.sunbird.org/discovery-protocol-specifications/discovery-protocol)
* Open Source Beckn Adaptor (Protocol Server) [https://github.com/beckn/protocol-server](https://github.com/beckn/protocol-server)
* If you are facing any issues, please share your query on [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)
* Beckn Protocol Server is a service that helps the application connect to Beckn Network: Protocol server codebase: [https://github.com/beckn/protocol-server/tree/master](https://github.com/beckn/protocol-server/tree/master)
* Documentation on protocol server: [https://github.com/beckn/protocol-server/wiki](https://github.com/beckn/protocol-server/wiki)

**Step 7:** Test with reference BPPs (provider platforms) on the sandbox

* The postman collections for testing with reference apps are here: [https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json](https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json)
* Hosted versions of the provider platform (BPP) and Seeker platform (BAP) can be used to test the implementations. Please find the links below:
  * Provider platform (BPP): [https://fs-ps-bpp-network.onest.network/](https://fs-ps-bap-network.onest.network/)
  * Seeker Application (BAP): [https://fs-ps-bap-network.onest.network/](https://fs-ps-bap-network.onest.network/)
* Link to Sandbox: [https://github.com/beckn/beckn-sandbox/tree/main/artefacts](https://github.com/beckn/beckn-sandbox/tree/main/artefacts)

**Step 8:** Demo the end-to-end flow

**​​Step 9:** Implement signatures and validation as per spec.

* sample code on generation of keys, signing and verification:

[https://github.com/beckn-on-succinct/beckn-sdk-java/blob/master/src/test/java/in/succinct/beckn/SampleUseCase.java](https://github.com/beckn-on-succinct/beckn-sdk-java/blob/master/src/test/java/in/succinct/beckn/SampleUseCase.java)

* Beckn Registry Documentation:

[https://beckn-registry.readthedocs.io/en/latest/index.html](https://beckn-registry.readthedocs.io/en/latest/index.html)

* Codes to be used for generating a pair of private key, public keys:

[https://registry.becknprotocol.io/crypto\_keys/generate/ed25519:256](https://registry.becknprotocol.io/crypto\_keys/generate/ed25519:256)

[https://registry.becknprotocol.io/crypto\_keys/generate/x25519:256](https://registry.becknprotocol.io/crypto\_keys/generate/x25519:256)

1. Discovery, Trust & Transact are the three stages of an end-to-end transaction ↑
