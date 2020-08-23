|||
|---------|------------------------|
|**ID**|**E1055**|
|**Objective(s)**| [Defense Evasion](../defense-evasion), [Privilege Escalation](../privilege-escalation)|
|**Related ATT&CK Technique**|[Process Injection](https://attack.mitre.org/techniques/T1055)|


Process Injection
=================
Malware may execute code in the address space of a separate process. 

See ATT&CK: [**Process Injection**](https://attack.mitre.org/techniques/T1055).

Methods
------- 
* **Shell_TrayWnd**: Injects code using the Shell_TRyaWnd technique.
* **CreateRemoteThread**: Malware creates a thread using CreateRemoteThread (or NtCreateThreadEx, RtlCreateUserThread) and LoadLibrary. The path to the malware's malicious dynamic-link library (DLL) is written in the virtual address space of another process; the malware ensures the remote process loads it by creating a remote thread in the target process. This is one of the most common process injection methods. [[1]](#1)
* **PE Injection**: Malware copies its malicious code into an existing open process and causes it to execute via shellcode or by calling CreateRemoteThread (instead of passing the address of the LoadLibrary) [[1]](#1)
* **Thread Execution Hijacking**: Malware targets an existing thread of a process, avoiding noisy process or thread creations operations. [[1]](#1)
* **SetWindowsHooksEx**: Malware can leverage hooking functionality to have its malicious DLL loaded upon an event getting triggered in a specific thread, which is usually done by calling SetWindowsHookEx to install a hook routine into the hook chain. [[1]](#1)
* **APC Injection**: Malware may leverage Asynchronous Procedure Calls (APC) to force another thread to execute its code by attaching it to the APC Queue of the target thread (using QueueUserAPC / NtQueueApcThread); also called AtomBombing [[1]](#1), [[3]](#3).
* **RunPE**: GetThreadContext / SetThreadContext [[3]](#3).
* **Registry Modification**: Malware may insert the location of its malicious library under a registry key (e.g., Appinit_DLL, AppCertDlls, IFEO) to have another process load its library. [[1]](#1)
* **Extra Window Memory Injection (EWMI)**: Malware may inject into Explorer tray window’s extra window memory [[1]](#1).
* **Shims**: Malware may use shims to target an executable (shims are a way of hooking into APIs and targeting specific executables and are provided by Microsoft for backward compatibility, allowing developers to apply program fixes without rewriting code) [[1]](#1). 


Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|--------|-----------------------------|
|[**UP007**](../xample-malware/up007.md)|April 2016|The UP007 malware family... [[44]](#4)|
|[**TrickBot**](../xample-malware/trickbot.md)|2016|Trojan spyware program that has mainly been used for targeting banking sites.|
|[**Poison-Ivy**](../xample-malware/poison-ivy.md)|2005|After the Poison-Ivy server is running on the target machine, the attacker can use a Windows GUI client to control the target computer. [[2]](#2)|

References
----------
<a name="1">[1]</a> Ashkan Hosseini, *Ten Process Injection Techniques: A Technical Survey of Common and Trending Process Injection Techniques*, July 2017. https://www.endgame.com/blog/technical-blog/ten-process-injection-techniques-technical-survey-common-and-trending-process 

<a name="2">[2]</a> https://www.cyber.nj.gov/threat-profiles/trojan-variants/poison-ivy

<a name="3">[3]</a> https://github.com/LordNoteworthy/al-khaser 

<a name="4">[4]</a> https://citizenlab.ca/2016/04/between-hong-kong-and-burma/