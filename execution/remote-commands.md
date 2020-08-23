|||
|---------|------------------------|
|**ID**|**M0011**|
|**Objective(s)**| [Execution](../execution)|
|**Related ATT&CK Technique**|None|


Remote Commands
===============
Malware may provide an attacker with explicit commands. This behavior differs from the [Remote Access](../impact/remote-access.md) behavior under the [Impact](../impact) objective in that *Impact: Remote Access* is potentially much broader and may include full remote access.

Given an "execute" command, the attacker may choose to delete files or corrupt data, power-off the machine, or upload and execute other applications. The malware may also provide specific commands to the attacker (e.g., "delete file"). 

Commands provided by the malware can be captured with the methods defined below. For example, malware that enables an attacker to delete a file could be tagged with *Execution:Remote Commands:Delete File*.

It may be useful to capture remote commands along with related behaviors because the associated descriptions could provide details of how the malware implements the command. For example, *Defense Evasion:File Deletion* could be used to provide details and context to *Execution:Remote Commands:Delete File*.

Autonomous behaviors - those done by the malware without an active attacker - should not be captured with *Execution:Remote Commands*. For example, malware that *automatically* destroys data would be tagged with the [Impact: Data Destruction](../impact/data-destruction.md) behavior.

Methods
-------
* **Delete File**
* **Download File**
* **Execute**
* **Shutdown**
* **Sleep**
* **Uninstall**
* **Upload File**

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|--------|-----------------------------|


References
----------
