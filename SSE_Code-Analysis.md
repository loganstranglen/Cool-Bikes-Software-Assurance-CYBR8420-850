
### Cardea Mobile Agent (Ryan):
* CWE-20 Bad Input Validation
    * components/Registration/ContactInfo/index.js lines 123,180
    * utils/schemas.js line 5
    * Discovered by SonarCloud. What bad input could entail on Cardea Mobile Agent is unknown, and needs further investigation. However, Cardea Mobile Agent has root-level permissions for reading/writing to local files. So a worse-case scenario could result in a rooted/jailbroken phone. 
* CWE-922 Insecure Storage of Sensitive Information
    * android/app/src/main/AndroidManifest.xml line 8
    * Discovered by SonarCloud and predicted by us. Tampering of Cardea User Mobile files can result in changing lab test results. This could allow ill travelers to enter Cardea-restricted restaurants, bars, and clubs. Perry and Ryan predicted this vulnerability as Cardea Mobile Agent's biggest, so having SonarCloud find it too gives it credibility.
* CWE-XXX Logs
    * The threat report brought this issue to light. A manual analysis of the code shows that no logs are kept for Cardea Mobile Agent, like when lab results are received or when the traveler scans a verifier's QR code. Even if logs were kept, Cardea's de-centralized infrastructure demands that logs concerning Cardea Mobile Agent would be stored on the traveler's local files. So there is no garuntee that the logs preserve integrity. This is not a severe vulnerability, but a lack of quality logs means a higher barrier to fixing bugs on the app.
* CWE-XXX No Authentication
    * A manuel review of the code confirmed our suspicion that Cardea Mobile Agent has no authentication. That means that whoever has access to the smartphone can open Cardea Mobile Agent and see the owner's lab results and whatever is in their digital wallet, like passport information. This vulnerability is not the same authentication issue as the verifier's side, in which the verifier can only authenticate traveler's based on their (unreliable) biometric photo. The crux of this authentication issue is that Cardea Mobile Agent has no login. Thus, the access to Cardea Mobile Agent is confined to the PIN/password/fingerprint/face scan of the smartphone, which may be disabled by the user. 


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
