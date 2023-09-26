## Part 1

Patient-Doctor Communication Diagram

![](https://user-images.githubusercontent.com/87502871/270497268-f5dc94ae-bd10-4844-a740-6b8143e4e07f.jpg)


Traveler-Vendor Access Diagram

![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/assets/19509882/4af678d9-6376-4f7d-acf8-6ed2c98c7402)


Traveler-Test Result Diagram

![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/assets/76424137/f4fd982e-fe03-40cf-9803-6bf76f2d3ca0)



## Part 2

Cardea does not publicly document its installation issues, but it does have security configurations that can be adjusted after cloning it from GitHub. The Cardea GitHub has three controller repositories: ![Health Issuer Controller](https://github.com/hyperledger-labs/cardea-health-issuer-controller), ![Primary Verifier Controller](https://github.com/hyperledger-labs/cardea-primary-verifier-controller), and ![Secondary Verifier Controller](https://github.com/hyperledger-labs/cardea-secondary-verifier-controller). All of these controllers have editable fields in their .env file that pertain to security. For all three, the JWT_SECRET and SESSION_SECRET fields hold 32 alpha-numeric digits that serves as the cryptographic private key used to encrypt credentials sent to the Hyperledger Indy Network. 

According to the ![Cardea White Paper](https://wiki.hyperledger.org/display/labs/Cardea?preview=/80780946/80781623/Cardea-White-Paper-V1.0.pdf), the credentials are issued by a health provider and sent to a traveler. The credential is a QR code that is verified by the public health agency that the traveler consents to sharing medical information with. The QR code credential can be configured for minimal disclosure of PII (Personal-Identifiable Information), or predicate proofs which prove medical information without revealing it (p.17). It is up to the public health agency which method of credential to accept.  


