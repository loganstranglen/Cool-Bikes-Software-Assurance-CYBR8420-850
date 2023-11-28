
### Cardea Mobile Agent (Ryan):
* CWE-20 Bad Input Validation
    * components/Registration/ContactInfo/index.js lines 123,180
    * utils/schemas.js line 5
CWE-922 Insecure Storage of Sensitive Information
    android/app/src/main/AndroidManifest.xml line 8


### Cardea Primary Verifier Controller (Perry):
* CWE-327 Use of a Broken or Risky Cryptographic Algorithm
    * util.js line 57

* CWE-200 Exposure of Sensitive Information to an Unauthorized Actor / CWE-319 Cleartext Transmission of Sensitive Information
    * orm/connections.test.js lines 17,37
    * orm/contactsCompiled.test.js line 18

* CWE-1004 Sensitive Cookie Without 'HttpOnly' Flag
    * /index.js line 119
