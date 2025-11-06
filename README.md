# AWS IAM & EC2 Security Project

**Author:** MOHAMMAD ATHAR SHAREEF

**Purpose:** Demonstrate environment-based access control in AWS using IAM policies, EC2, and resource tagging.

---

## Project Overview
This project shows how to:
- Launch EC2 instances for **production** and **development**
- Create an IAM policy that grants EC2 actions only for instances tagged `Env=development`
- Create IAM group and user, attach the policy, and verify access via IAM Policy Simulator and console tests

---

## Architecture & Services Used
- Amazon EC2 (compute instances)
- AWS IAM (policies, users, groups)
- IAM Policy Simulator (testing)
- AWS Account Alias (friendly sign-in URL)

---

## Files in this Repo
- `policy/NextWorkDevEnvironmentPolicy.json` — IAM policy used in this project  
- `images/` — screenshots from the AWS Console  
- `report/AWS-IAM-EC2-Project-Report.pdf` — (optional) downloadable report  
- `README.md` — this file

---

## Policy (summary)
The policy allows `ec2:*` for resources tagged `Env=development`, allows `ec2:Describe*` globally, and denies tag edits (`ec2:CreateTags`, `ec2:DeleteTags`).

Example policy JSON is in `policy/NextWorkDevEnvironmentPolicy.json`.

---

## How to Reproduce
1. Create two EC2 instances and tag them:
   - `Env=production` (name: `nextwork-prod-...`)
   - `Env=development` (name: `nextwork-dev-...`)
2. Create IAM policy from the JSON in `policy/`
3. Create group `nextwork-dev-group`; attach the policy
4. Create user `nextwork-dev-...` and add to the group
5. Use the IAM Policy Simulator or login as the user to confirm:
   - Dev instance: start/stop allowed
   - Prod instance: start/stop denied

---

## Screenshots
![EC2 Instances](images/ec2_instances.png)
![IAM Policy JSON](images/iam_policy.png)
![Denied Production Action](images/denied_production.png)
![Allowed Development Action](images/allowed_development.png)

---

## Learnings
- Implemented least privilege with tag-based policies  
- Verified policy behavior using the IAM Policy Simulator  
- Separated dev and prod access to prevent accidental changes

---

## License
This project is licensed under the MIT License. See `LICENSE` for details.

---
