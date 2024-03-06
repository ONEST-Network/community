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

# For Seeker Platform

This document highlights the steps to be followed by a provider platform for technical integration on the ONEST network in order to go live with their offerings. \
\
Discovery, Order, Fulfilment, Post-fulfilment are the four stages  in an order lifecycle. Thus, post following the steps highlighted in the document, every provider platform will be able to make their offerings discoverable across seeker platforms present within the ONEST network. For any further steps within a transaction, the consumers will be routed to the respective provider platform.

### **Prerequisites**&#x20;

* [ ] Watched all the videos from [beckn-protocol-server](../learn/integration-of-adaptors/beckn-protocol-server/ "mention")
* [ ] Watched all the videos from [getting-started-on-dsep-video-library](../learn/getting-started-on-dsep-video-library/ "mention")
* [ ] Read [understanding-the-apis.md](../learn/understanding-the-apis.md "mention")
* [ ] Your technical team must have a DevOps Engineer, a Developer and UI Engineer&#x20;
* [ ] [Broken link](broken-reference "mention")

***

### **Steps for technical integration:**

Before you begin, please ensure that you have filled out the "Join Us" form linked [HERE](https://onest.network/join-us) so that a person from our team can be in touch with you to support your integration journey.&#x20;

**Step 1:** Identify key use cases and user stories to start with, following an MVP for go-live on the ONEST network.

* Example use case: There is an organisation C that needs more number of offerings on their platform for their existing userbase or to attract more users. Such an organisation’s key usecase will be enabling the discoverability of learning and livelihood opportunities offered by provider platforms on ONEST network. Thus, they can join as a seeker platform and make all the offerings of the provider platforms discoverable on their platform.

**Step 2:** [onboarding-sandbox-registration](../onboarding-sandbox-registration/ "mention")

**Step 3:** Refer [onest-specifications](../learn/onest-specifications/ "mention") and understand the APIs schema from the  specifications and examples.

* (Latest) [https://github.com/beckn/DSEP-Specification/tree/draft/examples](https://github.com/beckn/DSEP-Specification/tree/draft/examples)

**Step 3:** List down the data points that will be sent as part of the search request

* For example: Let’s take the example of the same organisation as highlighted in step 1. If a user comes to the platform by Organisation C and searches for courses, the user may want to search by grade/ age group of students for whom the course is offered, the duration of the course, the topics covered and so on. These data points that need to be sent to the provider platforms as part of the Search request are listed. This will help the provider platforms respond with the relevant content as part of the on-search response.

**Step 4:** Read [developing-the-apis.md](../learn/developing-the-apis.md "mention")

* Beckn Protocol Server is an open-source service that helps applications connect to any network that is using Beckn Protocol including ONEST. It follows the Beckn protocol and makes it easier for the applications to get started with ONEST implementation. Routing, request signing, schema and signature validation etc is done by this service. More details about the open-source package can be found here: [beckn-protocol-server](../learn/integration-of-adaptors/beckn-protocol-server/ "mention")&#x20;
* Network participants can use EITHER the Beckn Protocol Server - the open-source service or develop it themselves or avail a TSP.

**Step 5:** Refer [network-observability](../network-observability/ "mention")to generate telemetry and send to the ONEST network.

**Step 6:** Test with reference BPP (provider platform) on the sandbox. The following is the [postman collection](https://raw.githubusercontent.com/beckn/DSEP-Specification/draft/examples/postman-collection/sandbox-sample-collection.json)

**Step 7:** Share the logs [here](https://github.com/ONEST-Network/verification-logs) by following these [steps](https://github.com/ONEST-Network/verification-logs/blob/main/README.md) and get sign-off by ONEST Team

**Step 8:**  Reach out to the ONEST team to [register](https://prod.onest.network/login) onto to Production to Go Live

**Support:** If you are facing any issues, please share your query on [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)
