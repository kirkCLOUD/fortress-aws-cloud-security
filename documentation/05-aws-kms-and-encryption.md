# FORTRESS — AWS KMS and Encryption

## 1. Introduction

AWS Key Management Service (AWS KMS) is a managed service used to create and manage cryptographic keys.

FORTRESS incorporates AWS KMS into its security architecture to protect sensitive information through encryption and controlled key access.

The proposed implementation focuses on protecting centralized audit logs and sensitive workload data.

## 2. Security Objectives

The encryption strategy aims to:

- Protect sensitive information from unauthorized access.
- Establish controlled encryption key management.
- Restrict access to key administration functions.
- Support key rotation.
- Monitor key-related activities.
- Improve data confidentiality and encryption governance.

## 3. FORTRESS KMS Configuration

The project includes:

`cloudtrail/KMSConfig.md`

The configuration identifies the following security controls.

### 3.1 Customer-Managed KMS Keys

FORTRESS proposes using customer-managed KMS keys to provide greater control over encryption key management.

These keys allow administrators to manage key policies, permissions, and lifecycle settings.

### 3.2 Key Rotation

Key rotation is supported as part of the proposed encryption strategy.

Rotation helps reduce the long-term use of a single cryptographic key.

For supported symmetric customer-managed keys, AWS KMS can perform automatic key rotation.

### 3.3 Restrict Key Administration Permissions

Access to key administration functions should be limited to authorized administrators.

This reduces the risk of unauthorized key deletion, modification, or policy changes.

### 3.4 IAM and Key Policies

FORTRESS uses IAM permissions and KMS key policies as complementary access-control mechanisms.

Key policies define access to KMS keys, while IAM policies can also grant permissions when the key policy allows IAM-based access management.

### 3.5 CloudTrail Monitoring

CloudTrail is used to record supported AWS KMS API activity.

This provides audit visibility into key-related operations and supports security investigations.

## 4. Encryption Strategy

FORTRESS proposes using AWS KMS to protect:

- Centralized audit logs.
- Sensitive workload data.
- Other supported AWS resources containing sensitive information.

Encryption at rest helps protect stored information against unauthorized access to the underlying storage.

Actual encryption requires configuring the relevant AWS services to use the selected KMS keys.

## 5. How KMS Integrates with FORTRESS

The proposed workflow is:

1. An AWS resource stores sensitive information.
2. The resource is configured to use an appropriate KMS key.
3. AWS KMS performs or supports the required cryptographic operations.
4. IAM permissions and key policies control access to the key.
5. Key-related API activity is recorded through CloudTrail.
6. Administrators review relevant activity for security and auditing purposes.

## 6. Security Benefits

The proposed KMS implementation supports:

- Improved data confidentiality.
- Centralized encryption key management.
- Controlled key administration.
- Better visibility into key-related activity.
- Support for encryption governance.
- Reduced risk of unauthorized key usage.

## 7. Implementation Limitations

The current FORTRESS project contains KMS configuration documentation and proposed security controls.

The following have not yet been demonstrated through a live AWS deployment:

- Creation of customer-managed KMS keys.
- Configuration and testing of key policies.
- Activation of automatic key rotation.
- Integration of KMS keys with CloudTrail log storage.
- Integration of KMS with sensitive workload resources.
- Validation of key access restrictions.
- Testing of key administration permissions.

These activities are recommended for future implementation and validation.

## 8. Future Improvements

Potential improvements include:

- Create customer-managed KMS keys.
- Enable automatic key rotation where supported.
- Implement separate administrative and usage permissions.
- Configure encryption for centralized CloudTrail log storage.
- Integrate KMS with supported workload services.
- Review key policies periodically.
- Monitor key-related API activity through CloudTrail.
- Establish key deletion and recovery safeguards.

## 9. Conclusion

AWS KMS provides an important encryption and key-management layer within the FORTRESS architecture.

By combining customer-managed keys, controlled permissions, key rotation support, and CloudTrail monitoring, the proposed design improves data confidentiality and encryption governance.

---

**Project:** FORTRESS  
**Security Domain:** Encryption and Key Management  
**AWS Service:** AWS Key Management Service (KMS)