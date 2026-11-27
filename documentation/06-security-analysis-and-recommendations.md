# FORTRESS — Security Analysis and Recommendations

## 1. Executive Summary

FORTRESS is a proposed AWS Zero-Trust Cloud Security Architecture designed to improve infrastructure security through identity management, organizational governance, centralized auditing, threat detection, and encryption.

This assessment reviews the major security risks addressed by the architecture and identifies additional controls recommended for future implementation.

The project follows a defense-in-depth approach, combining multiple security mechanisms to reduce the likelihood and impact of security incidents.

## 2. Security Risk Assessment

The following table identifies key risks considered in the FORTRESS architecture.

| Security Risk | Potential Impact | Proposed Mitigation |
|---|---|---|
| Excessive IAM permissions | Unauthorized resource access | Least-privilege IAM policies |
| Unauthorized audit log changes | Reduced audit visibility | CloudTrail protection through SCPs |
| Suspicious account activity | Potential account compromise | Amazon GuardDuty |
| Unauthorized encryption key usage | Exposure of sensitive information | KMS key policies and IAM controls |
| Inconsistent account governance | Security configuration gaps | AWS Organizations and SCPs |

## 3. Security Control Analysis

### 3.1 Identity and Access Management

**Risk:** Users or services may receive excessive permissions.

**Existing design control:** EC2ReadOnlyPolicy.json demonstrates restricted read-only EC2 permissions.

**Recommendation:**
- Apply least-privilege access.
- Use centralized identity management.
- Review permissions periodically.
- Require MFA for workforce access.

### 3.2 Organizational Governance

**Risk:** Security restrictions may not be consistently applied across AWS accounts.

**Existing design control:** ProtectCloudTrailSCP.json demonstrates explicit denial of selected CloudTrail management actions.

**Recommendation:**
- Establish organizational units.
- Apply SCPs to appropriate member accounts.
- Test security restrictions.
- Review organizational policies periodically.

### 3.3 Audit Logging and Monitoring

**Risk:** Insufficient audit visibility can make security investigations difficult.

**Existing design control:** CloudTrail is configured as a proposed multi-region organization trail with log-file validation enabled.

**Recommendation:**
- Configure centralized audit-log storage.
- Restrict access to audit logs.
- Monitor logging configuration changes.
- Establish alerts for suspicious activities.

### 3.4 Threat Detection

**Risk:** Suspicious activities may remain undetected.

**Existing design control:** Amazon GuardDuty is included for threat detection and security finding review.

**Recommendation:**
- Enable GuardDuty across supported regions.
- Configure delegated security administration.
- Establish high-severity finding notifications.
- Develop incident response procedures.

### 3.5 Encryption and Key Management

**Risk:** Sensitive information may be exposed if encryption keys are improperly managed.

**Existing design control:** AWS KMS is proposed for customer-managed encryption keys, key rotation support, and restricted key administration.

**Recommendation:**
- Apply restrictive key policies.
- Separate key administration from key usage.
- Enable automatic rotation where supported.
- Monitor key-related API activity.
- Establish key recovery and deletion safeguards.

## 4. Recommended Security Improvements

The following improvements can strengthen the proposed architecture.

| Priority | Recommendation | Purpose |
|---|---|---|
| High | Centralized CloudTrail log storage | Improve audit protection |
| High | GuardDuty delegated administration | Centralize threat monitoring |
| High | IAM permission reviews | Reduce excessive access |
| High | MFA enforcement | Strengthen authentication |
| Medium | EventBridge and SNS integration | Improve security notifications |
| Medium | AWS Config monitoring | Detect configuration drift |
| Medium | Incident response procedures | Improve security response |
| Medium | Periodic SCP testing | Validate governance controls |

These priorities represent proposed recommendations rather than completed deployments.

## 5. Defense-in-Depth Strategy

FORTRESS applies multiple layers of protection.

| Security Layer | AWS Service or Control | Responsibility |
|---|---|---|
| Identity | IAM Identity Center | Workforce access management |
| Access Control | AWS IAM | Permission management |
| Governance | AWS Organizations and SCPs | Organizational restrictions |
| Auditing | AWS CloudTrail | API activity records |
| Threat Detection | Amazon GuardDuty | Suspicious activity detection |
| Encryption | AWS KMS | Cryptographic key management |
| Configuration Monitoring | AWS Config | Resource compliance monitoring |

Each layer supports a different security responsibility, reducing dependence on a single security mechanism.

## 6. Implementation Limitations

FORTRESS currently represents an architecture design and configuration-documentation project.

The configurations and policies in the repository are examples and proposed controls.

The following activities still require live implementation and testing:

- Deploying the multi-account AWS architecture.
- Validating IAM permissions.
- Applying SCPs to member accounts.
- Configuring centralized CloudTrail storage.
- Enabling and testing GuardDuty.
- Creating and configuring KMS keys.
- Testing security findings and incident response.
- Validating the effectiveness of implemented controls.

Consequently, the expected security improvements have not yet been measured through a live deployment.

## 7. Future Development Roadmap

### Phase 1 — Architecture Validation
- Review the architecture diagram.
- Validate IAM and SCP policy syntax.
- Review security configuration documents.

### Phase 2 — AWS Deployment
- Establish AWS Organizations.
- Configure member accounts.
- Implement IAM and SCP controls.
- Configure CloudTrail and GuardDuty.
- Establish KMS encryption controls.

### Phase 3 — Security Testing
- Test permitted and denied IAM actions.
- Validate SCP restrictions.
- Verify audit log delivery.
- Review GuardDuty findings.
- Validate encryption and key permissions.

### Phase 4 — Monitoring Improvements
- Configure centralized security notifications.
- Integrate EventBridge and SNS.
- Establish periodic security reviews.
- Document incident response procedures.

## 8. Conclusion

FORTRESS demonstrates how AWS security services can be combined into a layered cloud security architecture.

The project addresses important cloud security concerns involving identity management, organizational governance, audit logging, threat detection, and encryption.

By incorporating the recommended improvements and validating the proposed controls through live AWS deployment, FORTRESS can evolve into a more comprehensive cloud security implementation.

---

**Project:** FORTRESS  
**Category:** AWS Cloud Security Architecture  
**Security Focus:** Risk Assessment, Governance, Monitoring, and Encryption  
**Author:** Kirk Jan Ogapong