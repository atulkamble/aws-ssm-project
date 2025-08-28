```
sudo yum install -y amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
sudo systemctl start amazon-ssm-agent
```

full **AWS Systems Manager (SSM) practice project** to the canvas — Terraform code, custom SSM runbooks, Patch Manager (baseline + maintenance window), Inventory to S3, Parameter Store (String + SecureString), CloudWatch Agent association, smoke-test scripts, plus optional GitHub Actions and a Jenkinsfile.

### How to run (quick)

1. In the `terraform/` folder:

```bash
terraform init
terraform apply -auto-approve \
  -var "region=ap-south-1" \
  -var "project=cloudnautic-ssm" \
  -var "db_password=ChangeMe#2025"
```

2. Start a Session Manager shell:

```bash
aws ssm start-session --target $(terraform output -raw instance_id) --region ap-south-1
```

3. (Optional) Run the smoke tests:

```bash
bash scripts/smoke_tests.sh
```

Want me to tailor it for **multi-AZ** + **private subnets with NAT**, or add **Hybrid Activations** to manage on-prem VMs too?
