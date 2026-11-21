# FORTRESS — Zero-Trust AWS Cloud Security Architecture

## Project Overview

FORTRESS is a cloud security architecture project designed to demonstrate how AWS environments can be protected through centralized identity management, least-privilege access, organizational governance, audit logging, threat detection, and encryption.

The project follows AWS security best practices and uses a multi-account architecture model.

## Objectives

- Apply the Principle of Least Privilege using AWS IAM.
- Design organizational security governance using AWS Organizations and SCPs.
- Establish centralized audit logging using AWS CloudTrail.
- Integrate threat detection using Amazon GuardDuty.
- Protect sensitive information using AWS KMS.
- Design a scalable and secure multi-account AWS environment.

## Architecture

The proposed architecture includes:

1. Management Account — AWS Organizations and security governance.
2. Security Account — Centralized security monitoring and auditing.
3. Workload Account — Protected application resources.
4. IAM Identity Center — Centralized identity and access management.

See `architecture/architecture.mmd` for the architecture diagram.

## Security Controls

| AWS Service | Security Implementation |
|---|---|
| AWS IAM | Least-privilege access policies |
| AWS Organizations | Multi-account governance |
| SCP | Restricts disabling CloudTrail |
| AWS CloudTrail | Centralized audit logging design |
| Amazon GuardDuty | Threat detection design |
| AWS KMS | Encryption and key management |

## Repository Structure

```text
fortress-aws-cloud-security/
├── architecture/
│   └── architecture.mmd
├── iam-policies/
│   └── EC2ReadOnlyPolicy.json
├── scp-policies/
│   └── ProtectCloudTrailSCP.json
├── cloudtrail/
│   ├── CloudTrailConfig.json
│   ├── GuardDutyConfig.md
│   └── KMSConfig.md
├── screenshots/
├── documentation/
├── README.md
└── security-analysis.md
```

## Key Security Principles

- Least Privilege
- Defense in Depth
- Centralized Monitoring
- Encryption at Rest
- Identity-Based Access Control
- Security Governance

## Implementation Scope

This repository currently contains architecture designs, example IAM and SCP policies, and service configuration documentation.

The AWS service configurations are proposed designs and have not all been deployed or validated in a live multi-account AWS environment.

## Expected Outcomes

- Improved access control
- Better audit visibility
- Centralized security governance
- Enhanced threat detection capabilities
- Stronger data protection

## Technologies

- Amazon Web Services (AWS)
- AWS IAM
- AWS Organizations
- AWS CloudTrail
- Amazon GuardDuty
- AWS KMS
- Mermaid

## Author

Kirk Jan Ogapong

AWS Cloud Infrastructure | Cloud Security

Philippines