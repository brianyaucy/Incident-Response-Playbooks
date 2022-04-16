# 2022-04-17_IAMCompromise

## Attack Sequence

![AWS IAM Attack Sequence](images/be779917ec1f355d48b35640622833965d2bf7c4568a49ce32ff53be93c07cf2.png)  

## Detection Opportunities

1. Detect IAM activities from uncommon locations
2. Detect IAM User `ConsoleLogin` without MFA
3. Detect IAM User `ConsoleLogin` from uncommon locations
4. Detect sensitive IAM policy attachment (e.g. `AdministratorAccess`)
5. Detect IAM User or Access Key Creation (`iam:CreateUser` / `iam:CreateLoginProfile` / `iam:UpdateLoginProfile` / `iam:CreateAccessKey`)
6. Detect `RequestServiceQuotaIncrease` for potential impact

## Reference

### Expel.io Blog

[Incident report: From CLI to console, chasing an attacker in AWS](https://expel.com/blog/incident-report-from-cli-to-console-chasing-an-attacker-in-aws/)

### Expel.io AWS Mindmap

![picture 14](images/1cca8a99fbdc4a5ff4e032c4e8541cb082c6fcf0a8c648e9155f365543d30bdb.png)  