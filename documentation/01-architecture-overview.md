# FORTRESS — Architecture Overview

## 1. Project Introduction

FORTRESS is a proposed Zero-Trust AWS Cloud Security Architecture designed to demonstrate how cloud infrastructure can be protected through identity management, access control, security governance, centralized auditing, threat detection, and encryption.

The architecture follows a defense-in-depth approach, combining multiple security controls instead of relying on a single protective mechanism.

## 2. Problem Statement

Organizations operating in cloud environments face several security challenges:

- Unauthorized access to cloud resources.
- Excessive permissions assigned to users.
- Insufficient visibility into account activities.
- Unauthorized modification or disabling of audit logs.
- Potential exposure of sensitive information.
- Difficulty maintaining consistent security policies across multiple accounts.

FORTRESS addresses these challenges through a proposed centralized AWS security architecture.

## 3. Architecture Design

The proposed architecture consists of four major components.

### 3.1 Management Account

The Management Account serves as the organizational control center.

Responsibilities:
- Manage AWS Organizations.
- Establish organizational governance.
- Define and manage Service Control Policies.
- Coordinate member accounts.

### 3.2 Security Account

The Security Account is designed to centralize security monitoring and auditing.

Responsibilities:
- Centralized security monitoring.
- Review CloudTrail audit information.
- Monitor GuardDuty security findings.
- Support compliance monitoring.
- Manage encryption-related security controls.

### 3.3 Workload Account

The Workload Account represents the environment where application infrastructure operates.

Responsibilities:
- Host application resources.
- Apply least-privilege IAM policies.
- Protect cloud infrastructure.
- Follow organizational security restrictions.

### 3.4 AWS IAM Identity Center

IAM Identity Center provides centralized workforce access management.

Responsibilities:
- Centralized user access.
- Assignment of users to permission sets.
- Role-based access to AWS accounts.
- Reduced reliance on individual IAM users for workforce access.

## 4. Security Architecture Components

| Component | Security Function |
|---|---|
| AWS Organizations | Multi-account governance |
| IAM Identity Center | Centralized identity management |
| AWS IAM | Permission management |
| Service Control Policies | Organizational permission boundaries |
| AWS CloudTrail | API activity auditing |
| Amazon GuardDuty | Threat detection |
| AWS KMS | Encryption key management |
| AWS Config | Resource configuration and compliance monitoring |

## 5. Security Principles Applied

### Least Privilege

Users should receive only the permissions required to perform their assigned responsibilities.

### Defense in Depth

Multiple security controls work together to protect cloud resources.

### Centralized Monitoring

Security events and audit information should be accessible through a centralized security monitoring design.

### Encryption

Sensitive information should be protected using appropriate encryption mechanisms.

### Governance

Organizational policies establish security restrictions across AWS member accounts.

## 6. Architecture Workflow

1. Administrators authenticate through IAM Identity Center.
2. Users receive access according to their assigned permission sets.
3. Workload resources operate under applicable IAM permissions.
4. Service Control Policies restrict prohibited actions in member accounts.
5. CloudTrail records AWS API activity.
6. GuardDuty analyzes supported data sources for suspicious activity.
7. Security teams review findings and investigate potential incidents.
8. AWS KMS supports encryption and key management.

## 7. Expected Security Outcomes

- Improved access management.
- Reduced risk of excessive permissions.
- Better audit visibility.
- Improved threat detection capabilities.
- Consistent organizational security governance.
- Stronger protection of sensitive information.

## 8. Implementation Status and Limitations

This project currently represents an architecture design and configuration-documentation exercise.

The IAM and SCP policies are provided as example configurations. CloudTrail, GuardDuty, AWS Config, and KMS are documented as proposed security integrations.

The architecture has not yet been fully deployed or validated across separate AWS accounts.

Further implementation would require:
- Configuring AWS Organizations and member accounts.
- Establishing appropriate cross-account permissions.
- Configuring centralized audit-log storage.
- Enabling and validating security services.
- Testing access restrictions and security findings.

## 9. Conclusion

FORTRESS demonstrates how multiple AWS security services can be integrated into a layered cloud security architecture.

By combining identity management, least-privilege access, organizational governance, auditing, threat detection, and encryption, the proposed design establishes a foundation for a more secure and manageable cloud environment.

---

**Project:** FORTRESS  
**Category:** AWS Cloud Security Architecture  
**Author:** Kirk Jan Ogapong