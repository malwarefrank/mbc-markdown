|||
|---------|------------------------|
|**ID**|**M0004**|
|**Objective(s)**|[Anti-Behavioral Analysis](../anti-behavioral-analysis)|
|**Related ATT&CK Technique**|None|


Emulator Detection
==================
Detects whether the malware instance is being executed inside an emulator. If so, conditional execution selects a benign execution path.

Methods
-------
* **Check for Emulator-related Files**: Checks whether particular files (e.g., QEMU files) exist.
* **Check for WINE Version**: Checks for WINE via the `get_wine_version` function from WINE's `ntdll.dll`.
* **Check Emulator-related Registry Keys**: Emulators register artifacts in the registry, which can be detected by malware. For example, installation of QEMU results in the registry key: *HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 0* with value=*Identifier* and data=*QEMU*, or registry key: *HARDWARE\Description\System* with value=*SystemBiosVersion* and data=*QEMU*. [[1]](#1)
* **Failed Network Connections**: Some emulated systems fail to handle some network communications; such failures will indicate the emulated environment.

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|--------|-----------------------------|


References
----------
<a name="1">[1]</a> http://unprotect.tdgt.org/index.php/Sandbox_Evasion
 
 
