# Week 0 — Billing and Architecture

### AWS CLI
Installed the AWS CLI and updated the gitpod.yml with the following commands.
```
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```
Created an IAM User, generated AWS credentials, and set the env variables.

### Billing
Enabled billing alerts, created a SNS topic, and created a billing alarm.

### Budgets
Created a budget with the following code.
```
aws sts get-caller-identity --query Account --output text

aws budgets create-budget \
    --account-id AccountID \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json
```
