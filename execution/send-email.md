|||
|---------|------------------------|
|**ID**|**M0020**|
|**Objective(s)**|[Execution](../execution), [Lateral Movement](../lateral-movement)|
|**Related ATT&CK Technique**|[Spearphishing Attachment](https://attack.mitre.org/techniques/T1193), [Spearphishing Link](https://attack.mitre.org/techniques/T1192)|

Send Email
==========
Sends an email message from the system on which the malware is executing to one or more recipients, mostly commonly for the purpose of spamming or for distributing a malicious attachment or URL (malspamming).

**See related ATT&CK Techniques:** [**Spearphishing Attachment**](https://attack.mitre.org/techniques/T1193), [**Spearphishing Link**](https://attack.mitre.org/techniques/T1192). These techniques are defined in PRE-ATT&CK, and being related to initial access are not included in MBC.

Malware Examples
----------------
|Name|Date|Description|
|--------------|--------------------------|-----------------------------|
|[**Gamut**](../xample-malware/gamut.md)|2014|Gamut probes the infected system's SMTP port 25 by sending a test SMTP transaction to mail.ru and hotmail.com. If port 25 is open, the bot requests the spam template and email list, which it uses to send spam. [[1]](#1)|
|[**Bagle**](../xample-malware/bagle.md)|2004|Bagle uses its own SMTP engine to mass-mail itself as an attachment from an infected computer. [[2]](#2)|
|[**TrickBot**](../xample-malware/trickbot.md)|2016|Trojan spyware program that has mainly been used for targeting banking sites.|

References
----------
<a name="1">[1]</a> https://www.trustwave.com/Resources/SpiderLabs-Blog/Gamut-Spambot-Analysis/

<a name="2">[2]</a> https://en.wikipedia.org/wiki/Bagle_(computer_worm)