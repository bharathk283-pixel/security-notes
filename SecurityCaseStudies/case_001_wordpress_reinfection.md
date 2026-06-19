# Case Study: Website Reinfection Through Compromised Subscriber Account and Vulnerable Component

## Overview

A WordPress website experienced repeated reinfections despite multiple malware cleanups. The objective of the investigation was to identify the root cause of the reinfections and determine how the attacker was regaining access to the website.

## Initial Findings

The website contained known vulnerabilities, including:

* NextMove Lite (Reflected XSS)
* LearnDash LMS (SQL Injection)

However, neither vulnerability directly explained the repeated modification of PHP files and malware reappearance after cleanup.

## Investigation

Firewall and activity logs were reviewed to trace the attack timeline.

The logs showed that a user account named **wp_support** successfully logged into the website shortly before the reinfection occurred.

### User Details

* Username: wp_support
* Role: Subscriber

The account had only Subscriber-level permissions and therefore could not:

* Install plugins
* Edit themes
* Modify WordPress core files
* Access administrative settings

## Attack Sequence

1. The attacker logged in using the **wp_support** account.
2. Several requests were made to administrative areas such as:

   * Plugins page
   * Theme Editor page
   * Plugin management endpoints
3. Access to these areas was denied due to insufficient permissions.
4. Shortly afterward, the attacker executed PHP code through a separate endpoint on the website.
5. The malicious payload attempted to create and deploy additional PHP components, resulting in reinfection.

## Root Cause

The investigation concluded that the reinfections were not caused by the Subscriber account permissions themselves.

Instead, the attacker:

* Obtained access to the **wp_support** account.
* Leveraged a vulnerable component or existing backdoor on the website after authentication.
* Used that vulnerability to execute arbitrary PHP code despite having only Subscriber-level access.

This allowed the attacker to reintroduce malware after each cleanup.

## Why Reinfections Continued

The malware cleanup removed the malicious files, but the underlying access path remained available.

As long as the attacker could:

1. Access the compromised account, and
2. Exploit the vulnerable component,

they were able to reinfect the website repeatedly.

## Remediation

The following actions were recommended:

* Rotate all WordPress, hosting, FTP/SFTP, and database credentials.
* Remove or update vulnerable plugins and themes.
* Review all user accounts and remove unnecessary accounts.
* Audit recently modified files for unauthorized changes.
* Remove any backdoors or unauthorized PHP files.
* Enable additional security monitoring and login protection.

## Key Takeaway

Repeated reinfections are often a sign that the root cause has not been removed. Cleaning malware alone is not sufficient if attackers still retain a method to regain access. In this case, a compromised user account combined with a vulnerable component allowed the attacker to repeatedly execute malicious code and reinfect the website.
