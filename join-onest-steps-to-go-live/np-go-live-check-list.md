# NP Go-Live Check List

1. **Use Case identification & finalization**
   1. Understanding ONEST and going through the resources
   2. Identification of role - Seeker or Provider
   3. Identification of use case - includes domain
   4. Finalizing use case with EkStep team (including test cases)
   5. Run through the test cases for feasibility analysis
   6. Identify Tech resources & capabilities
2. **ONEST Implementation**
   1. Register on the sandbox environment
   2. Setup BAP or BPP servers (using beckn protocol server)
   3. Setup Proxy Servers
   4. Expose the API Service with a domain name
3. **API integration**
   1. Mapping relevant APIs to the process flow
   2. Understanding and mapping Schema fields with internal fields
   3. Implementing Search, Select, Init, Confirm & Status APIs
4. **Testing**
   1. Test with seeker/provider Mock Apps
   2. Get the test results and JSON files validated from tech team
   3. Run functional test cases
5. **UI & Pre-production**
   1. Create wireframes/UI design for the application
   2. Developing the UI layer
   3. Integrate the APIs with the UI
   4. Register on preprod environment
   5. Test the application with another seeker/provider side app on the preprod environment
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
9. **Master data for SKU criteria matching with user profile data**
   1. Location - Finalize master data - location - e.g. geotags for states ad cities, state codes, etc
   2. Social identity-Finalize master data - social status
   3. Professional Status of user or of parents (in case of minor)- Finalize master data - professional status
   4. Gender-Finalize gender master data
   5. Age-Finalize age master data
10. **Network Observability**
    1. Generate telemetry for all the protocol APIs (Search, On\_Search, Select, On\_select, Init, On\_Init, Confirm, On\_Confirm, Status, On\_status).
11. **Protocol**
    1. Current version of protocol
