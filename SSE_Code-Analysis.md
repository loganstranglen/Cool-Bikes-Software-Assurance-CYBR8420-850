
### Cardea Mobile Agent (Ryan):
The first weakness of Cardea Mobile Agent is CWE-20 Bad Input Validation, found in components/Registration/ContactInfo/index.js lines [123](https://sonarcloud.io/project/security_hotspots?id=redge9987_cardea-mobile-agent&hotspots=AYwTj7HNrAR3_H4WBxcK),[180](https://sonarcloud.io/project/security_hotspots?id=redge9987_cardea-mobile-agent&hotspots=AYwTj7HNrAR3_H4WBxcS) and [utils/schemas.js line 5](https://sonarcloud.io/project/security_hotspots?id=redge9987_cardea-mobile-agent&hotspots=AYwTj7K4rAR3_H4WBxhu). This weakness was hypothesized by the group and confirmed by SonarCloud. What bad input could entail on Cardea Mobile Agent is unknown, and needs further investigation. However, Cardea Mobile Agent has root-level permissions for reading/writing to local files. So a worse-case scenario could result in a rooted/jailbroken phone. 

The second weakness is CWE-922 Insecure Storage of Sensitive Information, found in [android/app/src/main/AndroidManifest.xml line 8](https://sonarcloud.io/project/security_hotspots?id=redge9987_cardea-mobile-agent&hotspots=AYwTj7LArAR3_H4WBxhz). This weakness was discovered after reading the Cardea documentation and reviewing the code manually. Tampering of Cardea User Mobile files can result in changing lab test results. This could allow ill travelers to trick Cardea-restricted restaurants, bars, and clubs. This weakness is Cardea Mobile Agent's biggest, so having SonarCloud find it too raises confidence in the tool. 

The third weakness is CWE-778 Insufficient Logging. The Microsoft Threat Modeling Tool first brought this issue to light. The tool suggested the possible weakness of repudiation on Cardea Mobile App, where logs or audits are not stored in a secure way. A manual analysis of the code revealed that no logs are kept for Cardea Mobile Agent at all. This means that key activity on the app, like receiving lab results or scanning QR codes, go undocumented. Even if logs were kept, Cardea's de-centralized infrastructure demands that logs concerning Cardea Mobile Agent would be dangerously stored on the local file system of the traveler's smartphone. This weakness is not severe, but a lack of logs makes forensic investigation and detecting malicious behavior on the mobile agent impossible. Activity on Cardea software outside of the mobile agent is still logged through the Hyperledger Indy Network. 

The last weakness of Cardea Mobile Agent is CWE-306 Missing Authentication for Critical Function. Without needing to review code, simply launching Cardea Mobile Agent will reveal that it has no user authentication. AKA no login. That means that whoever has access to the smartphone can open Cardea Mobile Agent and see the owner's lab results and whatever is in their digital wallet, like passport information. Thus, access to Cardea Mobile Agent is confined to the PIN/password/fingerprint/face scan of the smartphone, which may or may not be enabled. 


### Cardea Primary Verifier Controller (Perry):
* CWE-327 Use of a Broken or Risky Cryptographic Algorithm
    * util.js line 57
    * SonarCloud proved especially useful here. At first, our group had high confidence in Cardea's encryption since it was spoken highly in the Cardea White Paper page 14. But SonarCloud revealed that the encryption uses a deprecrated cyrptography algorithm. The risk of decrypting Cardea's information is still low, but not a low as initially thought. 
* CWE-200 Exposure of Sensitive Information to an Unauthorized Actor / CWE-319 Cleartext Transmission of Sensitive Information
    * orm/connections.test.js lines 17,37
    * orm/contactsCompiled.test.js line 18
* CWE-1004 Sensitive Cookie Without 'HttpOnly' Flag
    * /index.js line 119
    * SonarCloud also proved useful here. The group assumed that information was sent over HTTPS, since that is standard. But assumptions were proven wrong when SonarCloud revealed that sensitive information was sent over HTTP packets. After manual reveal, the risk was reduced after finding out that the information sent through HTTP was encrypted. But this vulnerability highlights room for security improvement in Cardea. 
