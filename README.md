# 🛡️ Compliance-Aware Multi-Region AWS Config Deployment Pipeline

> 🎯 **Scenario**: You're a GRC engineer managing 100+ AWS accounts across 3+ regions. You need to enforce CIS, NIST, and ISO compliance — not manually, but through automated Config rules as code. This repo shows you how.

![Framework: NIST 800-53](https://img.shields.io/badge/NIST-800--53-blue)
![CIS Benchmarks](https://img.shields.io/badge/CIS-v8-green)
![Status](https://img.shields.io/badge/Deployment-MultiRegion-orange)
![Type](https://img.shields.io/badge/GRC--Engineering-Project-critical)

---

## 🔧 What This Does

- ✅ Deploys **AWS Config rules** to multiple AWS accounts and regions
- ✅ Combines **managed + custom** rules (JSON/YAML or Rego)
- ✅ Uses **deploymentTargets** (like in Landing Zone Accelerator) to define scope
- ✅ Reports findings to **Security Hub**

---

## 📁 Project Structure

```bash
aws-config-rule-cicd-for-multi-region-grc/
├── config-rules/           # Rule definitions (JSON/YAML)
├── templates/              # CloudFormation/CDK stacks
├── pipelines/              # CI/CD logic
└── .github/workflows/      # GitHub Action to deploy rules
---

## 🧭 Architecture

This pipeline uses GitHub Actions (or CodePipeline) to deploy AWS Config rules across multiple accounts and regions using Infrastructure-as-Code. It supports both AWS-managed rules and custom ones defined in JSON, YAML, or Rego.

### 🔄 Flow Summary:

1. **Developer commits Config rule definition(s)** to the `config-rules/` folder
2. **GitHub Action pipeline** is triggered
3. CI/CD logic parses a `deploymentTargets.yaml` file to map accounts and regions
4. For each target:
   - Deploys AWS Config rules via CloudFormation (or CDK)
   - Tags each rule with compliance mappings (e.g., NIST, CIS)
   - Publishes findings to Security Hub in central Audit account

### 📊 Visual Architecture Diagram

📌 ![Multi-Account Config Deployment](./architecture.png)

