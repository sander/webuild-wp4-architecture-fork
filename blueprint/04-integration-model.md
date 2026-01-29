# 4. Interaction & Integration Model

## 4.1 Integration Principles
Modularity, standardization, versioning.

## 4.2 High-Level Flows
- Credential issuance
- Presentation & verification
- Revocation and status checking

### 4.2.1 General PID issuing process
This chapter describes the general PID issuing process in a sequence diagram.

<strong>Description</strong>
1) The user installs the app from a trusted and official app store
2) During installation, the OS checks the integrity of the app by comparing hash and signature of the app to the one provided by the store
3) The user launches the app (opens it)
4) Do device check to prove that the device environment is secure and untampered and collect evidence. 
5) Generate and store hardware protected device keys (possession factor).
6) Validate device integrity evidence in order to issue Wallet Instance Attestation. 
7) After the app genuinity and device security has been validated, the Wallet Instance attestation is sent to the Wallet App by the Wallet provider. It is a short-lived token attestation that proves that the Wallet App is genuine and the Wallet Provider is trusted.
8) The WIA is stored in the app. 
9) The user is prompted to enter a PIN (knowledge factor).
10) The Wallet app sets up a secure user private key storage (f.ex.in a HSM or locally). 
11) Wallet registration means that a user profile is created at the Wallet provider, linked to the device, user and wallet instance. 
12) Optional: In some processes, a user protected signing key is generated in a HSM and a reference is associated with the user-profile. 
13) With the assurance of hardware protected keys and user control over a device and Wallet App, the Wallet Provider generates the Wallet Unit Attestation (WUA). The WUA is a key-attestation and proof that the users keys for a certain Wallet App are managed securely. 
14) User is prompted to choose a PID Provider
15) User unlocks the secure storage with the PIN in order to be able to use the WUA and WIA. 
16) WIA is sent to the PID Issuer to authenticate the WA and check the Wallet Provider trusted root.
17) The user is authenticated. How authentication works depends on the PID issuer and methods used. 
18) The user is prompted to prove his/hers identity by using the national eID card on LoA High. The card is usually read by NFC.
19) The data is sent to the IDP and the IDP answers with an access token to the Wallet Adapter. 
20) The Wallet App sends the access token and WUA to the PID Issuer
21) PID Issuer verifies access token and validates WUA. PID Issuer obtains data for PID (f.ex. in trusted channel from IDP)
22) PID Issuer stores revocation details inside the PID attestation and its own register and reserves an index (if status lists are used).
23) PID Issuer seals the PID
24) PID Issuer sends PID to Wallet App via OpenID4VCI
25) Optional: User accepts the PID in the Wallet App
26) In some cases the PID can be stored server-side (Wallet Provider)

![General PID issuing process ](04-images/PID-issuing.png "PID Issuing")

PlantUML macro [here](04-images/plantuml_export.puml).

### 4.2.2 Examples for Wallet and PID Lifecycle in Germany
This chapter shows examples from the German EUDI Wallet in sequence diagrams for

1) [Wallet Activation](https://gitlab.opencode.de/bmi/eudi-wallet/wallet-development-documentation-public/-/blob/main/doc/architecture-concept/flows/00-wallet-activation.md)
2) [Wallet Registration](https://gitlab.opencode.de/bmi/eudi-wallet/wallet-development-documentation-public/-/blob/main/doc/architecture-concept/flows/01-wallet-registration.md)
3) [PID Issuance](https://gitlab.opencode.de/bmi/eudi-wallet/wallet-development-documentation-public/-/blob/main/doc/architecture-concept/flows/21-pid-issuance.md)

There are more diagrams on [Wallet Development Documentation](https://gitlab.opencode.de/bmi/eudi-wallet/wallet-development-documentation-public/-/blob/main/doc/architecture-concept/04-data-flows.md?ref_type=heads)

## 4.3 Interfaces and Protocols
List of integration points that will be formalized in Conformance Specifications.
