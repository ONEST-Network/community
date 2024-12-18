# Financial support, Skilling (DSEP 1.0)

Following are the APIs to be developed by BAP and BPP for the above two domains

**BAP**

BAP should consume the following on\_action APIs and trigger action APIs.

* on\_search API
* on\_select API
* on\_init API
* on\_confirm
* on\_status
* on\_update
* on\_rating
* on\_support

#### BPP

BPP should consume the following action APIs and trigger on\_action APIs.

* search API
* select API
* init API
* confirm
* status
* update
* rating
* support

### Steps to create a Request:

<figure><img src="../../.gitbook/assets/onest api flow.jpeg" alt=""><figcaption></figcaption></figure>

1. All the action and on\_action APIs have `context` and `message` objects. Refer to this [link](https://developers.becknprotocol.io/docs/core-specification/schema-reference/context/) to understand the list of properties in the context object.\
   \
   Message object varies based on the API, refer [reference-implementation-guides](../reference-implementation-guides/ "mention") for examples. Below is the sample API request with context and message objects.

```
{
  "context": {
    "domain": "ONDC:ONEST11",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "search",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "ttl": "PT10M"
  },
  "message": {
    "intent": {
      "item": {
        "descriptor": {
          "name": "english"
        }
      }
    }
  }
}
```

2. Participant should sign the payload and send to gateway. [Steps](https://github.com/beckn/protocol-specifications/blob/master/docs/BECKN-006-Signing-Beckn-APIs-In-HTTP-Draft-01.md) to sign the request payload and verify when a payload received.
3. [Error codes](https://github.com/beckn/protocol-specifications/blob/master/docs/BECKN-005-Error-Codes-Draft-01.md) implementation by BAP and BPP.
4. Only search API goes through gateway, rest all APIs are between BAP and BPP.\
   Example: BAP sends search API to gateway, and it will broadcast to all available providers in that domain. Next, BPP will make on\_search API directly to BAP.

### **Note:**

[beckn-protocol-server](../integration-of-adaptors/beckn-protocol-server/ "mention") is a reference application, which helps the participants to quickly develop the protocol APIs. It will help in signing and verification of payload signature, schema validation, sending and receiving requests to Gateway and Participants.

It is not mandatory to use the protocol server; you can build your own network adaptors to connect to the ONEST network.

[Sample code](https://github.com/beckn-on-succinct/beckn-sdk-java/blob/master/src/test/java/in/succinct/beckn/SampleUseCase.java) for implementing signature and verification.

### Registry Lookup API

The registry lookup API can be used to get the details of all the participants in the registry. In request body, `type` can be `BG`,`BAP`, `BPP`

```url
curl --location 'https://staging.registry.ondc.org/lookup' \
--header 'Content-Type: application/json' \
--data '{
    "country": "IND",
    "type":"BPP"
}'
```

[https://staging.registry.ondc.org/lookup\
\
](https://staging.registry.ondc.org/lookup)[https://staging.registry.ondc.org/vlookup\
\
](https://staging.registry.ondc.org/vlookup)

### Gateway URL

```url
https://staging.gateway.proteantech.in/search
```
