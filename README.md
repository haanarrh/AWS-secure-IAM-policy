# IMPLEMENTING IAM BEST PRACTICES IN AWS FOR CLOUTLEAD
## Overview
Designing a basic but secure IAM structure for a fictional company called CloutLead, following the principle of least privilege and AWS best practices.
CloutLead is a startup that designs, deploys, and manages cloud computing services for businesses in Nigeria,
aiming to deliver scalable, secure, and cost-effective cloud solutions that accelerate digital transformation.

### AWS Identity Access Management (IAM) Structure
#### Defined IAM users
Each IAM user is assigned to a group based on their role, to ensure permissions are logically managed and follow the principle of least privilege.

| **Username**     | **Group**          | **Purpose**                       |
| ---------------- | ------------------ | --------------------------------- |
| `Lola.admin`     | `Admins`           | Super admin, full access          |
| `muna.devops`    | `DevOpsEngineers`  | Deploys servers, manages network  |
| `Tobi.dev`       | `Developers`       | Works on application code         |
| `chika.security` | `SecurityTeam`     | Reviews logs and security alerts  |
| `wale.analyst`   | `ReadOnlyAnalysts` | Analyzes metrics and dashboards   |
| `ife.billing`    | `BillingTeam`      | Monitors cost reports and budgets |

![IAM users](https://github.com/user-attachments/assets/2d6766e2-e7b3-485c-b209-8b81483eb258)

### Defined IAM Roles for Cloutlead
| **Role**             | **IAM Group**      | **Description**                                                                | **Example Permissions**                                    |
| -------------------- | ------------------ | ------------------------------------------------------------------------------ | ---------------------------------------------------------- |
| **Cloud Admin**      | `Admins`           | Oversees all AWS services. Full control over cloud resources and IAM.          | `AdministratorAccess` (AWS managed policy)                 |
| **DevOps Engineer**  | `DevOpsEngineers`  | Manages infrastructure (EC2, VPC, S3, Lambda, etc.), but not IAM users/groups. | Custom policy with `EC2`, `S3`, `Lambda`, `CloudWatch`     |
| **App Developer**    | `Developers`       | Deploys and manages application code. Needs access to Lambda, S3, etc.         | Custom policy with `Lambda`, `API Gateway`, `S3` (limited) |
| **Security Analyst** | `SecurityTeam`     | Monitors logs, reviews audit trails, and enforces security policies.           | Read-only on CloudTrail, GuardDuty, IAM logs               |
| **Data Analyst**     | `ReadOnlyAnalysts` | Analyzes data, reviews metrics and dashboards. No access to edit.              | `ReadOnlyAccess` (AWS managed policy)                      |
| **Billing Manager**  | `BillingTeam`      | Manages billing and budgets, but no access to AWS services.                    | `AWSBillingReadOnlyAccess`                                 |

![IAM groups & roles](https://github.com/user-attachments/assets/95182520-34e0-4bf1-9f41-58cf301f7a1a)

### Security Features Applied

Multi-Factor Authentication (MFA) enforced for all IAM users

Strong password policy: minimum 12 characters with numbers, symbols, and uppercase

No use of root account, except for emergencies

No inline or user-attached policies; only group-attached managed/custom policies

CloudTrail enabled to monitor all IAM activities and log events (recommended)

### Lessons Learnt

- Planning IAM around roles makes it scalable and easier to manage.

- The principle of least privilege reduces risk exposure.

- MFA and password policies are your first line of defense.

- It's better to use groups and policies rather than assign permissions directly to users.

### Portfolio-Worthy Lab Ideas (for future expansion)

- Automate IAM user and group creation using a CloudFormation template

- Build a Python script using boto3 to rotate IAM credentials

- Create a custom IAM policy simulator to test least privilege

- Integrate IAM with AWS SSO and identity federation (e.g., Google Workspace)

### Additional Resources & Labs

- AWS IAM Best Practices

- IAM Workshop (Official AWS)

- FreeCodeCamp - IAM Beginner Lab

- AWS CloudQuest IAM Role-Based Game

