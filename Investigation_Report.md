# Investigation Report: Phishing Email Investigation

## Executive Summary

A suspicious email claiming to be from Microsoft 365 Support was reported for investigation. The email informed the recipient that their Microsoft 365 password would expire within 24 hours and instructed them to verify their account using a provided link.

The investigation identified multiple phishing indicators including sender impersonation, social engineering tactics, urgency-based messaging, and a suspicious credential verification URL. Based on the findings, the email was classified as a phishing attempt designed to harvest user credentials.

---

# Incident Information

| Field              | Value               |
| ------------------ | ------------------- |
| Incident Type      | Phishing Email      |
| Severity           | Medium-High         |
| Status             | Closed              |
| Classification     | Confirmed Phishing  |
| Analyst            | Hema Prasad Potnuru |
| Investigation Date | June 2026           |

---

# Alert Details

## Email Subject

```text
URGENT: Microsoft 365 Password Expiration Notice
```

## Sender

```text
office365.support.team@gmail.com
```

## Recipient

```text
hemaprasadpotnuru2895@gmail.com
```

---

# Investigation Process

## Step 1: Initial Triage

The email was reviewed to determine whether it contained characteristics commonly associated with phishing campaigns.

### Observations

* Urgent subject line
* Password expiration warning
* Request for account verification
* Generic greeting
* Embedded URL
* Microsoft branding references

### Assessment

The email displayed several common phishing indicators and was escalated for detailed analysis.

---

# Step 2: Email Content Analysis

The email body was reviewed to identify social engineering techniques.

## Email Excerpt

```text
Dear Employee,

Our records indicate that your Microsoft 365 password is scheduled to expire within the next 24 hours.

Please verify your account and update your password immediately.
```

## Findings

### Urgency

The sender attempted to create pressure by stating that the recipient's password would expire within 24 hours.

### Fear Tactics

The email warned that failure to act could result in service disruption and account suspension.

### Generic Greeting

The use of "Dear Employee" instead of the recipient's actual name is a common phishing characteristic.

### Credential Request

The recipient was instructed to verify their account and update their password.

### Conclusion

The email uses multiple social engineering techniques intended to encourage immediate user interaction.

---

# Step 3: Sender Analysis

## Observed Sender

```text
office365.support.team@gmail.com
```

## Display Name

```text
narendramodi
```

## Analysis

The sender attempted to appear as a Microsoft support representative while using a Gmail account.

Legitimate Microsoft security notifications are typically delivered from official Microsoft-owned domains.

Examples:

```text
@microsoft.com
@microsoftonline.com
```

The observed sender domain does not belong to Microsoft.

## Conclusion

Sender impersonation detected.

---

# Step 4: URL Analysis

## Extracted URL

```text
http://microsoft365-password-verification.example
```

## Analysis

The URL contains several suspicious characteristics:

### Non-Microsoft Domain

The domain does not belong to Microsoft.

### Credential-Themed Keywords

The URL contains:

```text
password
verification
```

which are commonly used in phishing campaigns.

### HTTP Protocol

The URL uses HTTP rather than HTTPS.

### Brand Impersonation

The URL attempts to appear related to Microsoft 365 services.

## Conclusion

The URL is consistent with a credential harvesting attempt.

---

# Step 5: Email Header Analysis

The email headers were analyzed to verify authenticity and identify signs of spoofing.

## Authentication Results

| Control | Result |
| ------- | ------ |
| SPF     | PASS   |
| DKIM    | PASS   |
| DMARC   | PASS   |

## Header Findings

### Return Path

```text
office365.support.team@gmail.com
```

### Mail Provider

```text
gmail.com
```

### Message Origin

The email originated from Google's mail infrastructure.

## Analysis

Although SPF, DKIM, and DMARC checks passed successfully, this does not indicate that the email is legitimate.

The sender owns the Gmail account used to send the email, allowing authentication checks to pass.

However, the sender is falsely presenting themselves as Microsoft Support.

## Key Finding

Authentication validates domain ownership but does not validate business legitimacy.

A phishing email can successfully pass SPF, DKIM, and DMARC checks while still being malicious.

## Conclusion

No technical spoofing detected. Social engineering and impersonation techniques were used instead.

---

# Indicators of Compromise (IOCs)

## Email Address

```text
office365.support.team@gmail.com
```

## URL

```text
http://microsoft365-password-verification.example
```

## Subject

```text
URGENT: Microsoft 365 Password Expiration Notice
```

---

# MITRE ATT&CK Mapping

| Technique ID | Technique                    |
| ------------ | ---------------------------- |
| T1566.002    | Phishing: Spearphishing Link |
| T1078        | Valid Accounts               |

## Adversary Objective

Credential harvesting through phishing and social engineering.

---

# Risk Assessment

## Potential Impact

* Credential Theft
* Unauthorized Account Access
* Account Compromise
* Data Exposure
* Business Email Compromise (BEC)

## Risk Rating

**Medium-High**

---

# Containment Recommendations

## Immediate Actions

1. Block the sender address.
2. Block the malicious URL.
3. Remove similar emails from user mailboxes.
4. Notify potentially affected users.
5. Monitor for suspicious login attempts.
6. Reset compromised credentials if interaction occurred.

## Long-Term Recommendations

1. Enable Multi-Factor Authentication (MFA).
2. Conduct phishing awareness training.
3. Strengthen email filtering policies.
4. Review email security controls.
5. Perform regular phishing simulation exercises.

---

# Final Verdict

The investigation confirmed that the email was a phishing attempt impersonating Microsoft 365 Support.

The attacker leveraged urgency, credential verification requests, and a deceptive URL to encourage users to disclose sensitive information. While the email successfully passed SPF, DKIM, and DMARC authentication checks, business context and content analysis clearly indicated malicious intent.

The email was classified as a confirmed phishing attempt and appropriate containment recommendations were identified.

---

# Skills Demonstrated

* Email Security Analysis
* Phishing Detection
* Email Header Analysis
* IOC Extraction
* Threat Analysis
* MITRE ATT&CK Mapping
* Incident Response
* Security Documentation
* SOC Analyst Workflow
