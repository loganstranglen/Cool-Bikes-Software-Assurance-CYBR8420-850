# Open-source Project Proposal

**Group Name:** Cool-Bikes-Software-Assurance

**Group Members:** Perry Donahue, Daniel Mulangu Kaseya, Ryan King, Cole Nardini, Logan Stranglen


## Table of Contents

1. [Introduction](#introduction)
2. [Operational Environment](#operational-environment)
3. [Team Motivation](#team-motivation)
4. [Open-source Project Description](#open-source-project-description)
5. [Licensing](#licensing)
6. [Security-related History](#security-related-history)
7. [Teamwork Reflection](#teamwork-reflection)


## Introduction
**GitHub Repository:** https://github.com/loganstranglen/Cool-Bikes-Software-Assurance-CYBR8420-850

**Open-source Software Project:** Linux Foundation Public Health


## Operational Environment
#### Systems Engineering View Diagram 
![](https://user-images.githubusercontent.com/60804887/267173835-bd6bcc1e-e8b7-442c-b28a-95473dda097d.png)

#### Threats Perceived by User of the Software
This project pertains to healthcare and due to that, there is needed secure storage of sensitive information from threats both internal and external. Information in a healthcare environment often might have to have security measures and compliance protocols to meet various government and organization standards, the most known being HIPAA. 

Internally, any software that is user-facing must have authorization requirements to ensure that only those on a need to know basis can access patient records. With hospitals consisting of hundreds of staff and serving hundreds of people every day, systems must know who and when is accessing information and verify that they have the permissions to do that. Potential threats in this environment are patients, disgruntled employees, and visitors. Anyone that could have access to this software through a clinic office or a nurse’s station would have the ability to gather information they shouldn’t have access to or impact the system negatively.

Externally, any software containing sensitive information or system that supports a critical service is vulnerable to attack due to its high value. Potential threats could include ransomware, data leaks, denial of service, and various other methods of leveraging the value of the system and what it contains.

#### List of Security Features in the Software
LFPH uses Google-Apple Exposure Notification (GAEN) to emit bluetooth low energy (BLE) through an API call in a way without exposing personal identifiable information (PII) through transferred packets. PII confidentiality is especially important when data includes patient health information, such as a COVID-19 exposure. 

According to the LFPH website, hosted projects will also earn a Core Infrastructure Initiative Best Practices badge, demonstrating that a project follows best practices for producing higher-quality secure software. This list of best practices includes: [https://www.bestpractices.dev/en/criteria/0].  This list begins with basic project website content. Projects MUST succinctly describe what the software does (what problem does it solve? The project website MUST provide information on how to: obtain, provide feedback (as bug reports or enhancements), and contribute to the software. The information on how to contribute MUST explain the contribution process (e.g., are pull requests used?) The information on how to contribute SHOULD include the requirements for acceptable contributions (e.g., a reference to any required coding standard).  The software for the project must be released with a FLOSS License. Projects MUST provide basic documentation for the software produced by the project and MUST also provide reference documentation that describes the external interface of the software. The projects must have Change controls via public version-controlled source repositories, Unique version numbering and release notes.  The projects MUST have various reporting processes including, bug-reporting and vulnerability reporting. There is also a quality standard including, working build system, automated test suites, new functionality testing, and warning flags. Security leveraged. Projects MUST have at least one primary developer who knows how to design secure software.  The use of basic good cryptographic practices MUST be in use. Projects MUST be secured against man-in-the-middle (MITM) attacks. Projects MUST have no unpatched vulnerabilities, and have publicly known vulnerabilities fixed. Projects MUST have static and dynamic code analysis tools beyond compilers and safe language models.

## Team Motivation
The reason why our team decided to go with the Linux Foundation Public Health (LFPH) is due to the tremendous sensitive data that occurs to be managed within the public health sector. Data such as patient’s names, address, SSN, health conditions and so on. And as we’re living in an era of innovation where technology  is being used more often in this sector, developers should therefore be more careful about the different open source software that are available out there. And since the mission of the Linux Foundation Public health is to build and promote open source software to improve global health innovation,  that felt like the perfect project for our team.


## Open-source Project Description
#### What is it?
- Linux Foundation Public Health (LFPH) is an open-source organization that focuses on developing and maintaining technology solutions to help public health organizations to combat the spread of infectious diseases and improve overall community health.  Being open source, it brings together a global community of software developers, healthcare experts, and government agencies to collaborate on critical public health initiatives.

#### Contributors 
- Developers, Epidemiologists, government agencies, data scientists, community health advocates

#### Activity
- According to LFPH’s website, their mission is to build, promote and sustain open source software to improve global health innovation.  LFPH is active and responsive to the dynamic challenges of the healthcare system.  Its projects are continually updated and improved to meet evolving needs.   The organization maintains and supports several projects and leverages epidemiological modeling software for public health agencies.

#### Uses
- LFPH is used in a multitude of ways.  Including, COVID-19 Exposure and contact tracing, health data sharing, epidemiological modeling, vaccination tracking and health resource allocation.

#### Popularity
- LFPH’s projects have been adopted on a global scale, their projects are popular due to their proven effectiveness in addressing public health challenges.

#### Languages
- PHP, CSS, SCSS, Shell, JavaScript, Hack, and HTML

#### Platform
- LFPH projects are designed to be platform-agnostic, allowing them to be utilized on various operating systems and devices.

#### Documentation Sources
- Comprehensive documentation is available regarding LFPH projects, making it easy for developers, healthcare professionals and the (us) the general public to understand and use the software.  This documentation includes; the official website, the github repository, and community forums.


## Licensing
#### Licenses
- LFPH’s repository contains data received from Crunchbase. This data is not licensed pursuant to Apache license. However, it is subject to Crunchbase data Access Term. Everything else is under Apache License.

#### Contribution Procedure
- LFPH has a number of tools to enable contribution and collaboration among its community such as slack and mailing list. It hosts a slack organization which can be joined through its github and webpage. It also maintains a number of mailing lists for its community members. The mailing lists are managed by the Linux Foundation staff and LFPH community leadership.

#### Contributor Agreements
- LFPH pledges to respect all people who contribute through reporting issues, posing feature requests, submitting pull requests and other activities. And is committed to making participation in the project harassment-free experience for everyone regardless of their level of experience or ethnicity.


## Security-related History
LFPH’s projects (for example their project COVID green) include a handful of commits fixing errors and finding resolutions to problems over time as the open-source has become more widely adopted. These updates include fixing typescript errors, solving linter errors, resolving GAEN API entitlement restrictions, and to fix general conflicts in code. Overall, there is decent documentation regarding updates up until the end of 2021.
[https://github.com/covidgreen/covid-green-app/commits/current]



## Teamwork Reflection
Our team worked cohesively and was proactive in scheduling times to meet that worked for each of us to choose an open source project. We were able to determine a regular meeting time and everyone was willing to meet a couple extra times to make sure we were able to finish what we needed before our deadlines. Thus far, it seems like everyone has been able to contribute uniquely in their own ways. Each member pitched ideas and weighed the pros and cons of each idea. As the team lead, Perry communicated regularly with Dr. Gandhi set up the Github repository for this proposal. Ryan created the diagram of the Systems Engineering View. Logan typed the security features, description, and security history. Cole typed the security threats and reflection. Daniel typed the team motivation and licenses. As of now, the only issue we as a team have had to resolve was a discrepancy in understanding the project initially and having to find a new open-source software to build our project around. We have since then moved forward in choosing a new open-source (being Linux Foundation Public Health).
