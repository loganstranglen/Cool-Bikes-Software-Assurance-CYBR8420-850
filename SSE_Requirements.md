## Part 1

### Five use cases of Cardea by Hyperledger Labs in association with Linux Foundation Public Health

Patient-Doctor Communication Diagram by Logan

![](https://user-images.githubusercontent.com/87502871/270497268-f5dc94ae-bd10-4844-a740-6b8143e4e07f.jpg)



Traveler-Vendor Access Diagram by Cole

![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/assets/19509882/4af678d9-6376-4f7d-acf8-6ed2c98c7402)


Traveler-Test Result Diagram by Daniel

![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/assets/76424137/f4fd982e-fe03-40cf-9803-6bf76f2d3ca0)

Traveler-Verifier Diagram by Ryan

![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/assets/60804887/d50d146a-08ee-4aae-8bc5-af381e2ad2ca)

### Cardea's Security Alignments
Upon making the misuse cases, several security issues were discovered. For one, the health credential issuer cryptographically sends a credential to the traveler which may contain PII, leading to a risk of reverse-engineering and uncovering the sensitive information within a QR code. Reverse-engineering cryptography is difficult but still presents a misuse case. Second, the weakest link of verifying a credential is a rogue verifier. If a rogue verifier somehow gains access to a traveler's QR credential without their consent, then that could result in unlawful disclosure of medical information. Third, blockchain software such as Cardea has airtight code security, however, is still susceptible to man-in-the-middle attacks. Simply capturing and deciphering web packets can compromise sensitive information. Cardea rightly advertises strong security. And the misuse cases presented in this file are unlikely to happen. However, understanding the misuse and vulnerabilities in any software is the first step to making it more secure. 

### Summary and Reflection

Through the execution of part 1 of the project deliverable, Requirements for Software Security Engineering, all team members took on equal responsibility. Individually, we created Use/Misuse diagrams and uploaded them to the GitHub markdown. Ryan took the lead on part 2 of the assignment and wrote a report regarding the review of OSS documentation and information available to us.
We began working on this deliverable with the wrong idea of how the diagrams were meant to flow, which thankfully was corrected by Dr. Gandhi during our check-in meeting. We then had to rework all of our diagrams, and through this, we collaborated together in part to make sure our diagrams were accurate and fluent. Cole found documentation concerning the software. Perry studied a recorded demonstration that displayed the blockchain software used by Hyperledger Indy Network (used by Cardea). Then Ryan and Daniel assessed and summarized the alignment of security requirements regarding Cardea. Logan summarized deliverable contributions and wrote the reflection. We plan in the future to attempt to better understand the directions given for the deliverables so we can more advantageously use our check-in meetings with the professor. 

## Part 2

Cardea does not publicly document its installation issues, but it does have security configurations that can be adjusted after cloning it from GitHub. The Cardea GitHub has three controller repositories: ![Health Issuer Controller](https://github.com/hyperledger-labs/cardea-health-issuer-controller), ![Primary Verifier Controller](https://github.com/hyperledger-labs/cardea-primary-verifier-controller), and ![Secondary Verifier Controller](https://github.com/hyperledger-labs/cardea-secondary-verifier-controller). All of these controllers have editable fields in their .env file that pertain to security. For all three, the JWT_SECRET and SESSION_SECRET fields hold 32 alpha-numeric digits that serve as the cryptographic private key used to encrypt credentials sent to the Hyperledger Indy Network. 

According to the ![Cardea White Paper](https://wiki.hyperledger.org/display/labs/Cardea?preview=/80780946/80781623/Cardea-White-Paper-V1.0.pdf), the credentials are issued by a health provider and sent to a traveler. The credential is a QR code that is verified by the public health agency that the traveler consents to sharing medical information with. The QR code credential can be configured for minimal disclosure of PII (Personal-Identifiable Information), or predicate proofs which prove medical information without revealing it (p.17). It is up to the public health agency which method of credential to accept.  


