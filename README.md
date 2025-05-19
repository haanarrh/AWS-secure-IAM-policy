# AWS-secure-IAM-policy
### Implementing IAM best practices in AWS for CloutLead
Designing a basic but secure IAM structure for a fictional company called CloutLead, following the principle of least privilege and AWS best practices.
CloutLead is a startup that designs, deploys, and manages cloud computing services for businesses in Nigeria,
aiming to deliver scalable, secure, and cost-effective cloud solutions that accelerate digital transformation.

### Defined IAM Roles for Cloutlead
| **Role**             | **IAM Group**      | **Description**                                                                | **Example Permissions**                                    |
| -------------------- | ------------------ | ------------------------------------------------------------------------------ | ---------------------------------------------------------- |
| **Cloud Admin**      | `Admins`           | Oversees all AWS services. Full control over cloud resources and IAM.          | `AdministratorAccess` (AWS managed policy)                 |
| **DevOps Engineer**  | `DevOpsEngineers`  | Manages infrastructure (EC2, VPC, S3, Lambda, etc.), but not IAM users/groups. | Custom policy with `EC2`, `S3`, `Lambda`, `CloudWatch`     |
| **App Developer**    | `Developers`       | Deploys and manages application code. Needs access to Lambda, S3, etc.         | Custom policy with `Lambda`, `API Gateway`, `S3` (limited) |
| **Security Analyst** | `SecurityTeam`     | Monitors logs, reviews audit trails, and enforces security policies.           | Read-only on CloudTrail, GuardDuty, IAM logs               |
| **Data Analyst**     | `ReadOnlyAnalysts` | Analyzes data, reviews metrics and dashboards. No access to edit.              | `ReadOnlyAccess` (AWS managed policy)                      |
| **Billing Manager**  | `BillingTeam`      | Manages billing and budgets, but no access to AWS services.                    | `AWSBillingReadOnlyAccess`                                 |

### Defined IAM users
| **Username**     | **Group**          | **Purpose**                       |
| ---------------- | ------------------ | --------------------------------- |
| `Lola.admin`     | `Admins`           | Super admin, full access          |
| `muna.devops`    | `DevOpsEngineers`  | Deploys servers, manages network  |
| `Tobi.dev`       | `Developers`       | Works on application code         |
| `chika.security` | `SecurityTeam`     | Reviews logs and security alerts  |
| `wale.analyst`   | `ReadOnlyAnalysts` | Analyzes metrics and dashboards   |
| `ife.billing`    | `BillingTeam`      | Monitors cost reports and budgets |

### Security Features Applied

  - Enforced MFA for all users

  - Password policy: min 12 characters, includes numbers & symbols

   -  Root account not used (only for emergencies)

  -  No direct policy attachment to individual users

   - CloudTrail enabled (optional but recommended)


