# CLOUD-AWS-IAM-001: Sensitive AWS IAM Policy Attachment

## Metadata

| **Use Cases Metadata** ||
| --- | --- |
| **UUID** | 3b86f7e4-27da-471d-b8c4-66452243b9ad |
| **Name** | Sensitive AWS IAM Policy Attachment |
| **Short Name** | CLOUD-AWS-IAM-001 |
| **Author** | Brian Yau |
| **Kill Chain** | Privilege Escalation |
| **ATT&CK** | Privilege Escalation |
| **References** | [Expel.io - Incident report: From CLI to console, chasing an attacker in AWS](https://expel.com/blog/incident-report-from-cli-to-console-chasing-an-attacker-in-aws/) |

## Goal

Detect sensitive AWS IAM policies attachment.

## Category

- [ ] Initial Access
- [ ] Lateral Movement
- [X] Privilege Escalation
- [ ] Hacking
- [ ] Malware
- [ ] Insider Threat
- [ ] Audit

## Priority

- [ ] Highest
- [x] High
- [ ] Medium
- [ ] Low

## Status

- [X] Experimental
- [ ] Functional
- [ ] Stable
- [ ] Retired

## Strategy Abstract

- Look for `iam:AttachUserPolicy` CloudTrail events with sensitive privileges. For example:
    - AdministratorAccess
    - IAMFullAccess
    - PowerUserAccess

## Technical Context

Adversaries may attempt to perform privilege escalation by attaching privileged policies to  compromised AWS IAM users or roles.

With enough permissions (for example, users or roles attached with either  `AdministratorAccess`,  `IAMFullAccess`,  `PowerUserAccess` policy), the adversaries can call `iam:AttachUserPolicy` to attach a high privilege policy like `AdministratorAccess`.

## Blind spots & Assumptions

- Assume CloudTrail is enable and searchable on SIEM

## False Positives

- Legit IAM activities

## Validation

- Test by calling `iam:AttachUserPolicy` to attach `AdministratorAccess` to an IAM user using AWS CLI
- Test by attach `AdministratorAccess` to an IAM user via AWS Console

## Response

- 
