#### Part 1 - Code Review:

The group executed automated code review over the Cardea Mobile Agent, Cardea Primary Verifier Controller, Cardea Mobile Secondary Verifier Agent, Cardea Secondary Verifier Controller, Cardea Health Issuer Controller, and the Cardea Health Issuer UI portions of the code. Whilst doing so, they were able to identify a handful of Mtire Common Weakness Enumerations (CWE) within the open sources Github repository. 

During their code review, they anticipated encountering several challenges. The initial hurdle involved a lack of familiarity with the JavaScript programming language. The second difficulty arose from uncertainty about what specific aspects to scrutinize, given the well-maintained nature of Cardea. The final challenge they foresaw was identifying issues and dealing with uncertainty in associating them with the matching Mitre Common Weakness Enumeration.

(insert Ryan/Perry manual/automated review documentation (See logan/danial example below)

(insert Cole manual/automated review documentation (See logan/danial example below)

Daniel & Logan Code Review:
Regarding the manual code review of Cardea, neither Daniel or Logan have a strong familiarity with JavaScript. So, they opted to fork both of the repositories that were undergoing analysis to their own GitHub accounts. From there, they then employed the native tools GitHub offers to solve errors and issues within written code and went through the folders of both repos’. By doing this, they hoped to find security flaws and syntax errors that would require action to resolve. 

For the automated code review portion of the analysis, the pair chose the tool SonarCloud (SonarCloud Online Code Review as a Service Tool | Sonar) to handle the task of reviewing the repositories that aligned with their initial assurance and misuse cases. After watching a demo of how the tool functioned and deeming it suitable for the task, they decided to implement it themselves and have it analyze the code. By using this tool, they expected to see outcomes such as security vulnerabilities, bugs, and security hotspots that would need attention. 

For their manual review, the two were able to discover argument errors in the code which the automated tool was also able to discover at line 42 of the src/UI/CanUser.js and line 52 of the src/UI/Contact.js. Both instances are only errors in the code, rather than security issues, and were also anticipated.


#### Part 2:


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

### Cardea Health Issuer Controller (Logan & Daniel)

