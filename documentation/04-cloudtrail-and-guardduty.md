# FORTRESS — CloudTrail and GuardDuty Security Monitoring

## 1. Introduction

FORTRESS incorporates AWS CloudTrail and Amazon GuardDuty as key components of its security monitoring architecture.

These services provide visibility into AWS account activities and help identify potentially malicious behavior.

CloudTrail focuses on recording AWS API activity, while GuardDuty focuses on detecting potential security threats.

Together, they support security auditing, threat visibility, and incident investigation.

## 2. AWS CloudTrail

### 2.1 Purpose

AWS CloudTrail records activities performed within an AWS account.

It provides event history that can help administrators understand who performed an action, what action was performed, and when it occurred.

### 2.2 FORTRESS Configuration

The project includes:

`cloudtrail/CloudTrailConfig.json`

The configuration contains the following settings:

| Configuration | Value | Purpose |
|---|---|---|
| TrailName | FORTRESS-Centralized-Audit-Trail | Identifies the audit trail |
| IsMultiRegionTrail | true | Covers supported AWS regions |
| IncludeGlobalServiceEvents | true | Includes global service events |
| EnableLogFileValidation | true | Enables log integrity validation |
| IsOrganizationTrail | true | Specifies