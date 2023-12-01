
### Cardea Mobile Agent (Ryan):
* CWE-20 Bad Input Validation
   * components/Registration/ContactInfo/index.js lines 123,180
   * utils/schemas.js line 5
* CWE-922 Insecure Storage of Sensitive Information
   * android/app/src/main/AndroidManifest.xml line 8


### Cardea Primary Verifier Controller (Perry):
* CWE-327 Use of a Broken or Risky Cryptographic Algorithm
   * util.js line 57
* CWE-200 Exposure of Sensitive Information to an Unauthorized Actor / CWE-319 Cleartext Transmission of Sensitive Information
   * orm/connections.test.js lines 17,37
   * orm/contactsCompiled.test.js line 18
* CWE-1004 Sensitive Cookie Without 'HttpOnly' Flag
   * /index.js line 119

### Cardea Mobile Secondary Verifier Agent (Cole)

The first CWE associated with the Cardea Mobile Secondary Verifier Agent is CWE-250, Execution with Unnecessary Privileges, in [line 5 of the AndroidManifest.xml](https://sonarcloud.io/project/security_hotspots?id=hydra1114_cardea-mobile-secondary-verifier-agent&file=android%2Fapp%2Fsrc%2Fmain%2FAndroidManifest.xml&fileUuid=AYwTawN1GsAc-SEPvuSg&tab=code) file. This is specifically about the repository's requirements of permissions to access the camera. The verifier app does not use the camera as part of its verification process and so the access is unnecessary and may be taken advantage of. This could be a considered a low-level risk as it is a privacy concern, but doesn't give direct access to personal information or higher permissions. We were not originally looking into unexpected permissions as a security risk in our scenarios, so in this case the automated tool helped identify issues we hadn't thought of.

The second CWE detected was CWE-1333, Inefficient Regular Expression Complexity, in [line 159 of components/Registration/BusinessInfo/index.js](https://sonarcloud.io/project/security_hotspots?id=hydra1114_cardea-mobile-secondary-verifier-agent&file=components%2FRegistration%2FBusinessInfo%2Findex.js&fileUuid=AYwTawN1GsAc-SEPvuRq). This CWE would result in a Denial of Servce attack if taken advantage of. However, the context of this flaw is validating the user's phone number. Because of this, the only user being denied service would be the user typing in the phone number, so no security related risk is relavent. Potential inefficiencies leading to DoS attacks is something that we hadn't thought of when evaluating risks in our usage scenarios.

The third CWE found was CWE-319, Cleartext Transmission of Sensitive Information, in [line 9 of AndroidManifest.xml](https://sonarcloud.io/project/security_hotspots?id=hydra1114_cardea-mobile-secondary-verifier-agent&file=android%2Fapp%2Fsrc%2Fmain%2FAndroidManifest.xml&fileUuid=AYwTawN1GsAc-SEPvuSg&tab=code). While fact that cleartext communication is being used in an authentication and permissions application is disconcerting, the context of this flaw in this application according to Cardea's documentation is the transmission of public credentials with a limited lifespan directly with the app requesting verification. Because of the kind of information being transmitted and the nature of the communication, this flaw would be considered medium rather than high risk. Throughout our misuse and assurance cases, secure communication was a requirement of this application. The presence of this flaw, if wide-spread, could be considered a deal breaker.

### Cardea Secondary Verifier Controller (Cole)

There was only one potential security flaw detected in the Secondary Verifier Controller: CWE-1004, Sensitive Cookie Without 'HttpOnly' Flag. This is found in [line 120 of index.js](https://sonarcloud.io/project/security_hotspots?id=hydra1114_cardea-secondary-verifier-controller&tab=code) when creating a new session. It's not clear what the application is using the cookie for, but not setting the HttpOnly flag opens the application up to cross-site scripting attacks where clients can access the information stored in the cookie. Due to the ability of an attacker to access that information, this flaw could be considered medium risk. Further investigation would need to be done to asses how this cookie is used and if sensitive information would be at risk. Safe transmission and data storage is integral for the cardea suite of applications to be used for the purpose it was developed and is something that has been brought up in each of the scenarios we have explored.

