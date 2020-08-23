# <a name="mbc"></a>Malware Behavior Catalog #
The Malware Behavior Catalog (MBC) is a catalog of malware objectives and behaviors, created to support malware analysis-oriented use cases, such as labeling, similarity analysis, and standardized reporting. Please see the [FAQ](yfaq/README.md) page for answers to common questions.

Check out the [MBC presentation](https://www.youtube.com/watch?v=KY8Ty-0sdVU) given at BSides DC (October 2019).

To join the **MBC mailing list**, please send a request to mbc@mitre.org.

### Objectives ###
As shown below, thirteen objectives are defined. Two are specific to malware analysis and are not defined in ATT&CK: ANTI-BEHAVIORAL ANALYSIS and ANTI-STATIC ANALYSIS. Eleven are based on ATT&CK tactics and are tailored for malware analysis use cases. 

### Behaviors ###
Under each objective, MBC captures all behaviors and code characteristics discovered during malware analysis, with links to [ATT&CK Techniques](https://attack.mitre.org/techniques/enterprise/) as appropriate. Names of MBC behaviors may or may not match related ATT&CK techniques. Any content provided on behavior pages is *supplemental* to ATT&CK content. In other words, ATT&CK content is not duplicated in MBC, and MBC users will want to reference ATT&CK while capturing malware behaviors.

### <a name="ids"></a>Identifiers ###
The first letter of a behavior identifier indicates whether the behavior is a stub referencing an ATT&CK technique ("T", matching the ATT&CK identifier; e.g. T1234), whether it enhances an ATT&CK technique with malware-specific details ("E"; e.g. E1234), or whether it is a newly defined behavior in MBC ("M"; e.g. M1234). When two or more MBC behaviors refine the same ATT&CK technique, each is given an MBC identifier and each references the ATT&CK identifier. When a new ATT&CK technique is defined *after* an MBC behavior has been defined, the preexisting MBC identifier is preserved and the new ATT&CK identifier is referenced. 

### Example Malware ###
The MBC also contains a collection of [example malware](xample-malware/) that are characterized with malware behaviors.

## Malware Objective Descriptions ##
Malware objectives are defined below. Follow the links to view associated behaviors. Please see the [MBC Matrix](http://maecproject.github.io/ema/index.html) to view all behaviors.

|**Objective**|**Description**|
|------------------------------------------------------------------|----------------------------|
|[**Anti-Behavioral Analysis**](anti-behavioral-analysis/README.md) |Malware aims to prevent, obstruct, or evade behavioral analysis done in a sandbox, debugger, etc.|
|[**Anti-Static Analysis**](anti-static-analysis/README.md)| Malware aims to prevent static analysis or make it more difficult. Simpler static analysis identifies features such as embedded strings, executable header information, hash values, and file metadata. More involved static analysis involves the disassembly of the binary code.|
|[**Collection**](collection/README.md) | Malware aims to identify and gather information, such as sensitive files, from a target network prior to exfiltration. This objective includes locations on a system or network where the malware may look for information to exfiltrate.|
|[**Command and Control**](command-and-control/README.md) |Malware aims to communicate (receive and/or execute remotely submitted commands) with controlling or controlled systems within a target network (C2 servers, bots, etc.).|
|[**Credential Access**](credential-access/README.md)|Malware aims to obtain credential access, allowing it or its underlying threat actor to assume control of an account, with the associated system and network permissions.|
|[**Defense Evasion**](defense-evasion/README.md)|Malware aims to evade detection or avoid other cybersecurity defenses.|
|[**Discovery**](discovery/README.md)|Malware aims to gain knowledge about the system and internal network.|
|[**Execution**](execution/README.md)| Malware aims to execute its code on a system to achieve a variety of goals.|
|[**Exfiltration**](exfiltration/README.md)|  Malware aims to steal data from the system on which it executes. This includes stored data (e.g., files) as well as data input into applications (e.g., web browser).|
|[**Impact**](impact/README.md)| Malware aims to achieve its mission of manipulating, interrupting, or destroying systems and data.|
|[**Lateral Movement**](lateral-movement/README.md)|Malware aims to propagate through the infection of a system or is able to infect a file after executing on a system. The malware may infect actively (e.g., gain access to a machine directly) or passively (e.g., send malicious email).|
|[**Persistence**](persistence/README.md)|Malware aims to remain on a system regardless of system events.|
|[**Privilege Escalation**](privilege-escalation/README.md)|Malware aims to obtain a higher level of privilege for execution.|

