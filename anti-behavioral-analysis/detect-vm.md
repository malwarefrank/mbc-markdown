|||
|---------|------------------------|
|**ID**|**M0009**|
|**Objective(s)**|[Anti-Behavioral Analysis](../anti-behavioral-analysis)|
|**Related ATT&CK Technique**|[Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497/)|


Virtual Machine Detection
=========================
Detects whether the malware instance is being executed in a virtual machine (VM), such as VMWare. If so, conditional execution selects a benign execution path. [[1]](#1)

The Virtual Machine Detection behavior relates to anti-analysis, whereas a related ATT&CK technique relates to [Defense Evasion](../defense-evasion): for details, see the ATT&CK: [**Virtualization/Sandbox Evasion**](https://attack.mitre.org/techniques/T1497/).

Methods
-------
* **Check File and Directory Artifacts**: Virtual machines create files on the file system (e.g., VMware creates files in the installation directory C:\Program Files\VMware\VMware Tools). Malware can check the different folders to find virtual machine artifacts (e.g., Virtualbox has the artifact VBoxMouse.sys). [[2]](#2)
* **Check Memory Artifacts**: VMware leaves many artifacts in memory. Some are critical processor structures, which, because they are either moved or changed on a virtual machine, leave recognizable footprints. Malware can search through physical memory for the strings VMware, commonly used to detect memory artifacts. [[2]](#2)
* **Check Named System Objects**: Virtual machines often include specific named system objects by default, such as Windows device drivers, which can be detected by testing for specific strings, whether found in the Windows registry or other places.
* **Check Processes**: The VMware Tools use processes like VMwareServices.exe or VMwareTray.exe, to perform actions on the virtual environment. Malware can list the process and searches for the VMware string. Process related to Virtualbox can be detected by malware by query the process list. [[2]](#2)
* **Check Registry Keys**: Virtual machines register artifacts in the registry, which can be detected by malware. For example, a search for "VMware" or "VBOX" in the registry might reveal keys that include information about a virtual hard drive, adapters, running services, or virtual mouse. [[2]](#2) Example registry key value artifacts include "HARDWARE\Description\System (SystemBiosVersion) (VBOX)" and "SYSTEM\ControlSet001\Control\SystemInformation (SystemManufacturer) (VMWARE)"; example registry key artifacts include "SOFTWARE\VMware, Inc.\VMware Tools (VMWARE)" and "SOFTWARE\Oracle\VirtualBox Guest Additions (VBOX)". [[5]](#5)
* **Check Running Services**: VMwareService.exe runs the VMware Tools Service as a child of services.exe. It can be identified by listing services. [[2]](#2)
* **Check Software**: Malware may check whether software is relatively current.
* **Check Virtual Devices**: The presence of virtual devices can indicate a virtualized environment (e.g., "\\.\VBoxTrayIPC"). [[5]](#5)
* **Check Windows**: Malware may check windows for VM-related characteristics such as:
	* *Window size*: tiny window size may indicate a VM.
	* *Unique windows*: may check for the presence of known windows from analysis tools running in a VM.
	* *Title bars*: may inject malicious code to svchost.exe to check all open window title bar text to a list of strings indicating virtualized environment.
* **Guest Process Testing**: Virtual machines offer guest additions that can be installed to add functionality such as clipboard sharing. Detecting the process responsible for these tasks, via its name or other methods, is a technique employed by malware for detecting whether it is being executed in a virtual machine.
* **HTML5 Performance Object Check**: In three browser families, it is possible to extract the frequency of the Windows performance counter frequency, using standard HTML and Javascript. This value can then be used to detect whether the code is being executed in a virtual machine, by detecting two specific frequencies commonly used in virtual but not physical machines.
* **Human User Check**: Detects whether there is any "user" activity on the machine, such as the movement of the mouse cursor, non-default wallpaper, or recently opened Office files. If there is no human activity, the machine is suspected to be a virtualized machine and/or sandbox. Other items used to detect a user: mouse clicks (single/double), DialogBox, scrolling, color of background pixel, change in foreground window [[5]](#5).
* **Modern Specs Check**: Different aspects of the hardware are inspected to determine whether the machine has modern characteristics. A machine with substandard specifications indicates a virtual environment: 
   * *Total physical memory*: most modern machines have at leave 4 GB of memory. (GlobalMemoryStatusEx) [[5]](#5).
   * *Drive size*: most modern machines have at least 80 GB disks. May use DeviceloControl (IOCTL_DISK_GET_LENGTH_INFO) or GetDiskFreeSpaceEx (TotalNumberOfBytes) [[5]](#5).
   * *USB drive*: checks whether there is a potential USB drive; if not a virtual environment is suspected.
   * *Printer*: checks whether there is a potential connected printer or default Windows printers; if not a virtual environment is suspected.
   * *Processor count*: checks number of processors; single CPU machines are suspect.
   * *Keyboard layout*
* **Unique Hardware/Firmware Check**: Malware may check for hardware characteristics unique to being virtualized, allowing the malware to detect the virtual environment. Items checked include:
   * *BIOS*: characteristics of the BIOS, such as version, can indicate virtualization.
   * *I/O Communication Port*: VMware uses virtual I/O ports for communication between the virtual machine and the host operating system to support functionality like copy and paste between the two systems. The port can be queried and compared with a magic number VMXh to identify the use of VMware.
   * *CPU Name*
   * *CPU Location*: When an Operating System is virtualized, the CPU is relocated. [[2]](#2)
   * *MAC Address*: VMware uses specific virtual MAC address that can be detected. The usual MAC address used started with the following numbers: "00:0C:29", "00:1C:14", "00:50:56", "00:05:69". Virtualbox uses specific virtual MAC address that can be detected by Malware. The usual MAC address used started with the following numbers: 08:00:27. [[2]](#2)
* **Instruction Testing**: The execution of certain x86 instructions will result in different values when executed inside of a VM instead of on bare metal. Accordingly, these can be used to detect the execution of the malware in a VM. [[2]](#2)
   * *SIDT (red pill)*: Red Pill is an anti-VM technique that executes the SIDT instruction to grab the value of the IDTR register. The virtual machine monitor must relocate the guest's IDTR to avoid conflict with the host's IDTR. Since the virtual machine monitor is not notified when the virtual machine runs the SIDT instruction, the IDTR for the virtual machine is returned.
   * *SGDT/SLDT (no pill)*: The No Pill technique relies on the fact that the LDT structure is assigned to a processor not an Operating System. The LDT location on a host machine will be zero and on a virtual machine will be non-zero.
   * *SMSW*
   * *STR*
   * *CPUID*: Checking the CPU ID found within the registry can provide information to system type.
   * *IN*
   * *RDTSC*
   * *VMCPUID*
   * *VPCEXT*

Malware Examples
----------------
|Name|Date|Description|
|-----------------------------|-----------|-----------------------------|
|**GravityRAT**|May 2018|GravityRAT checks system temperature by recording thermal readings for detecting VMs. Heat levels indicate whether the system is a VM. [[3]](#3)|
|[**WebCobra**](../xample-malware/webcobra.md)|2018|WebCobra injects malicious code to svchost.exe and uses an infinite loop to check all open windows and to compare each window’s title bar text with a set of strings to determine whether it is running in an isolated, malware analysis environment [[4]](#4)|

References
----------
<a name="1">[1]</a> https://www.fireeye.com/blog/threat-research/2011/01/the-dead-giveaways-of-vm-aware-malware.html 

<a name="2">[2]</a> http://unprotect.tdgt.org/index.php/Sandbox_Evasion

<a name="3">[3]>/a> https://www.hackread.com/gravityrat-malware-evades-detection-targets-india/
 
<a name="4">[4]</a> https://securingtomorrow.mcafee.com/other-blogs/mcafee-labs/webcobra-malware-uses-victims-computers-to-mine-cryptocurrency/

<a name="5">[5]</a> https://github.com/LordNoteworthy/al-khaser
