# Chapter 4: DSEP Specification and Network Architecture

{% embed url="https://drive.google.com/file/d/1Agc6waBaNZrsnPFb144efV1A74zcR_GJ/view?usp=drive_link" %}

1. DSEP contains a layered architecture of - Network Actors, APIs, DSEP Schema, Communication Protocol and Sector-specific Tags
2. Network Actors include - Beckn Application Platform (BAP), Beckn Provider Platform (BPP), DSEP Gateway and DSEP Registry
3. Actors and their roles
   * BAP is a consumer-focused experience with a "super-charged browser", and interfaces with BPP eg. Aggregator apps, Super Apps, Standalone platforms like LinkedIn, Unacademy, Monster.com and Udemy etc.; End-consumer facing Chatbots like Telegram, WhatsApp or IVRS, Blogs or consumer-focused software utilities such as marketing widgets, browser extensions etc.
   * BPPs is a provider-focused experience and hence, acquire education and skill development service providers as users. A BPP maintains an active inventory, provides rich, service-focused experience, interfaced with BAP and Gateways via DSEP API to publish a catalog of providers, machine-readable terms of service, receive bookings for products and services, provide status updates regarding fulfillment . Eg of BPP are backends of platforms such as UDEMY, Coursera, Enterprise Backends of Education and Skill Development Enterprise Service-provider-facing chatbots like Telegram Bot and WhatsApp bots.
   * DSEP Gateway is a part of DSEP network infrastructure and it interfaces with the BAP and BPPs to enable discovery of BPPs by BAPs and to broadcast search requests. Providers an equal opportunity for BPPs to be discovered and respond.
   * DSEP Registry – Allows permissioned onboarding of platforms on the DSEP network through a certification and compliance process. Interfaces with consumer Applications  (BAPs) Provider platforms and gateways – which is help authenticated lookup of trusted platforms on the network, store public keys for digital signing and verification of transactions between network participants and allows broadcast optimization by allowing network-level filtering by industry sector, country and city.



<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
