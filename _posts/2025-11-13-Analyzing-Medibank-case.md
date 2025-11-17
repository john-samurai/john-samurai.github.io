---
title: "Analyzing Medibank’ Handling of the 2022 Data Breach"
date: 2025-11-13T23:00
categories:
  - blog
tags:
  - Medibank
  - Ransomware
---

## Summary

This analysis examines Medibank's response to the October 2022 cyberattack that compromised sensitive data of approximately 9.7 million customers. The breach resulted from stolen credentials and inadequate security controls, particularly the lack of multi-factor authentication on VPN access. While Medibank demonstrated strengths in rapid system restoration (within 24 hours) and transparent communication, critical weaknesses emerged in alert management—with a six-week delay in investigating endpoint detection and response (EDR) alerts—and premature public statements claiming no evidence of breach before thorough verification.

Comparing Medibank's response with the Change Healthcare breach reveals common vulnerabilities including compromised employee credentials and missing MFA implementation, both violations of industry standards like HIPAA and Australia's Essential Eight. The analysis highlights that modern ransomware employs "double extortion" tactics involving data exfiltration, making encryption absence insufficient evidence of security. Key recommendations include implementing intelligent alert management systems using machine learning, establishing structured communication frameworks with mandatory investigation checkpoints, and enhancing cybersecurity staffing to address cognitive overload. These lessons emphasize the importance of proactive preparation, proper alert triage, and systematic verification before public disclosure in managing data breach incidents.

## 1. Introduction

In October 2022, Medibank and its subsidiary, ahm, experienced a significant cyberattack that exfiltrated sensitive data from approximately 9.7 million customers. The stolen information included names, dates of birth, home addresses, phone numbers, Medicare numbers, and detailed health-claims records, mental health diagnoses, addiction treatment, and abortion services. Because some affected customers were international students, passport numbers and visa details were also compromised. The breach stemmed from inadequate internal data management and flawed identity and access controls. According to the Office of the Australian Information Commissioner (OAIC), the incident began when an employee of a third-party IT provider saved Medibank administrator credentials to a personal browser profile that synced with a malware-infected device. The attacker then purchased and used these stolen credentials to access Medibank's VPN, which lacked multifactor authentication and required only a device certificate or username and password, installed a malicious script, and extracted roughly 520 GB of data across multiple systems. Although Medibank's endpoint detection and response system generated numerous alerts during this period, these warnings were not properly triaged or escalated. On 13 October 2022, Medibank issued a public statement asserting that it had taken the affected systems offline and found no evidence of customer-data access, in subsequent investigations, however, confirmed that records had indeed been compromised. Between 9 November and 1 December 2022, the stolen data was published on the dark web.

## 2. Strengths and Weaknesses of Medibank's Response

### 2-1 Strength in the Detect Phase (EDR)

Regarding the Detect phase of incident response, Medibank demonstrated both strengths and significant weaknesses. According to the OAIC's court filing, Medibank's endpoint detection and response (EDR) system successfully identified and flagged the threat actor's malicious activities in August 2022, generating various alerts that were sent to the IT Security Operations email address. The fact that the EDR system functioned properly and detected anomalous behavior indicates that Medibank had correctly inventoried their IT assets, established baselines of normal network activity and configured detection mechanisms to flag deviations that could indicate security events. This represents effective implementation of key aspects of the preparation and detection phases.

### 2-1 Weakness in the Detect Phase (EDR)

A critical weakness emerged in the alert management process. Despite the EDR system generating appropriate warnings, these alerts were not properly triaged or escalated by either Medibank or its managed service provider, resulting in notifications accumulating unmonitored in a shared mailbox. This failure provided the attacker with an approximately six-week window to operate undetected. Saleem and Naveed (2020) identify ignoring intrusion warnings as a key human error that can lead to data breaches. Their research indicates that high false-positive rates in intrusion detection systems can cause security personnel to become desensitized to alerts, ultimately leading them to ignore genuine threats. Bolzoni et al. (2007) state that the high volume of false alarms, which can represent up to 99% of total alerts in some systems, creates alert fatigue among IT staff. This potentially explains why Medibank's security team failed to properly investigate the legitimate warnings generated by their EDR system.

### 2-1 Improvement Approach towards the Weakness (EDR)

Ghadermazi et al. demonstrate that introducing machine learning and mathematical optimization methods to SOC operations can dynamically improve throughput during work shifts. Medibank should deploy an intelligent alert triage system using machine learning to automatically prioritize alerts based on risk severity and reduce false positives.

### 2-2 Strength in the Respond Phase (Communication)

One of Medibank's notable strengths was its public communication strategy. NIST SP 800-61r3 identifies public affairs and media relations as a key organizational function in incident response. Ping et al. (2017) emphasize that the timing of disclosure is critical in cyber-incident handling, for example, Yahoo waited until 2016 to acknowledge its 2014 breach, which led to significant financial losses and reputational damage. In contrast, Medibank classified the event as a high-severity incident and, within days of triaging it, informed Chief Executive David Koczkar of suspicious activity detected on the company network, prompting executives to issue a public notification as soon as possible.

### 2-2 Weakness in the Respond Phase (Communication)

While the Australian Securities Exchange (ASX) suggests that disclosure may not be required during initial stages where it is not yet clear what information has been accessed, Medibank's initial notification asserted that there was no evidence of a breach, only for it later to emerge that a massive data compromise had occurred. This discrepancy underscores the importance of confirming breach details prior to public announcements to avoid misleading stakeholders and maintain credibility.

### 2-2 Improvement Approach towards the Weakness (Communication)

Medibank should establish a graduated communication framework with mandatory investigation checkpoints before public statements. Additionally, they should create pre-written template communications for different investigation stages to avoid definitive statements about data compromise until verified.

### 2-3 Strengths in the Recover Phase (System Restoration)

Medibank demonstrated effective system restoration capabilities by restoring access to their ahm and international student policy systems on completely new IT infrastructure, with normal operations resuming on 14 October 2022 which was just one day after acknowledging suspicious activities. This rapid restoration represents strong business continuity planning and demonstrates their ability to maintain critical services during a crisis. By rebuilding systems on new infrastructure rather than simply restoring compromised systems, Medibank not only ensured operational continuity but also preserved the integrity of their forensic investigation. This systematic approach to recovery indicates mature incident response procedures that align with higher levels of cybersecurity capability maturity frameworks, suggesting well-defined and managed recovery processes.

### 2-3 Weaknesses in the Recover Phase (System Restoration)

In Medibank's 17 October announcement, the company mentioned "ransomware" for the first time, stating that they had contained the ransomware threat because their systems were not encrypted. This assessment reveals a critical gap in understanding modern ransomware tactics and represents premature conclusions about threat containment. MacColl et al. (2024) document that since late 2019, cybercriminals have adopted "double extortion" tactics, stealing victims' data in addition to encrypting it, then threatening to leak the information unless ransom demands are met. These evolved ransomware tactics demonstrate that the absence of encryption does not guarantee data security. In the Medibank case, concluding that the ransomware threat was contained solely because systems remained unencrypted was premature and failed to account for the possibility of data exfiltration—a conclusion that proved incorrect when the breach was later confirmed.

### 2-3 Improvement Approach towards the Weakness (System Restoration)

Medibank should establish a comprehensive threat intelligence program or team that continuously monitors and analyzes evolving cyber threats' tactics, techniques and procedures. This program should integrate real-time threat feeds, dark web monitoring, and intelligence from cybersecurity vendors to track emerging attack patterns.

## 3. Comparative Analysis

Change Healthcare data breach can be a comparative case (Table 1). It was detected on February 21, 2024, when they experienced widespread system outages and immediately shut down its entire network to isolate the intruders.

### Table 1: Comparison of Medibank and Change Healthcare case

| Category                            | Medibank                                                                                                                                 | Change Healthcare                                                                                                                                                                                                                     |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stolen Information**              | Names, Dates of birth, Gender, Home addresses, Email addresses, Phone numbers, Medicare numbers, Visa details, Health claims data, etc.  | Names, Dates of birth, Home addresses, Email addresses, Phone numbers, Social Security numbers, Driver's license or state ID numbers, Passport numbers, Health Insurance Information, Health Information, Financial Information, etc. |
| **Stolen Data Size**                | 520 GB                                                                                                                                   | 6 TB                                                                                                                                                                                                                                  |
| **Num of Affected People**          | 9.7 million                                                                                                                              | 190 million                                                                                                                                                                                                                           |
| **Detect**                          |                                                                                                                                          |                                                                                                                                                                                                                                       |
| Initial Access                      | - Stolen credential<br>- Stolen from the third-party employee's personal device                                                          | - Stolen credential<br>- Stolen from an employee by an Infostealer                                                                                                                                                                    |
| Exploited Technical Vulnerabilities | Lack of multi-factor authentication on VPN                                                                                               | - Lack of multi-factor authentication on remote access server<br>- Legacy payment system vulnerabilities                                                                                                                              |
| Alert Management                    | - 6 weeks detection gap from initial breach<br>- Not appropriately triaged or escalated either by Medibank staff or its service provider | 9 days detection gap from initial breach                                                                                                                                                                                              |
| Threat Group                        | Revil (Ransomware group)                                                                                                                 | - BlackCat (Ransomware as a service)<br>- RansomHub                                                                                                                                                                                   |
| **Respond**                         |                                                                                                                                          |                                                                                                                                                                                                                                       |
| Communication                       | Rapid but premature disclosure                                                                                                           | Rapid acknowledgement but delayed and hidden notifications                                                                                                                                                                            |
| Ransom Decision                     | Not paid                                                                                                                                 | Not paid                                                                                                                                                                                                                              |
| **Recover**                         |                                                                                                                                          |                                                                                                                                                                                                                                       |
| System Restoration Approaches       | - Restored access to ahm and international student policy systems within 24 hours<br>- Built systems on completely new IT infrastructure | - 9 months for full restoration of existing system<br>- Build alternative systems with limited functionalities                                                                                                                        |

### Common Trends in Both Cases

#### Insider Threats and Compromised Credentials

Both breaches involved stolen employee credentials that enabled external attackers to gain unauthorized access, representing a form of insider threat through credential compromise. In the Change Healthcare incident, an employee downloaded a malicious file from a file-sharing website (device type unspecified), which resulted in the installation of Infostealer malware that subsequently harvested credentials used to access the remote server. In contrast, in the Medibank case, an employee of a third-party IT provider contracted by Medibank saved their Medibank admin credentials to their personal internet browser profile on their work computer, which automatically synced to their personal device. When the personal device became infected with malware, the credentials were harvested and later exploited by attackers.

Several best practices can address these vulnerabilities. Sinclair and Smith (2008) emphasize that organizations must implement correct access control policy that simultaneously grants the user sufficient privileges to perform necessary tasks, yet also appropriately constrains access according to the principle of least privilege. In the Medibank case, the third-party contractor possessed excessive admin privileges across most of Medibank's systems, violating this fundamental principle. In the Change Healthcare case, the employee had unrestricted access to external websites and file downloads. Therefore, privileges should be carefully determined based on specific job roles and responsibilities. Additionally, comprehensive cybersecurity education is essential. Keeper Security research demonstrates that employees can be an organization's weakest link, so organizations should conduct regular training on identifying and avoiding common cyber threats.

#### Lack of Multi-Factor Authentication (MFA)

Both organizations lacked multi-factor authentication on critical access points, relying solely on username and password combinations for access control. This fundamental security oversight enabled attackers to gain unauthorized access using stolen credentials without additional verification requirements. Suleski et al. (2023) states that MFA improves the functionality of SFA and 2FA by providing additional layers of security that an adversary must obtain to masquerade as a legitimate user. It provides additional defence against brute-force attacks, dictionary attacks, snooping, or man-in-the-middle (MITM) tactics by adding a factor of possession (e.g. a smartphone), which acts as an extra step in the authentication process. Failure to implement MFA represents a violation of established regulatory requirements and industry standards. MFA is both a HIPAA requirement for healthcare organizations and one of the Australian Signals Directorate's Essential Eight security strategies. Given these mandatory frameworks, both organizations should have implemented multi-factor authentication as a baseline security control. The absence of this fundamental protection mechanism demonstrates significant gaps in compliance with industry-standard security practices and regulatory obligations.

The practices that can be applied to both organizations are, first, regulatory compliance implementation. Both organizations failed to meet mandatory regulatory requirements. Healthcare organizations must implement MFA solutions that leverage at least two distinct categories from NIST's framework: something you know, something you have, and something you are. As Meyer et al. (2023) demonstrate that MFA reduces the risk of compromise by 99.22% across the entire population and by 98.56% in cases of leaked credentials, MFA implementation is essential. Additionally, risk-based authentication should be implemented as a complementary security measure. OWASP guidance recommends implementing risk-based authentication to balance security with usability, including requiring MFA when users log in from new devices or locations, particularly those considered high-risk. This approach could have prevented both breaches, in which attackers accessed systems from unauthorized locations.

### Different Area in Both Cases

#### Alert Management

One of the biggest differences between the organizations is alert management (Table 2). Medibank's EDR system generated alerts approximately one to two days after the initial breach, but the organization took approximately six weeks to act on these alerts. In contrast, Change Healthcare detected the breach nine days after the initial intrusion and took immediate action by shutting down their entire network to isolate the intruders.

### Table 2: Comparison of Alert Management

|                       | Medibank                                                            | Change Healthcare                                  |
| --------------------- | ------------------------------------------------------------------- | -------------------------------------------------- |
| **Initial Breach**    | Around 23 August 2022 (Access to VPN)                               | February 12, 2024 (Access to remote access server) |
| **EDR Detection**     | Started from 24 - 25 August 2022                                    | February 21, 2024                                  |
| **Response Recovery** | 11 October 2022 (Built systems on completely new IT infrastructure) | February 21, 2024 (Shut down the entire network)   |

## 4. Personal Reflection and Recommendations

### Alert Management

I served in a government role for seven years, coordinating tasks across multiple agencies and assigning work to the appropriate divisions which had a role that functioned much like an incident handler. Despite maintaining careful attention to detail, I occasionally overlooked critical tasks, which colleagues later identified. This personal experience illustrates how cognitive overload can affect even dedicated professionals. Uncapher et al. (2017) demonstrate that heavy media multitasking reduces cognitive capacity and accuracy, causing individuals to lose focus when juggling numerous responsibilities. Similarly, Medibank's cybersecurity staff likely experienced cognitive overload from managing high volumes of alerts.

**Recommendations: Implementing Intelligent Alert Management Systems**

Medibank should deploy comprehensive alert management. First, implementing machine learning and mathematical optimization into SOC operations could significantly reduce operator workloads by automatically filtering false positives and prioritizing genuine threats. Second, Medibank should expand their cybersecurity team with appropriately skilled personnel. By implementing intelligent alert triage systems and increasing staffing levels, Medibank can ensure to detect and investigate subtle threats/changes in the environment.

### Communication Management

During my service in the government, I participated in updating our Business Continuity Plan (BCP), which included developing a comprehensive flowchart outlining response actions for various incident scenarios. This flowchart provided clear, step-by-step guidance that enabled personnel to understand and implement appropriate responses efficiently during crisis situations. This framework proved invaluable when a major earthquake occurred several years ago. The designated personnel systematically assessed whether our IT infrastructure remained operational and reported the results to an emergency response team within the government. Knight and Nurse (2020) emphasize that crisis communication is crucial in managing the confusion and uncertainty that characterizes cyber security incidents. Their research develops a comprehensive framework to help organizations communicate effectively after experiencing cyber security breaches. The framework emphasizes the critical importance of preparing communication strategies before incidents occur, including stakeholder identification, message development guidelines for different incident phases, channel selection criteria, and timeline considerations for disclosure and ongoing communication. Upon examining Medibank's initial public statement, it became evident that the organization lacked a practical communication framework for incident response. Their premature declaration that "there was no evidence of a breach" demonstrated insufficient preparation and verification procedures before making public announcements. This approach contradicted established best practices for crisis communication, which emphasize accuracy and measured responses.

**Recommendation: Implement a Structured Communication Framework**

Medibank should develop and implement a comprehensive communication framework based on established research such as Knight and Nurse's model. This framework should include pre-drafted message templates for various breach scenarios, clear verification procedures before public statements, defined stakeholder communication protocols, and established timelines for disclosure. Given that similar incidents had occurred at other Australian organizations like Optus, Medibank should have proactively developed robust incident communication procedures rather than responding reactively. The organization must recognize that data breaches represent a significant business risk requiring systematic preparation and response strategies.

## 5. Conclusion

The analysis of Medibank's 2022 data-breach response reveals a mixed performance, offering important lessons for cybersecurity management. While Medibank demonstrated strengths in rapid system restoration and transparent communication, the six-week delay in investigating EDR alerts and the premature public statements claiming no evidence of a breach exposed fundamental gaps in its incident-response capabilities. The comparative analysis with Change Healthcare highlights areas where Medibank excelled as well as aspects requiring improvement. Recommendations, such as implementing intelligent alert-management systems, establishing structured communication frameworks, and enhancing cybersecurity staffing, provide actionable pathways to bolster organizational resilience against future cyber threats.

## 6. References

### Academic Literatures

Bolzoni, D., & Etalle, S. (2007). The 21st Large Installation System Administration Conference. ATLANTIDES: An Architecture for Alert Verification in Network Intrusion Detection Systems. (2025).
https://www.usenix.org/legacy/event/lisa07/tech/full_papers/bolzoni/bolzoni_html/

Jalal Ghadermazi, Shah, A., & Sushil Jajodia. (2024). Digital Threats Research and Practice, 5(2), 1–23. A Machine Learning and Optimization Framework for Efficient Alert Management in a Cybersecurity Operations Center.
https://doi.org/10.1145/3644393

Knight, R., & Nurse, J. R. C. (2020). Computers & Security, 99, 102036. A Framework for Effective Corporate Communication after Cyber Security Incidents.
https://doi.org/10.1016/j.cose.2020.102036

Maccoll, J., Hüsch, P., Mott, G., Sullivan, J., Nurse, J., Turner, S., & Pattnaik, N. (2024). Royal United Services Institute. The Scourge of Ransomware Victim Insights on Harms to Individuals, Organisations and Society.
https://static.rusi.org/ransomware-harms-op-january-2024.pdf

Meyer, L. A., Romero, S., Bertoli, G., Burt, T., Weinert, A., & Ferres, J. L. (2023, May 1). ArXiv.org. Cornell University. How effective is multifactor authentication at deterring cyberattacks?. https://doi.org/10.48550/arXiv.2305.00945

Saleem, H., & Naveed, M. (2020). Proceedings on Privacy Enhancing Technologies, 2020(4), 153–174. SoK: Anatomy of Data Breaches. https://doi.org/10.2478/popets-2020-0067

Sinclair, S., & Smith, S. W. (2008). Insider Attack and Cyber Security, 165–194. Preventative Directions For Insider Threat Mitigation Via Access Control.
https://doi.org/10.1007/978-0-387-77322-3_10

Suleski, T., Ahmed, M., Yang, W., & Wang, E. (2023). Digital Health, 9(1), 1–20. A review of multi-factor authentication in the internet of healthcare things. https://doi.org/10.1177/20552076231177144

Uncapher, M. R., Lin, L., Rosen, L. D., Kirkorian, H. L., Baron, N. S., Bailey, K., Cantor, J., Strayer, D. L., Parsons, T. D., & Wagner, A. D. (2017). Pediatrics, 140(Supplement 2), S62–S66. Media Multitasking and Cognitive, Psychological, Neural, and Learning Differences.
https://doi.org/10.1542/peds.2016-1758d

Wang, P. & Park, S. (2017). Issues in Information Systems, 18(2), 136–147. COMMUNICATION IN CYBERSECURITY: A PUBLIC COMMUNICATION MODEL FOR BUSINESS DATA BREACH INCIDENT HANDLING. https://iacis.org/iis/2017/2_iis_2017_136-147.pdf

### Others

Alder, S. (2018, January 9). HIPAA Journal. The HIPAA Password Requirements and the Best Way to Comply With Them. https://www.hipaajournal.com/hipaa-password-requirements/

Australian Cyber Security Centre. (n.d.). Essential Eight. https://www.cyber.gov.au/resources-business-and-government/essential-cybersecurity/essential-eight

Office of the Australian Information Commissioner. (2024, June 5). OAIC takes civil penalty action against Medibank. https://www.oaic.gov.au/news/media-centre/oaic-takes-civil-penalty-action-against-medibank

OWASP. (n.d.). OWASP Cheat Sheet Series. Multifactor authentication cheat sheet.
https://cheatsheetseries.owasp.org/cheatsheets/Multifactor_Authentication_Cheat_Sheet.html#Riskbased_authentication_can_be_used_to_challenge_a_request_from_a_new_device_or_location

Ritchie, E. (2022, October 13). Medibank Newsroom. Medibank cyber incident update.
https://www.medibank.com.au/livebetter/newsroom/post/medibank-cyber-incident-update

Ritchie, E. (2022, October 14). Medibank Newsroom. Medibank cyber incident update. https://www.medibank.com.au/livebetter/newsroom/post/cyber-incident-update

Ritchie, E. (2022, October 14). Medibank Newsroom. Medibank cyber incident and trading update. https://www.medibank.com.au/livebetter/newsroom/post/medibank-cyber-incident-and-trading-update

Rutland, R., & Dawson., L. (2024, June 13). Hopgood Ganim Lawyers. Disclosure obligations after a data breach: Updated ASX guidance.
https://www.hopgoodganim.com.au/news-insights/disclosure-obligations-after-a-data-breach-updated-asx-guidance/

Trevino, A. (2024, April 25). Keeper Security Blog. How Organizations Can Prevent Credential Theft. https://www.keepersecurity.com/blog/2024/04/25/how-organizations-can-prevent-credential-theft/

UnitedHealth Group. (n.d.). Change Healthcare Cyberattack Support.
https://www.unitedhealthgroup.com/ns/health-data-breach.html
