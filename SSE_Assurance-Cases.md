Part 1

Vendor-Verifier Assurance Case 
![](https://github.com/hydra1114/Cool-Bikes-Software-Assurance-CYBR8420-850/blob/main/Assurance-Diagrams/Vendor%20Verifier%20Assurance%20Case%20Revised%202.jpg?raw=true)




Part 2

In the Vendor-Verifier Assurance Case above, there are three main pieces of evidence that need to be supplied. The first is that the vast majority of traveler's don't lose their phones. While outside of the domain of the system's software, this evidence provides assurance that the intended user can utilize the system. According to a [Statista survery from 2015](https://www.statista.com/statistics/441650/items-lost-stolen-while-traveling/#:~:text=The%20statistic%20shows%20the%20share,a%20smartphone%20stolen%20whilst%20traveling.), 10% of traveler's lose their phone while traveling. While 10% may sound like a low number, for critical functions such as access to a country, this must be evaluated to be acceptable or not. The second evidence is a Hyper Ledger security report. The Cloud Security Alliance published a [security report on Hyper Ledger in 2021](https://theblockchaintest.com/uploads/resources/CSA%20-%20Hyperledger%20Fabric%2020%20Architecture%20Security%20Report%20-%202021.pdf) with an accompanying [Security Controls Checklist](https://cloudsecurityalliance.org/artifacts/hyperledger-fabric-2-0-architecture-security-controls-checklist/) that provides a guide for aligning with the NIST Cybersecurity Framework. The third evidence is a code review to ensure that the verifier is in charge of determining the jurisdiction of governance the traveler is being verified in. This can be done manually by looking at the verifier agent's source code. There does not appear to be any documentation explicitly mentioning how this is handled.
