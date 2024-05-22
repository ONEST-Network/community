# NP Go-Live Check List

1. **Use Case identification & finalization**
   1. Understanding ONEST and going through the resources.
      1. [beckn-protocol-video-library](learn/beckn-protocol-video-library/ "mention")
      2. [getting-started-on-dsep-video-library](learn/getting-started-on-dsep-video-library/ "mention")
   2. Identification of role - Seeker or Provider
   3. Identification of use case - includes domain
   4. Finalizing use case with EkStep team (including test cases)
   5. Run through the test cases for feasibility analysis
   6. Identify Tech resources & capabilities
2. **ONEST Implementation**
   1. [Register](onboarding-sandbox-registration/) on the sandbox environment
   2. Setup BAP or BPP servers (using [protocol server](learn/integration-of-adaptors/beckn-protocol-server/))
   3. Setup [Proxy Servers](learn/integration-of-adaptors/beckn-protocol-server/local-tunnelling-and-nginx-setup.md)
   4. Expose the API Service with a domain name
3. **API integration**
   1. [Understand the APIs](learn/understanding-the-apis.md)
   2. Go through [implementation guides](learn/reference-implementation-guides/) and understand the flows, schemas etc
   3. Mapping relevant APIs to the process flow
   4. Mapping Schema fields with internal fields
   5. Implementing Search, Select, Init, Confirm & Status APIs
4. **Testing**
   1. Test with seeker/provider platforms with mock server ([postman collection](https://github.com/ONEST-Network/ONEST-Specification/blob/main/docs/postman\_collection/sandbox-sample-collection.json))&#x20;
   2. Get the test results and JSON files validated from tech team
   3. Run functional test cases
5. **UI & Pre-production**
   1. Create wireframes/UI design for the application
   2. Developing the UI layer
   3. Integrate the APIs with the UI
   4. Register on pre-prod environment
   5. Test the application with another seeker/provider side app on the pre-prod environment
   6. Login Functionality
   7. Profile modification/update
   8. Tracking functionality for the user-status of the use-case
6. **Compliance & Legal check**
   1. Get the Application tested for security measures
   2. Abide by the network policies and sign the agreement
   3. Get in agreement with Ekstep team regarding the tech implementation and integration
   4. Verify the business use case and functionality as per what was decided earlier
   5. Request to get onboarded on the Production environment
7. **Production ready & Go Live**
   1. Publish a weekly update on the status and feedback
   2. Regularly update the policies and abide by them
   3. Provide a support mechanism for the app/platform
8. **Tracking and monitoring of applications**
   1. Show current application status against an application ID (under process, reviewed, disbursed, etc)
   2. Any status update to be communicated/flagged to individual applicants via SMS. Standard SMS templates to be configured
   3. To give feature to view all applications, download data, perform actions on it, etc
9. [network-observability](network-observability/ "mention")
   1. Generate telemetry for all the protocol APIs (Search, On\_Search, Select, On\_select, Init, On\_Init, Confirm, On\_Confirm, Status, On\_status).
