# 🛡️ AWS Config Rule CI/CD Deployment Pipeline (GRC Engineering)
![Deploy Workflow](https://github.com/Runc9/aws-config-rule-cicd-for-multi-region-grc/actions/workflows/config-rule-deploy.yml/badge.svg)

## 1. 🧠 Overview

> Imagine your organization must enforce IAM password policy compliance across all AWS environments — but manual rule creation won’t scale, and audit fatigue is growing.

As a GRC Engineer, your mission is to:
- Convert security policy into an automated AWS Config rule
- Deploy it via CloudFormation through GitHub Actions
- Ensure changes are tracked, tested, and enforced as code

This project builds a real-world **Compliance-as-Code pipeline** that deploys managed AWS Config rules based on Git commits — traceable, testable, and auditable.
## 2. 🧩 Architecture Diagram

![Architecture](architecture.png)
## 3. 🎯 Lab Objectives

- ✅ Define a managed AWS Config rule (IAM_PASSWORD_POLICY)
- ✅ Convert it into JSON format with tagging metadata
- ✅ Write a CloudFormation template for reusable deployments
- ✅ Configure GitHub Actions to validate + deploy rules on push
- ✅ Store AWS credentials securely using GitHub Secrets
## 4. 🗂️ Project Structure

```bash
.
├── config-rules/
│   └── cis-1-4-1-iam-password-policy.json
├── templates/
│   └── config-rule-template.yaml
├── .github/
│   └── workflows/
│       └── config-rule-deploy.yml
├── architecture.png
└── README.md
## 5. ⚙️ How It Works

- All AWS Config rules are defined as `.json` files inside `config-rules/`
- Rules are deployed via `templates/config-rule-template.yaml`
- On every Git push to `config-rules/` or `templates/`, GitHub Actions:
  - Validates syntax
  - Loads AWS credentials from `Secrets`
  - Runs `aws cloudformation deploy` to apply the rule
## 6. 🚀 CI/CD Pipeline (GitHub Actions)

| Stage                     | Description                             |
|---------------------------|-----------------------------------------|
| `Checkout`                | Fetches code from GitHub repo           |
| `Configure AWS Credentials` | Loads from `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` |
| `CloudFormation Deploy`   | Applies the latest Config rule via CLI  |
## 7. 🧠 Skills Demonstrated

- AWS Config (managed rule deployment)
- CloudFormation (parameterized infrastructure as code)
- GitHub Actions (automated CI/CD pipelines)
- Secrets management with GitHub
- Compliance-as-Code (GRC automation workflows)
- IAM and Security Governance
## 8. 📚 Resources

- [AWS Config Documentation](https://docs.aws.amazon.com/config/latest/developerguide/)
- [IAM Password Policy Rule (AWS Managed)](https://docs.aws.amazon.com/config/latest/developerguide/iam-password-policy.html)
- [CloudFormation Resource Types](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
- [GitHub Actions AWS CLI Setup](https://github.com/aws-actions/configure-aws-credentials)
- [CIS AWS Foundations Benchmark](https://www.cisecurity.org/benchmark/amazon_web_services)
