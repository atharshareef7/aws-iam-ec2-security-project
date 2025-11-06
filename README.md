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
### 📸 Screenshots

**1. AWS Account Alias Creation**
![Account Alias Creation](images/account_alias_creation.png)


**2. Development Instance Tagging**
![Development Instance Tags](images/tags_development_instance.png)


**3. Production Instance Tagging**
![Production Instance Tags](images/tags_production_instance.png)


**4. IAM Policy JSON**
![IAM Policy JSON](images/iam_policy_json.png)


**5. IAM User Creation**
![IAM User Creation](images/user_creation_console.png)


**6. Production Instance Stop Attempt (Access Denied)**
![Prod Access Denied](images/production_access_denied.png)


**7. Development Instance Stopped (Access Allowed)**
![Dev Instance Stopped](images/dev_instance_stopped.png)


---

## Learnings
- Implemented least privilege with tag-based policies  
- Verified policy behavior using the IAM Policy Simulator  
- Separated dev and prod access to prevent accidental changes

---

## License
This project is licensed under the MIT License. See `LICENSE` for details.

---
