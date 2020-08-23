|||
|---------|------------------------|
|**ID**|**E1486**|
|**Objective(s)**|[Impact](../impact)|
|**Related ATT&CK Technique**|[Data Encrypted for Impact](https://attack.mitre.org/techniques/T1486/), [Encrypt Files - Mobile](https://attack.mitre.org/techniques/T1471/)|


Data Encrypted for Impact 
=========================
Malware may encrypt files stored on the system to prevent user access until a ransom is paid and/or to interrupt system availability. The encryption process usually iterates over all letter drives in the system (except for CD drives) and then recursively encrypts all files with specific suffixes.

See ATT&CK: [**Data Encrypted for Impact**](https://attack.mitre.org/techniques/T1486/) and [**Encrypt Files (Mobile)**](https://attack.mitre.org/techniques/T1471/). 

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|-----------|-----------------------------|
|**CryptoWall** | August 2014 | [[1]](#1)| 
|**CryptoLocker**| December 2013| [[2]](#2)| 

References
----------
<a name="1">[1]</a> http://www.secureworks.com/cyber-threat-intelligence/threats/cryptowall-ransomware/

<a name="2">[2]</a> http://www.secureworks.com/cyber-threat-intelligence/threats/cryptolocker-ransomware/


 
