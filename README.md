This repository and documentation describe the **MTA-STS** (Mail Transfer Agent Strict Transport Security) configuration for **Care & Fly** (`careandfly.eu`). MTA-STS enhances email security by enforcing the use of encrypted (TLS) connections and preventing downgrade attacks.

## Overview

MTA-STS ensures that emails sent to Care & Fly domains are encrypted using TLS, protecting them from man-in-the-middle attacks and other forms of interception.

## 📌 MTA-STS Configuration

### MTA-STS Policy File

The MTA-STS policy file is hosted at:
https://mta-sts.careandfly.eu/.well-known/mta-sts.txt


### File Content

```plaintext
version: STSv1
mode: online
mx: mx.zoho.eu
mx: mx2.zoho.eu
mx: mx3.zoho.eu
max_age: 604800
```

- **version**: STSv1: Version of the MTA-STS policy.
- **mode**: testing: Testing mode to avoid delivery errors during the setup phase. online for PROD.
- **mx**: List of MX servers authorized to receive emails for the domain.
- **max_age**: Duration of the policy's validity (in seconds).


This file defines the MTA-STS policy for Care & Fly domains..

------

## 🔧 DNS Configuration

To enable MTA-STS for Care & Fly, the following DNS records must be configured:

1. **CNAME Record**

`mta-sts.careandfly.eu. CNAME careandfly.github.io.`

3. **TXT Record**

`_mta-sts.careandfly.eu. TXT "v=STSv1; id=<UNIX_TIMESTAMP>"`

Replace `<UNIX_TIMESTAMP>` with the current Unix timestamp to ensure the policy is up-to-date.

## 🌐 Hosting with GitHub Pages

The MTA-STS policy file is hosted using **GitHub Pages**, a static site hosting service provided by GitHub. This allows us to easily serve the `mta-sts.txt` file at the required path: `https://mta-sts.careandfly.eu/.well-known/mta-sts.txt`. The CNAME record `mta-sts.careandfly.eu` points to `careandfly.github.io`, where the file is hosted. GitHub Pages is chosen for its simplicity, reliability, and seamless integration with our GitHub repository.

## ？How It Works

1. **Policy Discovery**: When an email is sent to a Care & Fly domain, the sending mail server checks for the MTA-STS policy by querying the DNS TXT record at `_mta-sts.careandfly.eu`.

2. **Policy Retrieval**: The sending mail server then retrieves the MTA-STS policy file from `https://mta-sts.careandfly.eu/.well-known/mta-sts.txt`.

3. **Enforcement**: The sending mail server enforces the policy, ensuring that all emails are sent over TLS.

## Benefits

- **Security**: Protects emails from interception and tampering.
- **Compliance**: Helps meet security and compliance requirements for email communications.
- **Trust**: Enhances trust in email communications with Care & Fly.

## Maintenance

- **Update the Policy**: Regularly update the MTA-STS policy file to reflect any changes in email server configurations.
- **Monitor**: Monitor the MTA-STS configuration to ensure it remains effective and up-to-date.

## Contact

For questions or issues related to the MTA-STS configuration, please contact the Care & Fly IT team.

---
