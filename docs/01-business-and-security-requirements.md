# Moltrix Endpoint Management Requirements

## Document Status

- **Version:** 0.1
- **Status:** Draft
- **Project:** Moltrix Secure Endpoint Management
- **Platform:** Microsoft Intune and Microsoft Entra
- **Certification alignment:** MD-102

## 1. Business Scenario

Moltrix requires a secure endpoint-management solution for a small hybrid workforce.

Authorized users need access to organizational applications and information from managed Windows devices. A correct username and password alone are not sufficient because an authorized user may attempt to connect from an unsafe device.

The solution must therefore evaluate both the user’s identity and the device’s security condition.

## 2. Project Goal

The goal is to design and test an endpoint-management environment that:

- Verifies user identities through Microsoft Entra ID.
- Manages and evaluates devices through Microsoft Intune.
- Protects organizational information.
- Identifies devices that do not meet security requirements.
- Produces sanitized evidence of configuration and testing.

## 3. Initial Scope

Version 1 will focus on:

- Microsoft Entra test users and groups
- One test Windows device
- Microsoft Intune enrollment
- Antivirus protection
- Windows Firewall
- BitLocker drive encryption
- Device compliance evaluation
- Sanitized test evidence

## 4. Security Requirements

### SEC-01 — Antivirus Protection

Moltrix-managed Windows devices must have antivirus protection enabled and security intelligence kept current.

A device with disabled or outdated antivirus protection must not be considered compliant.

### SEC-02 — Firewall Protection

Moltrix-managed Windows devices must have Windows Firewall enabled.

Intune will be used to configure the required firewall setting and verify that protection remains active.

### SEC-03 — Disk Encryption

Moltrix-managed Windows devices must use BitLocker drive encryption.

BitLocker will protect organizational information stored on a device if the laptop or its storage drive is lost or stolen.

### SEC-04 — Recovery-Key Protection

BitLocker recovery keys must be stored securely and made accessible only to authorized administrators.

Recovery keys must never appear in public screenshots, documentation, or GitHub content.

## 5. Compliance Decisions

A device may receive one of the following results:

- **Compliant:** The device satisfies all required security policies.
- **Noncompliant:** The device fails one or more required security policies.
- **Not evaluated:** Intune has not received enough information to determine the device’s status.
- **In grace period:** The device has temporarily been given time to correct a policy violation.

Security responses should reflect risk. For example:

- Disabled antivirus protection requires urgent remediation.
- A routine update that is slightly overdue may receive a short grace period.
- A seriously compromised device should have access blocked and be investigated.

## 6. Evidence Requirements

### EVD-01 — Evidence Sanitization

All evidence must be inspected and sanitized before publication.

Public screenshots must not expose:

- Passwords, tokens, or recovery codes
- BitLocker recovery keys
- Tenant or subscription identifiers
- Usernames or personal email addresses
- Device IDs, serial numbers, or hardware identifiers
- Confidential organizational information

Evidence may show policy names, security status, compliance results, and test outcomes after sensitive information has been removed.

## 7. Initial Success Criteria

The first project milestone will be successful when:

- The business and security requirements are documented.
- The relationship between Entra ID and Intune is explained.
- The initial endpoint architecture is designed.
- The security policies can be connected to measurable test results.
- All published evidence passes a privacy and security review.

## 8. Current Learning Summary

Microsoft Entra ID verifies who the user is. Microsoft Intune manages the device and evaluates whether it follows organizational security policies.

An authorized identity should not automatically receive access from an unsafe device. Secure access requires both an acceptable identity and an acceptable device.