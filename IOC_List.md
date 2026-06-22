# IOC List

## Investigation Summary

This document contains the Indicators of Compromise (IOCs) identified during the phishing email investigation involving a fraudulent Microsoft 365 password expiration notification.

---

# Email Indicators

| IOC Type     | Value                                                                       |
| ------------ | --------------------------------------------------------------------------- |
| Sender Email | [office365.support.team@gmail.com](mailto:office365.support.team@gmail.com) |
| Display Name | narendramodi                                                                |
| Subject      | URGENT: Microsoft 365 Password Expiration Notice                            |

---

# URL Indicators

| IOC Type       | Value                                             |
| -------------- | ------------------------------------------------- |
| Suspicious URL | http://microsoft365-password-verification.example |

---

# Domain Indicators

| IOC Type         | Value                                      |
| ---------------- | ------------------------------------------ |
| Domain           | microsoft365-password-verification.example |
| Associated Brand | Microsoft 365 (Impersonation Attempt)      |

---

# Authentication Results

| Control | Result |
| ------- | ------ |
| SPF     | PASS   |
| DKIM    | PASS   |
| DMARC   | PASS   |

## Notes

The authentication checks passed because the sender legitimately owned the Gmail account used to send the email. However, the sender attempted to impersonate Microsoft 365 Support, making the email malicious despite successful authentication.

---

# Threat Classification

| Category      | Value                 |
| ------------- | --------------------- |
| Threat Type   | Phishing              |
| Attack Vector | Email                 |
| Objective     | Credential Harvesting |
| Risk Level    | Medium-High           |

---

# MITRE ATT&CK Mapping

| Technique ID | Technique                    |
| ------------ | ---------------------------- |
| T1566.002    | Phishing: Spearphishing Link |
| T1078        | Valid Accounts               |

---

# Recommended Blocking Actions

## Block Email Address

```text
office365.support.team@gmail.com
```

## Block URL

```text
http://microsoft365-password-verification.example
```

## Monitor For

* Similar password expiration emails
* Microsoft impersonation attempts
* Suspicious login activity
* Credential theft indicators

---

# IOC Status

| IOC                 | Status     |
| ------------------- | ---------- |
| Sender Email        | Identified |
| Suspicious URL      | Identified |
| Subject Line        | Identified |
| Phishing Indicators | Confirmed  |
| Investigation       | Completed  |

---

# Conclusion

The identified IOCs are associated with a phishing email designed to impersonate Microsoft 365 Support and persuade users to disclose credentials. These indicators should be monitored and blocked where applicable to reduce the risk of future phishing attempts.
