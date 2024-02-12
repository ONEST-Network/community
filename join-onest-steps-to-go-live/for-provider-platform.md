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

# For Provider Platform

This document highlights the steps to be followed by a provider platform for technical integration on the ONEST network in order to go live with their offerings. \
\
Discovery, Order, Fulfilment, Post-fulfilment are the four stages  in an order lifecycle. Thus, post following the steps highlighted in the document, every provider platform will be able to make their offerings discoverable across seeker platforms present within the ONEST network. For any further steps within a transaction, the consumers will be routed to the respective provider platform.

### **Prerequisites:**

* [ ] Watched all the videos from [open-source-beckn-protocol-server](../learn/integration-of-adaptors/open-source-beckn-protocol-server/ "mention")
* [ ] Watched all the videos from [getting-started-on-dsep-video-library](../learn/getting-started-on-dsep-video-library/ "mention")
* [ ] Read [understanding-the-apis.md](../learn/understanding-the-apis.md "mention")
* [ ] Your technical team must have a DevOps Engineer and a Developer
* [ ] [Broken link](broken-reference "mention")

### **Steps for technical integration:**

Before you begin, please ensure that you have filled out the "Join Us" form linked [HERE](https://onest.network/join-us) so that a person from our team can be in touch with you to support your integration journey.&#x20;

**Step 1:** Identify key use cases and user stories to start with, following an MVP for go-live on the ONEST network

* Example use case: There is an organisation A that creates a diverse range of educational content that is helping simplify K-12 education for students from all backgrounds. They upload this content on their own platform. Another organisation or individual looking for K-12 educational content need to find out about organisation A, visit their platform and search for the content based on the name, grade, subject and so on. But organisation A need more organisations and individuals to make use of this content. Thus, their key use case will be the discovery of educational courses hosted on their platform across all the seeker platforms on the ONEST network.

**Step 2:** [onboarding-sandbox-registration](../onboarding-sandbox-registration/ "mention")

**Step 3:** Refer [reference-implementation-guides](../learn/reference-implementation-guides/ "mention") and understand the APIs schema from the  specifications and examples.

* (Latest) [https://github.com/beckn/DSEP-Specification/tree/draft/examples](https://github.com/beckn/DSEP-Specification/tree/draft/examples)

**Step 4:** Read [developing-the-apis.md](../learn/developing-the-apis.md "mention")

* Beckn protocol Server is an open-source service that helps applications connect to any network that is using beckn protocol including ONEST. It follows the beckn protocol and makes it easier for the applications to get started with ONEST implementation. Routing, request signing, schema and signature validation etc is done by this service. More details about the open-source package can be found here: [open-source-beckn-protocol-server](../learn/integration-of-adaptors/open-source-beckn-protocol-server/ "mention")&#x20;
* Network participants can use Beckn Protocol Server - the open-source service or develop it themselves or avail a TSP.

**Step 5:** Refer [network-observability](../network-observability/ "mention")to generate telemetry and send to the ONEST network

**Step 6:** Test with reference seeker platform (BAP) on the sandbox. The following is the [postman collection](https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json)

**Step 7:** Share the logs [here](https://github.com/ONEST-Network/verification-logs) by following these [steps](https://github.com/ONEST-Network/verification-logs/blob/main/README.md) and get sign-off by ONEST Team

**Step 8:**  Reach out to the ONEST team to [register](https://prod.onest.network/login) onto to Production to Go Live

**Support:** If you are facing any issues, please share your query on [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)
