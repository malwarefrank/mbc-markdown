|||
|---------|------------------------|
|**ID**|**E1089**|
|**Objective(s)**|[Defense Evasion](../defense-evasion)|
|**Related ATT&CK Technique**|[Disabling Security Tools](https://attack.mitre.org/techniques/T1089/)|

Disabling Security Tools
========================
Malware may disable security tools to avoid detection. Security tools include OS security features and updating tools, anti-virus (AV) tools, firewalls, tool components providing security related logging and/or reporting, and Antimalware Scan Interface (AMSI) related capabilities.

Malware-related methods extending ATT&CK's definition are below. 

See ATT&CK: [**Disabling Security Tools**](https://attack.mitre.org/techniques/T1089/).

Methods
-------
* **Disable Kernel Patch Protection**: Bypasses or disables kernel patch protection mechanisms such as Windows' PatchGuard, enabling the malware instance to operate at the same level as the operating system kernel and kernel mode drivers (KMD).

* **Disable System File Overwrite Protection**: Disables system file overwrite protection mechanisms such as Windows file protection, thereby enabling system files to be modified or replaced.

* **Unhook APIs**: Security products may hook APIs to monitor the behavior of malware. To avoid being found, malware may load DLLs in memory and overwrite their bytes. 

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|-----------|-----------------------------|
|[**WebCobra**](../xample-malware/webcobra.md)| 2018 | Loads ntdll.dll and user32.dll as data files in memory and overwrites the first 8 bytes of those functions, which unhooks the APIs. [[1]](#1)|
|[**TrickBot**](../xample-malware/trickbot.md)|2016|Trojan spyware program that has mainly been used for targeting banking sites.|

References
----------
<a name="1">[1]</a> https://securingtomorrow.mcafee.com/other-blogs/mcafee-labs/webcobra-malware-uses-victims-computers-to-mine-cryptocurrency/