# Security Misconfiguration

# Overview

Security misconfiguration occurs when: 

- over-permissive privileges are assigned to entities
- [unnecessary features or services](https://medium.com/@shivam_bathla/omigod-rce-via-secret-agent-9bf8710d32ab) are enabled
- default accounts remain active with unchanged passwords
- security headers are not sent or are overly permissive (over-permissive CORS or CSP policies for instance)
- security features are not enabled (firewall rules, SELinux, Windows Defender, etc…)
- All the issues that could lead to [XXE](https://owasp.org/www-project-top-ten/2017/A4_2017-XML_External_Entities_(XXE)) (the new issue in class)

Misconfiguration vulnerabilities make your application susceptible to attacks that target any part of the application stack. For example, the following attack types may target misconfiguration vulnerabilities:

- `Brute force/credential stuffing`
- `Code injection`
- `Buffer overflow`
- `Command injection`
- `Cross-site scripting (XSS)`
- `Forceful browsing`

# **Catalog of security misconfigurations**

## In Linux

- `Password Policies`
- `Secure Shell`
- `Firewall`
- `OS Security`
- `Linux APT Hardening`
- `Grub Hardening`
- `AppArmor Hardening`
- `User Account Management`
- `Cron or At Utilities`
- `Insecure Services`
- `Mounting Options Security`
- `YUM Hardening`
- `SELinux Hardening`

## In Windows

- `Logon Security`
- `Antivirus Protection`
- `Windows Firewall hardening`
- `Share Permission Management`
- `Chrome Security Hardening`
- `Legacy Protocols`
- `User Account Management`
- `OS Security Hardening`
- `Bitlocker Encryption`
- `Password Policy`
- `Internet Explorer Hardening`

# Demo

## Example

![Untitled](Security%20Misconfiguration%2054df36f603d441a89f3aec6faddf9817/Untitled.png)

In the example above, the attacker modified the connectionId parameter of the GET request **to an API*,*  causing the application server to respond with a detailed exception error with stack trace information. These errors can include information about the application environment such as software vendor names, software packages used, software versions, and lines of code within the backend server-side code that the error resulted.

## [Case Study 1:  ****Exposed JIRA server leaks NASA staff and project data!****](https://logicbomb.medium.com/one-misconfig-jira-to-leak-them-all-including-nasa-and-hundreds-of-fortune-500-companies-a70957ef03c7)

There are a couple of settings in Jira (*An Atlassian task tracking systems/project management software etc.)* that, when not configured properly, may disclose information about the application and its users and it can provide unauthorized access to some internal data of the companies to any other user over the internet. This information may aid an attacker in gaining access to the application.

In Jira, while creating filters or dashboards it provides some visibility option to set on them. The issue was due to the wrong permissions assigned to them. When the filters or dashboards are set the visibility to “All users” and “Everyone” respectively, which instead of sharing with everyone of the organization (which people interpret), it share them publish. There is also a user picker functionality in Jira which gives a complete list of every user’s username and email address. This information disclosure is the result of an authorization misconfiguration in Jira’s Global Permissions settings. Because of the wrong permissions scheme, the following internal information appeared to be vulnerable:

- **all account’s employees’ names and emails,**
- **employees’ roles through JIRA groups,**
- **current projects, upcoming milestones through JIRA dashboards/filters.**

![Untitled](Security%20Misconfiguration%2054df36f603d441a89f3aec6faddf9817/Untitled%201.png)

As can be seen in the above screenshot (first line) there are in total of 1000 NASA internal user details which were getting disclosed by this misconfigured Jira setting.

![Untitled](Security%20Misconfiguration%2054df36f603d441a89f3aec6faddf9817/Untitled%202.png)

# Recommendations

- Regularly monitor web application security and vulnerabilities
- Define and monitor non-default security settings for apps and programs
- Remove unused applications, programs, and features
- Change all default accounts, usernames, and passwords
- Develop an application architecture with secure separation of elements
- Encrypt data-at-rest and data-in-transit