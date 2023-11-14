## Part 1

### Five assurance cases of Cardea by Hyperledger Labs in association with Linux Foundation Public Health
Vendor-Verifier Assurance Case 
![](https://github.com/hydra1114/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/Vendor%20Verifier%20Assurance%20Case%20Revised%202.jpg?raw=true)

Traveler-Consent Assurance Case
![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/AssuranceCaseRyan2.png?raw=true)

Issuer Assurance Case
![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/Issuer%20Assurance%20Case%20Daniel.png?raw=true)

Mobile Agent Vulnerability Assurance Case
![](https://github.com/hydra1114/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/AssuranceCasePerry.png?raw=true)

Secure Data Transmission Assurance Case
![](https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/loganstranglenAssuranceDiagram1.jpg?raw=true)

## Part 2

### Alignment of Evidence

In the Vendor-Verifier Assurance Case above, there are three main pieces of evidence that need to be supplied. The first is that the vast majority of travelers don't lose their phones. While outside of the domain of the system's software, this evidence provides assurance that the intended user can utilize the system. According to a [Statista survey from 2015](https://www.statista.com/statistics/441650/items-lost-stolen-while-traveling/#:~:text=The%20statistic%20shows%20the%20share,a%20smartphone%20stolen%20whilst%20traveling.), 10% of traveler's lose their phone while traveling. While 10% may sound like a low number, for critical functions such as access to a country, this must be evaluated to be acceptable or not. The second evidence is a Hyper Ledger security report. The Cloud Security Alliance published a [security report on Hyper Ledger in 2021](https://theblockchaintest.com/uploads/resources/CSA%20-%20Hyperledger%20Fabric%2020%20Architecture%20Security%20Report%20-%202021.pdf) with an accompanying [Security Controls Checklist](https://cloudsecurityalliance.org/artifacts/hyperledger-fabric-2-0-architecture-security-controls-checklist/) that provides a guide for aligning with the NIST Cybersecurity Framework. The third evidence is a code review to ensure that the verifier is in charge of determining the jurisdiction of governance the traveler is being verified. This can be done manually by looking at the verifier agent's source code. There does not appear to be any documentation explicitly mentioning how this is handled.

In the Traveler-Consent Assurance Case, there are three main pieces of evidence to supply. E1 is [Cardea User Mobile Agent's "Settings" page](https://github.com/hyperledger-labs/cardea-mobile-agent/blob/main/components/Settings/index.js) accessible on the app. Different languages can be set on this page to accommodate those who cannot read English. [E2](https://www.law.cornell.edu/cfr/text/18/3b.5) and [E3](https://www.law.cornell.edu/cfr/text/45/164.502) each refer to different sections of HIPAA's Privacy Rule. E4 is backed by the Youtube video from Indicio: ["Verifiable Health Data: Demonstrating Verifiable Credentials using Cardea"](https://www.youtube.com/watch?v=ruhnyMTqNog&list=LL&index=37&t=2337s) at the 35:16 mark. 

In the Issuer Assurance Case, there are four pieces of evidence to supply. E1 refers to the [Cardea White Paper](https://github.com/hyperledger-labs/cardea.app/blob/main/attachments/Cardea-White-Paper-V1.0.pdf), which gives a high-level view on how the software works. Page 15 shows how the issuer is the only one who has access to the blockchain. E2 is from [this Mimecast article](https://www.mimecast.com/blog/what-is-dos-attack-and-how-to-prevent-it/) that explains best practices for mitigating DoS attacks. These practices would be a desirable feature of Cardea. E3 refers to [this Hyperledger Indy documentation](https://hyperledger.github.io/indy-did-method/#uniqueness-of-dids) that explains how hash collisions in the blockchain are unlikely yet possible. Although the evidence itself is outside the scope of Cardea, it shows how hash colliding is accountable on Cardea's software rather the blockchain's software. Cardea does not handle hash collisions for the blockchain so preventing that would be a desirable feature. E4 refers to Section 6.1 of [this Hyperledger Indy documentation](https://hyperledger-indy.readthedocs.io/projects/sdk/en/latest/docs/design/005-dkms/DKMS%20Design%20and%20Architecture%20V3.html?highlight=backup#offline-recovery), which shows the offline recovery feature of its blockchain. It works by storing an offline encrypted backup of each owner's Cardea "wallet". 

In the Mobile Agent Vulnerability Assurance case, there are six pieces of evidence to ensure the top claim is true. The first, Apple and Google software 
security documentation, is difficult to track down. Apple has [security overview documentation](https://support.apple.com/guide/security/app-security-overview-sec35dd877d0/web), but lacks technical documentation. Google seems to rely on [Google Play Protect](https://developers.google.com/android/play-protect) to monitor for malicious apps and also lacks technical documentation. The second evidence is NIST documentation on secure configuration, which can be found [here](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-128.pdf). The third evidence consists of documentation on secure hashing is found in the Federal Information Processing Standards (FIPS), [here](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf) and [here](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.202.pdf). The fourth piece of evidence is GitHub's documentation on its access control as a secure system, which can be found in their [Get Started](https://docs.github.com/en/get-started/learning-about-github/access-permissions-on-github) documentation. The fifth piece of evidence is documentation on access of the application domain to the user's phone number to be able to implement multi-factor authentication. The only place we've found this mentioned explicitly without verifying through source code analysis is [this YouTube video](https://www.youtube.com/watch?v=ruhnyMTqNog&list=LL&index=37&t=2337s) on Cardea's credentials implementation. The final piece of evidence is a code review report. While this report does not currently exist to determine if this feature is possible, a [quick perusal of source code](https://github.com/hyperledger-labs/cardea-mobile-agent/blob/main/components/Settings/index.js) shows there is space for this feature to be implemented.

In the Secure Data Transmission Assurance Case above, presented are four pieces of evidence to back the claims made. The first evidence bubble states that all health records are protected by the Health Insurance Portability and Accountability Act of 1996 (HIPPA). Under this litigation, specifically 16 CFR 318.1, healthcare professionals are held accountable regarding the safekeeping of health records and if a breach of security (meaning unauthorized acquisition and access) were to occur, there would be repercussions E1: [HIPPA 16 CFR 318.1](https://www.ecfr.gov/current/title-16/chapter-I/subchapter-C/part-318) 
The second evidence presented is that CVS, Walgreens, Rite Aid all retain health records for 10 years and can be provided to customer. This is another way to confirm results and health records if for some reason there would be suspicion of incorrect information committed to Cardea. E2:
[Walgreens](https://www.walgreens.com/topic/pharmacy/healthcare-clinic/patient-resources-and-forms.jsp#:~:text=An%20electronic%20medical%20record%20is,medical%20records%20are%20being%20requested)
[Rite Aid](https://www.riteaid.com/legal/request-records#:~:text=You%20can%20request%20copies%20of,through%20a%20Chrome%20web%20browser)
[CVS](https://care.cvs.com/care-navigation/#/home)
The third evidence assures that even if web traffic were to be modified or a forged certificate leveraged, basic Antivirus such as Norton or McAfee would notify the user and quarantine suspicious downloads (certificate). E3:
[Norton](https://support.norton.com/sp/en/us/home/current/solutions/v80629965)
[McAfee](https://www.mcafee.com/support/?articleId=TS102131&page=shell&shell=article-view )
The fourth and final evidence confirms Cardea's safe handling of health records so it abides by HIPPA’s 45 C.F.R. § 164.524 (a)(1), which states that information, when handled correctly, will be securely and readily available for an individual at their request.
E4: [HIPPA 45 C.F.R. § 164.524 (a)(1)](https://www.law.cornell.edu/cfr/text/45/164.524) 

### Reflection

The following links are parts of the project board related to this assignment:
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/35
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/37
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/38
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/39
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/41
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/42
https://github.com/pdonahue28/Cool-Bikes-Software-Assurance-CYBR8420-850/issues/49

Our team did well on delivering this assignment with better coordination, organization, and timeliness than the last assignment. We met often to figure out the assignment and divide the work. There were issues with finding meeting times that worked with everyone. But most everyone was able to attend most meetings and work together. Each diagram has been run through two or three members before being finalized. We resolved our meeting time issues to just assign three meetings a week (Mondays, Thursdays, and Saturdays at 6:30pm) and just attend as many meetings as possible with regards to our personal schedule. We also had issues with finding information, since Cardea has much of its documentation in the form of videos rather than written documents. We resolved that by seeking out the videos covering Cardea. Looking forward, we will execute the next deliverable in a more swift and decisive manner. 


