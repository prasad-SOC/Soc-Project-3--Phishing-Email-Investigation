# Phishing Email Investigation

## Overview

This project documents the investigation of a phishing email impersonating Microsoft 365 Support. The objective was to analyze the suspicious email, identify phishing indicators, extract Indicators of Compromise (IOCs), review email headers, assess potential impact, and provide remediation recommendations.

The investigation followed a SOC Analyst Level 1 workflow from initial alert triage through final incident assessment.

---

## Scenario

A user received an email claiming to be from Microsoft 365 Support stating that their password would expire within 24 hours. The email urged the user to verify their account through a provided link to avoid account suspension.

The email was reported for investigation to determine its legitimacy.

---

## Investigation Objectives

* Analyze email content
* Verify sender legitimacy
* Investigate embedded URLs
* Perform email header analysis
* Extract Indicators of Compromise (IOCs)
* Map activity to MITRE ATT&CK
* Assess organizational risk
* Recommend containment actions

---

## Key Findings

### Phishing Indicators Identified

* Suspicious sender using a Gmail address
* Microsoft impersonation attempt
* Urgent and fear-based language
* Generic greeting ("Dear Employee")
* Credential verification request
* Suspicious password verification URL

### Verdict

**Confirmed Phishing Email**

The email attempted to impersonate Microsoft 365 Support and used social engineering techniques to persuade the recipient to disclose credentials.

---

## Email Details

| Field          | Value                                                                       |
| -------------- | --------------------------------------------------------------------------- |
| Subject        | URGENT: Microsoft 365 Password Expiration Notice                            |
| Sender         | [office365.support.team@gmail.com](mailto:office365.support.team@gmail.com) |
| Recipient      | [hemaprasadpotnuru2895@gmail.com](mailto:hemaprasadpotnuru2895@gmail.com)   |
| Classification | Phishing                                                                    |
| Severity       | Medium-High                                                                 |

---

## Email Header Analysis

Authentication checks returned:

| Control | Result |
| ------- | ------ |
| SPF     | PASS   |
| DKIM    | PASS   |
| DMARC   | PASS   |

### Important Observation

Although SPF, DKIM, and DMARC passed successfully, the email was still identified as phishing.

These controls verified that Gmail authorized the sender account, but they do not verify that the sender is actually Microsoft.

This demonstrates an important SOC concept:

> An email can pass SPF, DKIM, and DMARC checks while still being malicious.

---

## Indicators of Compromise (IOCs)

### Email Address

```text
office365.support.team@gmail.com
```

### Suspicious URL

```text
http://microsoft365-password-verification.example
```

### Subject Line

```text
URGENT: Microsoft 365 Password Expiration Notice
```

---

## MITRE ATT&CK Mapping

| Technique ID | Technique                    |
| ------------ | ---------------------------- |
| T1566.002    | Phishing: Spearphishing Link |
| T1078        | Valid Accounts               |

---

## Risk Assessment

### Potential Impact

* Credential Theft
* Unauthorized Account Access
* Business Email Compromise (BEC)
* Data Exposure
* Account Takeover

### Risk Level

**Medium-High**

---

## Recommendations

* Block the sender address
* Block the identified URL
* Remove the email from affected mailboxes
* Educate users on phishing awareness
* Enable Multi-Factor Authentication (MFA)
* Monitor authentication logs for suspicious activity

---

## Tools Used

* Gmail
* Email Header Analysis
* Manual IOC Extraction
* MITRE ATT&CK Framework

---

## Project Structure

```text
Phishing-Email-Investigation/
│
├── README.md
├── Investigation_Report.md
├── IOC_List.md
├── Artifacts/
│   └── URGENT_Microsoft_365_Password_Expiration_Notice.eml
│
└── Screenshots/
    ├── 01_Phishing_Email_Received.png
    ├── 02_Sender_Details.png
    ├── 03_Email_Header.png
    └── 04_Header_Analysis.png
```

---

## Skills Demonstrated

* Email Security Analysis
* Phishing Detection
* Email Header Analysis
* IOC Extraction
* Threat Hunting
* MITRE ATT&CK Mapping
* Incident Response
* Security Documentation

---

## Conclusion

This investigation identified a phishing email impersonating Microsoft 365 Support. Through content analysis, sender verification, URL inspection, and header review, the email was confirmed as a phishing attempt designed to harvest user credentials.

The project demonstrates practical SOC Analyst Level 1 skills in phishing detection, email investigation, IOC identification, and incident response documentation.
