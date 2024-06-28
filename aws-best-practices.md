# AWS Best Practices

## Overall

- Always use the latest version of AWS services and SDKs.
- Always use Infrastructure as Code (IaC) tools like Pulumi, CloudFormation, Terraform to manage your infrastructure.
- Document your infrastructure using diagrams and docs.
- Always use CloudTrail to log all API calls and monitor user activity.
- Tag all resources with meaningful tags to track cost and usage. Especially, use tags to identify resources by environment (staging, dev, uat, prod) to track costs and usage.
- When considering project architecture, always consider the 5 pillars of the AWS Well-Architected Framework: Operational Excellence, Security, Reliability, Performance Efficiency, and Cost Optimization. If your project needs incorporating security frameworks like GDPR, HIPAA, PCI DSS, etc., make sure to follow the guidelines.
- Remember that you can use AWS Trusted Advisor to get recommendations on cost optimization, security, fault tolerance, and performance.
- Remember that you can use AWS Personal Health Dashboard to get alerts and remediation guidance when AWS is experiencing events that may impact you.
- Remember that you can use AWS Well-Architected Tool to review your architecture and get recommendations on how to improve it.


## IAM 

- Use root user account only for initial setup and account management tasks.
- Require MFA for all IAM users.
- Use groups over setting permissions for individual users.
- Utilize IAM roles to provide temporary security credentials for accessing critical AWS resources.

## Budgets

- ALWAYS configure Budgets. Prepare budget with realistic expectations of the cost incurred by the infrastructure in a given time frame, according to the project at hand.
- Make sure to set budget alerts to multiple email contacts to maximize chances of notifying the team about any cost anomalies.

## S3

- Use Cross-Region Replication (CRR) or Same-Region Replication (SRR)
- Make sure S3 buckets are not publicly accessible unless necessary
- Enable MFA Delete to prevent deletion of files without an MFA
- Generate S3 file keys on the server-side rather than allowing them to be generated or set on the client-side to enhance security.
- Validate the file type of uploads. Allow only the file extensions and files that are allowed by your system. If needed, be extra careful when allowing uploading html and xmls files, they can expose app to cross site scripting attacks.
- Always check if the file uploaded is not overriding any other uploaded files.
- If large volumes of data are stored in S3, consider using S3 Intelligent-Tiering to automatically move objects between two access tiers based on changing access patterns or use lifecycle policies to move objects to lower-cost storage classes.

## VPC

- Place sensitive resources like databases, APIs, backend systems in private subnets to prevent direct access from internet.
- Separate environments (staging, dev, uat, prod) in different subnets, separated from each other.
- Leverage Gateway Endpoints to communicate between private resources and S3 to mitigate ingress/egress costs and enhance security.
- Choose appropriate CIDR blocks to leave extra room for any additional subnets and IP addresses.


## EC2

- Avoid using default security groups. Always create custom security groups with custom rules.
- Restrict inbound and outbound traffic to only necessary ports and IP addresses.
- Use IAM roles to grant EC2 instances access to AWS services.
- Use instance store volumes ONLY for temporary data.
- Use separate EBS volumes for operating system and data to make it easier to manage, scale and ensure data persistence.
- Regularly backup EBS volumes using snapshots.


## RDS 

- Enable encryption at rest using AWS Key Management Service (KMS) for your RDS databases.
- Enforce TLS encryption for all database connections to protect data in transit.
- Deploy RDS instances within a VPC for private network access and restrict inbound traffic using security groups.
- NEVER store sensitive information like passwords, API keys, etc. in plain text in RDS databases.
- NEVER deploy RDS instances in public subnets.
- Enable CloudTrail logging for all RDS API calls to track user activity and detect suspicious actions.
- Remember that you can use tools like Amazon RDS Performance Insights to analyze query performance and identify bottlenecks.
- Regularly take manual and ensure that snapshots are encrypted.
- Enable automated backups and set the backup window to occur during periods of low WriteIOPS.
- Consider Multi-AZ deployments for high availability and fault tolerance.
- Consider using read replicas to offload read traffic from the primary database and improve read performance.
- Monitor RDS instances using Amazon CloudWatch Metrics and Amazon CloudWatch Logs to identify performance issues and bottlenecks.


## Lambda 

- Use environment variables to store sensitive information like passwords, API keys, etc. NEVER hardcode them in your Lambda functions. Use AWS Secrets Manager or AWS Systems Manager Parameter Store to store and retrieve secrets.
- Use the most restrictive permissions when setting IAM policies for Lambda functions. Limit the execution role to only the resources and operations your functions need.
- To optimize cold start times, consider using provisioned concurrency, using languages that have faster cold start times like JavaScript, Python or Go, and reducing the size of your deployment package.
- Monitor your Lambda functions using Amazon CloudWatch Logs, Amazon CloudWatch Metrics, and AWS X-Ray to identify performance issues and bottlenecks.
- Ensure that Lambdas are completely stateless and do not store any data between invocations. Remember that the local file system is not persistent between invocations and should not be used to store data.