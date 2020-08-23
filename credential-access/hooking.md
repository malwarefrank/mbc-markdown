|||
|------------------|------------------------|
|**ID**|**E1179**|
|**Objective(s)**|[Anti-Behavioral Analysis](../anti-behavioral-analysis), [Credential Access](../credential-access), [Defense Evasion](../defense-evasion), [Persistence](../persistence), [Privilege Escalation](../privilege-escalation)|
|**Related ATT&CK Technique**|[Hooking](https://attack.mitre.org/techniques/T1179/)|


Hooking
=======
Malware alters API behavior or redirects execution to a malicious API version for a variety of purposes. Malware may use hooking to load and execute code within the context of another process, hiding execution and gaining elevated privileges and access to the process's memory. Methods related to anti-behavioral analysis are below. For example, hooking can be used to prevent memory dumps - see also [Memory Dump Obstruction](../anti-behavioral-analysis/memory-dump-obstruct.md).

For discussion related to the Credential Access, Persistence, and Privilege Escalation objectives, see ATT&CK: [**Hooking**](https://attack.mitre.org/techniques/T1179/). 

Note that in MBC, but not in ATT&CK, Hooking is also associated with the [Defense Evasion](../defense-evasion) and [Anti-Behavioral Analysis](../anti-behavioral-analysis) objectives.

Methods
-------
* **Patch MmGetPhysicalMemoryRanges**: Patching this function to always return NULL prevents drivers from getting information about the physical address space layout, preventing memory dumps. [[1]](#1)
* **Hook memory mapping APIs**: Prevents memory dumps by preventing mapping of memory into the kernel's virtual address space. [[1]](#1)
* **Hook procedures**: Intercepts and executes designated code in response to events such as messages, keystrokes, and mouse inputs. [[3]](#3)
* **Import Address Hooking (IAT) Hooking**: uses modifications to a process's IAT where pointers to imported API functions are stored.
* **Inline Hooking**: overwrites the first bytes in an API function to redirect code flow.

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|-----------|-----------------------------|
|**Kronos**|June 2014 |Kronos hooks the API of processes to prevent detection. [[2]](#2)|
|[**TrickBot**](../xample-malware/trickbot.md)|2016|Trojan spyware program that has mainly been used for targeting banking sites.|

References
----------
<a name="1">[1]</a> J. Stuttgen, M. Cohen, Anti-forensic resilient memory acquisition, www.dfrws.org/sites/default/files/session-files/paper-anti-forensic_resilient_memory_acquisition.pdf

<a name="2">[2]</a> https://blog.malwarebytes.com/cybercrime/2017/08/inside-kronos-malware/ 

<a name="3">[3]</a> https://docs.microsoft.com/en-us/windows/win32/winmsg/about-hooks?redirectedfrom=MSDN#hook-procedures