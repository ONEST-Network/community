---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Steps for Go Live: Provider Platform

### **Summary:**

This document highlights the steps to be followed by a provider platform for technical integration on the ONEST network in order to go live with their offerings. \
\
Discovery, Trust & Transact (Select, Order, Confirm, Fulfill, Post-fulfilment) are the three stages of an end-to-end transaction. Thus, post following the steps highlighted in the document, every provider platform will be able to make their offerings discoverable across seeker platforms present within the ONEST network. For any further steps within a transaction, the consumers will be routed to the respective provider platform.

### **Pre-reads:**

[understanding-the-apis.md](understanding-the-apis.md "mention")

***

### **Steps for technical integration:**

Before you begin, please ensure that you have filled out the "Join Us" form linked [HERE](https://onest.network/join-us) so that a person from our team can be in touch with you to support your integration journey.&#x20;

**Step 1:** Identify key use cases and user stories to start with, following an MVP for go-live on the ONEST network

* Example use case: There is an organisation A that creates a diverse range of educational content that is helping simplify K-12 education for students from all backgrounds. They upload this content on their own platform. Another organisation or individual looking for K-12 educational content need to find out about organisation A, visit their platform and search for the content based on the name, grade, subject and so on. But organisation A need more organisations and individuals to make use of this content. Thus, their key use case will be the discovery of educational courses hosted on their platform across all the seeker platforms on the ONEST network.

**Step 2:** [onboarding.md](onboarding.md "mention")

**Step 3:** Refer [reference-implementation-guides](reference-implementation-guides/ "mention") and understand the APIs schema from the  specifications and examples.

* (Latest) [https://github.com/beckn/DSEP-Specification/tree/draft/examples](https://github.com/beckn/DSEP-Specification/tree/draft/examples)

**Step 4:** [developing-the-apis.md](developing-the-apis.md "mention")

* Beckn Protocol Server is a service that helps the application connect to ONEST Network. It follows the [Beckn Protocol](https://beckn.network/protocol) and makes it more accessible for the applications to get started with ONEST implementation. Any network participant can run this server and connect to ONEST Network: [beckn-protocol-server.md](integration-of-open-source-adaptors/beckn-protocol-server.md "mention")

**Step 5:** Test with reference seeker platforms (BAPs) on the sandbox

* The postman collections for testing with reference apps are here: [https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json](https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json)
* Hosted versions of the provider platform (BPP) and Seeker platform (BAP) can be used to test the implementations. Please find the links below:
  * Provider platform (BPP): [https://fs-ps-bpp-network.onest.network/](https://fs-ps-bap-network.onest.network/)
  * Seeker Application (BAP): [https://fs-ps-bap-network.onest.network/](https://fs-ps-bap-network.onest.network/)

**Step 6:** Demo the end-to-end flow to ONEST and get sandbox sign-off.

**Step 7:**  Register onto to Production [ONEST Registry](https://prod.onest.network/) and Go Live !!!

**Support:** If you are facing any issues, please share your query on [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)
