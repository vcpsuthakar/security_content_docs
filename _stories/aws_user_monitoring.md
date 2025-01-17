---
title: "AWS User Monitoring"
last_modified_at: 2018-03-12
toc: true
toc_label: ""
tags:
  - Splunk Enterprise
  - Splunk Enterprise Security
  - Splunk Cloud
---

[Try in Splunk Security Cloud](https://www.splunk.com/en_us/cyber-security.html){: .btn .btn--success}

#### Description

Detect and investigate dormant user accounts for your AWS environment that have become active again. Because inactive and ad-hoc accounts are common attack targets, it's critical to enable governance within your environment.

- **Product**: Splunk Enterprise, Splunk Enterprise Security, Splunk Cloud
- **Datamodel**: 
- **Last Updated**: 2018-03-12
- **Author**: Bhavin Patel, Splunk
- **ID**: 2e8948a5-5239-406b-b56b-6c50f1269af3

#### Narrative

It seems obvious that it is critical to monitor and control the users who have access to your cloud infrastructure. Nevertheless, it's all too common for enterprises to lose track of ad-hoc accounts, leaving their servers vulnerable to attack. In fact, this was the very oversight that led to Tesla's cryptojacking attack in February, 2018.\
In addition to compromising the security of your data, when bad actors leverage your compute resources, it can incur monumental costs, since you will be billed for any new EC2 instances and increased bandwidth usage. \
Fortunately, you can leverage Amazon Web Services (AWS) CloudTrail--a tool that helps you enable governance, compliance, and risk auditing of your AWS account--to give you increased visibility into your user and resource activity by recording AWS Management Console actions and API calls. You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred.\
The detection searches in this Analytic Story are designed to help you uncover AWS API activities from users not listed in the identity table, as well as similar activities from disabled accounts.

#### Detections

| Name        | Technique   | Type         |
| ----------- | ----------- |--------------|
| [AWS Excessive Security Scanning](/cloud/1fdd164a-def8-4762-83a9-9ffe24e74d5a/) | [Cloud Service Discovery](/tags/#cloud-service-discovery) | [TTP](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Detect API activity from users without MFA](/deprecated/4d46e8bd-4072-48e4-92db-0325889ef894/) |  | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Detect AWS API Activities From Unapproved Accounts](/deprecated/ada0f478-84a8-4641-a3f1-d82362d4bd55/) | [Cloud Accounts](/tags/#cloud-accounts) | [Hunting](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Detect Spike in AWS API Activity](/deprecated/ada0f478-84a8-4641-a3f1-d32362d4bd55/) | [Cloud Accounts](/tags/#cloud-accounts) | [Anomaly](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Detect Spike in Security Group Activity](/deprecated/ada0f478-84a8-4641-a3f1-e32372d4bd53/) | [Cloud Accounts](/tags/#cloud-accounts) | [Anomaly](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |
| [Detect new API calls from user roles](/deprecated/22773e84-bac0-4595-b086-20d3f335b4f1/) | [Cloud Accounts](/tags/#cloud-accounts) | [Anomaly](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types) |

#### Reference

* [https://d0.awsstatic.com/whitepapers/aws-security-best-practices.pdf](https://d0.awsstatic.com/whitepapers/aws-security-best-practices.pdf)
* [https://redlock.io/blog/cryptojacking-tesla](https://redlock.io/blog/cryptojacking-tesla)



[*source*](https://github.com/splunk/security_content/tree/develop/stories/aws_user_monitoring.yml) \| *version*: **1**