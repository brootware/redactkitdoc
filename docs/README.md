# RedactKitDoc

## Title

RedactKit - Sensitive Data Redaction Tool

## Overview

RedactKit is a CLI tool to redact and un-redact sensitive data from multiple log files.

**What is it about?**

GovTech GIG, as the Infrastructure Engineer Capability Center, provides functional leadership to WOG. As part of this initiative, there are tools and processes that Agencies can leverage for their technical operations work. This tool addresses the common issue GIG has faced during the Co-sourcing model with vendors and product principals.

**Scenario:**

- When we seek support from product principals, there may be instances when we will need to send logs with sensitive internal IP addresses, URLs, email addresses, SOE IDs etc. to them.
  - Engineers will then need to manually eyeball and redact such data which could be time-consuming and prone to errors.
- This tool enables engineers to automate this process and save time, thereby, reducing operation overheads and errors.

**Why use a tool?**

- To redact sensitive data like internal IP addresses, emails, domain names, hostnames and SOE-IDs before sending them to product principles for troubleshooting.
- Sure, you can use `sed` and `grep` to redact sensitive data. But the original data is lost.
- RedactKit CLI tokenizes the sensitive data for later un-redaction if you need to deep dive into certain parts of the log file during troubleshooting.

## Features

A python-based command line tool that helps you automate the redaction of common sensitive data from the log files. The tool can be used on GSIB via Powershell. Engineers can redact / un-redact sensitive log data using the tool.

The core redaction engine redacts the following list of data types from your log files. (Extensible to other types of data based on user-defined regular expressions). 📄 ✍️

- SG NRIC 🆔 (M Series not included yet)
- Credit cards 🏧
- URLs 🌐
- Emails ✉️
- Ipv4 📟
- Ipv6 📟
- Base64 🅱️
- SOE-ID 🆔

## Benefits

Saves time ⏳. Focus on what matters.
Here is a sample redaction run on a log file with over 10k lines. If an engineer were to manually go through this it could take about ~6 hours.

```bash
[+] Redacted 10072 targets...
[+] Redacted results saved to ./redacted_test.txt
[+] Estimated total words : 29052
[+] Estimated total minutes saved : 388
[+] Estimated total man hours saved : 6
```

## Getting Started

The tool is available on software center as a GSSP package immediately. (GSSP_Python310 RedactKit_0.1.2)

Agency IT reps can opt to list it in WOG App Library for their respective agency's use.

## Resources

- [Usage Guide](./usage.md)
- [API Usage](./api-usage.md)

## Team profile

- Original Ideation by Benjamin Quek
  - Senior Infrastructure Engineer [LinkedIn](<https://linkedin.com/in/ben-quek-75254a19>)
- Improved and expanded more features by Oaker Min
  - Infrastructure Engineer [LinkedIn](<https://linkedin.com/in/oakermin>)
