# FORTRESS — AWS Organizations and Service Control Policies

## 1. Introduction

AWS Organizations is a service that allows organizations to centrally manage multiple AWS accounts.

FORTRESS uses a multi-account architecture to separate management, security monitoring, and workload environments.

Service Control Policies (SCPs) are used to establish organization-level permission restrictions.

## 2. Security Objectives

The proposed implementation aims to:

- Establish centralized account governance.
- Separate management and workload environments.
- Apply consistent security restrictions.
- Prevent unauthorized disabling of audit logging.
- Reduce the risk of organization-wide security misconfigurations.

## 3. Proposed Multi-Account Structure

| Account | Responsibility |
|---|---|
| Management Account | AWS Organizations and governance |
| Security Account | Centralized security monitoring |
| Workload Account | Application infrastructure |

Separating these responsibilities helps isolate administrative functions and security monitoring from application workloads.

## 4. Service Control Policies

An SCP defines the maximum available permissions for IAM users and roles within affected member accounts.

An SCP does not grant permissions. IAM policies must still grant the requested actions.

## 5. Implemented Policy Example

FORTRESS includes:

`ProtectCloudTrailSCP.json`

The policy explicitly denies the following actions:

| Action | Purpose |
|---|---|
| cloudtrail:StopLogging | Prevent stopping CloudTrail logging |
| cloudtrail:DeleteTrail | Prevent deleting a CloudTrail trail |
| cloudtrail:UpdateTrail | Prevent modifying trail configurations |

### Policy Effect

The policy uses:

- Effect: Deny
- Action: CloudTrail management actions
- Resource: *

The explicit Deny takes precedence over an Allow within the applicable SCP and IAM permission evaluation.

## 6. IAM Policy vs SCP

| IAM Policy | SCP |
|---|---|
| Grants or denies permissions | Sets maximum available permissions |
| Attached to IAM identities or resources | Applied through AWS Organizations |
| Controls access to AWS services | Restricts permissions across member accounts |
| Does not override an explicit Deny | Does not grant permissions |

## 7. Security Benefits

- Centralized governance.
- Consistent security restrictions.
- Reduced risk of unauthorized changes.
- Improved control over member accounts.
- Better separation of organizational responsibilities.

## 8. Important Limitations

SCPs do not restrict actions performed by users or roles in the AWS Organizations management account.

They also do not grant permissions or replace IAM policies.

The current FORTRESS SCP is an example configuration and has not yet been deployed or tested in a live AWS Organization.

## 9. Future Improvements

- Deploy the SCP in a test AWS Organization.
- Create organizational units for different workloads.
- Apply SCPs to appropriate member accounts.
- Test permitted and denied actions.
- Develop additional restrictions for security-sensitive services.

## 10. Conclusion

AWS Organizations and SCPs provide an important governance layer in the FORTRESS architecture.

By establishing centralized permission boundaries, organizations can reduce security risks and maintain more consistent controls across multiple AWS accounts.

---

**Project:** FORTRESS  
**Security Domain:** Cloud Governance  
**AWS Services:** AWS Organizations and Service Control Policies