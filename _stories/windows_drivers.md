---
title: "Windows Drivers"
last_modified_at: 2022-03-30
toc: true
toc_label: ""
tags:
  - Splunk Enterprise
  - Splunk Enterprise Security
  - Splunk Cloud
  - Endpoint
---

[Try in Splunk Security Cloud](https://www.splunk.com/en_us/cyber-security.html){: .btn .btn--success}

#### Description

Adversaries may use rootkits to hide the presence of programs, files, network connections, services, drivers, and other system components.

- **Product**: Splunk Enterprise, Splunk Enterprise Security, Splunk Cloud
- **Datamodel**: [Endpoint](https://docs.splunk.com/Documentation/CIM/latest/User/Endpoint)
- **Last Updated**: 2022-03-30
- **Author**: Michael Haag, Splunk
- **ID**: d0a9323f-9411-4da6-86b2-18c184d750c0

#### Narrative

A rootkit on Windows may sometimes be in the form of a Windows Driver. A driver typically has a file extension of .sys, however the internals of a sys file is similar to a Windows DLL. For Microsoft Windows to load a driver, a few requirements are needed. First, it must have a valid signature. Second, typically it should load from the windows\system32\drivers path. There are a few methods to investigate drivers in the environment. Drivers are noisy. An inventory of all drivers is important to understand prevalence. A driver location (Path) is also important when attempting to baseline. Looking at a driver name and path is not enough, we must also explore the signing information. Product, description, company name, signer and signing result are all items to take into account when reviewing drivers. What makes a driver malicious? Depending if a driver was dropped during a campaign or you are baselining drivers after, triaging a driver to determine maliciousness may be tough. We break this into two categories - 1. vulnerable drivers 2. driver rootkits. Attempt to identify prevelance of the driver. Is it on one or many? Review the signing information if it is present. Is it common? A lot of driver hunting will lead down rabbit holes, but we hope to help lead the way.

#### Detections

| Name        | Technique   | Type         |
| ----------- | ----------- |--------------|
| [Sc exe Manipulating Windows Services](/endpoint/f0c693d8-2a89-4ce7-80b4-98fea4c3ea6d/) | [Windows Service](/tags/#windows-service), [Create or Modify System Process](/tags/#create-or-modify-system-process) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Driver Inventory](/endpoint/f87aa96b-369b-4a3e-9021-1bbacbfcb8fb/) | [Exploitation for Privilege Escalation](/tags/#exploitation-for-privilege-escalation) | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Driver Load Non-Standard Path](/endpoint/9216ef3d-066a-4958-8f27-c84589465e62/) | [Rootkit](/tags/#rootkit), [Exploitation for Privilege Escalation](/tags/#exploitation-for-privilege-escalation) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Drivers Loaded by Signature](/endpoint/d2d4af6a-6c2b-4d79-80c5-fc2cf12a2f68/) | [Rootkit](/tags/#rootkit), [Exploitation for Privilege Escalation](/tags/#exploitation-for-privilege-escalation) | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Registry Certificate Added](/endpoint/5ee98b2f-8b9e-457a-8bdc-dd41aaba9e87/) | [Install Root Certificate](/tags/#install-root-certificate), [Subvert Trust Controls](/tags/#subvert-trust-controls) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Registry Modification for Safe Mode Persistence](/endpoint/c6149154-c9d8-11eb-9da7-acde48001122/) | [Registry Run Keys / Startup Folder](/tags/#registry-run-keys-/-startup-folder), [Boot or Logon Autostart Execution](/tags/#boot-or-logon-autostart-execution) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Service Create Kernel Mode Driver](/endpoint/0b4e3b06-1b2b-4885-b752-cf06d12a90cb/) | [Windows Service](/tags/#windows-service), [Create or Modify System Process](/tags/#create-or-modify-system-process), [Exploitation for Privilege Escalation](/tags/#exploitation-for-privilege-escalation) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows System File on Disk](/endpoint/993ce99d-9cdd-42c7-a2cf-733d5954e5a6/) | [Exploitation for Privilege Escalation](/tags/#exploitation-for-privilege-escalation) | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Windows Vulnerable Driver Loaded](/endpoint/a2b1f1ef-221f-4187-b2a4-d4b08ec745f4/) | [Windows Service](/tags/#windows-service) | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |

#### Reference

* [https://redcanary.com/blog/tracking-driver-inventory-to-expose-rootkits/](https://redcanary.com/blog/tracking-driver-inventory-to-expose-rootkits/)
* [https://www.trendmicro.com/en_us/research/22/e/avoslocker-ransomware-variant-abuses-driver-file-to-disable-anti-Virus-scans-log4shell.html](https://www.trendmicro.com/en_us/research/22/e/avoslocker-ransomware-variant-abuses-driver-file-to-disable-anti-Virus-scans-log4shell.html)
* [https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/daxin-backdoor-espionage](https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/daxin-backdoor-espionage)
* [https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/08064459/Equation_group_questions_and_answers.pdf](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/08064459/Equation_group_questions_and_answers.pdf)
* [https://www.welivesecurity.com/2022/01/11/signed-kernel-drivers-unguarded-gateway-windows-core/](https://www.welivesecurity.com/2022/01/11/signed-kernel-drivers-unguarded-gateway-windows-core/)



[*source*](https://github.com/splunk/security_content/tree/develop/stories/windows_drivers.yml) \| *version*: **1**