## AWS Best Practices

#### IAM 

- Use root user account only for initial setup and account management tasks.
- Require MFA for all IAM users.
- If project requires increased level on security and retractability consider enabling CloudTrail to log all API calls
- Use groups over setting permissions for individual users.
- Utilize IAM roles to provide temporary security credentials for accessing critical AWS resources.

#### Budgets

- ALWAYS configure Budgets. Prepare budget with realistic expectations of the cost incurred by the infrastructure in a given time frame, according to the project at hand.
- Make sure to set budget alerts to multiple email contacts to maximize chances of notifying the team about any cost anomalies.

#### S3

- Use Cross-Region Replication (CRR) or Same-Region Replication (SRR)
- Make sure S3 buckets are not publicly accessible unless necessary
- Enable MFA Delete to prevent deletion of files without an MFA
- Set S3 file keys on the server and never let it generate on the Client
- Validate the file type of uploads. Allow only the file extensions and files that are allowed by your system. If needed, be extra careful when allowing uploading html and xmls files, they can expose app to cross site scripting attacks.
- Always check if the file uploaded is not overriding any other uploaded files.

#### VPC

- Place sensitive resources like databases, APIs, backend systems in private subnets to prevent direct access from internet.
- Separate environments (staging, dev, uat, prod) in different subnets, separated from each other.
- Leverage Gateway Endpoints to communicate between private resources and S3 to mitigate ingress/engress costs and enhance security
- Choose appropriate CIDR blocks to leave extra room for any additional subnets and IP addresses.

#### EC2 WIP

#### ECS WIP

#### RDS WIP

#### Lambda WIP

#### Other WIP