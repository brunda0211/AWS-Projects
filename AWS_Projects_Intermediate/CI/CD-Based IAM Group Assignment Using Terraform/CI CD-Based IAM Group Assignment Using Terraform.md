# 📁 CI/CD-Based IAM Group Assignment Using Terraform

## 🎯 Objective:
Simulate a real-world corporate setup where:
- IAM users and group memberships are managed using Terraform
- Changes are made through Git, Pull Requests, and CI/CD pipelines
- A ticket-based task is resolved by editing shared Terraform files

---

## 🛠️ Project Structure:
```
terraform-iam-project/
├── main.tf                # Root provider config
├── iam/
│   ├── users.tf           # IAM users
│   ├── groups.tf          # IAM groups
│   └── memberships.tf     # IAM user-group memberships
```

---

## 🔹 Step 1: Provider Setup (`main.tf`)
```hcl
provider "aws" {
  region = "us-west-2"
}
```

---

## 🔹 Step 2: Create IAM User (`iam/users.tf`)
```hcl
resource "aws_iam_user" "alice" {
  name = "alice.dev"
  tags = {
    Role = "Developer"
  }
}
```

---

## 🔹 Step 3: Create IAM Group (`iam/groups.tf`)
```hcl
resource "aws_iam_group" "s3_admins" {
  name = "S3Admins"
}
```

---

## 🔹 Step 4: Add User to Group (`iam/memberships.tf`)
```hcl
resource "aws_iam_user_group_membership" "alice_to_s3admins" {
  user   = aws_iam_user.alice.name
  groups = [aws_iam_group.s3_admins.name]
}
```

---

## 🎟️ Ticket-Based Task Simulation

### Ticket:
_“Add IAM user `john.dev` to group `S3Admins` using Terraform.”_

### Developer Workflow:

1. **📥 Pull Latest Code**
   ```bash
   git clone https://github.com/org/terraform-iam-project.git
   cd terraform-iam-project
   git pull origin main
   ```

2. **🌿 Create Feature Branch**
   ```bash
   git checkout -b feature/add-john-to-s3admins
   ```

3. **📝 Edit `memberships.tf`**
   Add the following:
   ```hcl
   resource "aws_iam_user" "john" {
     name = "john.dev"
   }

   resource "aws_iam_user_group_membership" "john_to_s3admins" {
     user   = aws_iam_user.john.name
     groups = ["S3Admins"]
   }
   ```

4. **🧪 Run Terraform Plan (Locally)**
   ```bash
   terraform init
   terraform plan
   ```

5. **📤 Commit and Push Changes**
   ```bash
   git add .
   git commit -m "Add john.dev to S3Admins group"
   git push origin feature/add-john-to-s3admins
   ```

6. **🔀 Open Pull Request**
   - Go to GitHub
   - Create PR: `feature/add-john-to-s3admins` → `main`
   - Reference the ticket in the PR description

7. **✅ Code Review and Approval**
   - Team lead reviews and approves
   - PR is merged into `main`

8. **🚀 CI/CD Pipeline Runs**
   Automatically runs:
   ```bash
   terraform init
   terraform plan
   terraform apply -auto-approve
   ```

   *Tools: GitHub Actions, GitLab CI, Jenkins, etc.*

9. **🎉 Ticket Closed**
   - PR link added to ticket
   - Status marked "Done"

---

## 🧹 Clean Up (Optional)
For local testing:
```bash
terraform destroy
```

---

## 💡 Notes
- Never apply Terraform changes directly to `main`
- Use branches and PRs for traceability
- Apply actions should run via CI/CD only
- In production, use remote state (e.g., S3 + DynamoDB locking)
