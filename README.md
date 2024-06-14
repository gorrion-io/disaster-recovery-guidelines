---
title: Gorrion Disaster Recovery Guidelines
revision: 0.0.1
update_date: 2024-06-13
---
# Gorrion Disaster Recovery Guidelines
## Identify the need of DR

To identify if the project needs Disaster Recovery Plan (DRP), you should consider the following:

1. **Business Impact Analysis (BIA)**
	1. **Revenue impact** - does the project directly generate revenue or support revenue-generating services?
	2. **Operational impact** - is the project critical to day-to-day operations and business processes?
	3. **Reputation impact** - does the project disruption impacts the client's reputation?
2. **Compliance** - does the project subject to regulations such as GDPR or HIPAA which mandate data protection and disaster recovery?
3. **Supply chain** - is the project part of a larger system or supply chain, where disruption could affect multiple components or services?
4. **State of the project** - is the project live on production and how many users are there?

**It should be a part of the agreement between a client ("Client") and Gorrion if, how and when should Gorrion create a DRP for Client.**

## Before you start

The first step of DRP should be a documentation for the project. The minimal accepted coverage is a maintenance documentation and an architectural diagram. Consider documenting the architectural decisions in the form of ADRs.

## 1. Risk assessment

1. Identify **critical systems and components**.
2. Determine the **potential impact of outages** on business operations.
3. Evaluate **risks and vulnerabilities** in the existing infrastructure.

## 2. Define Recovery Objectives

1. **Recovery Time Objective (RTO)** - maximum acceptable downtime.
2. **Recovery Point Objective (RPO)** - maximum period during which data loss is tolerable.

## 3. Form a Recovery Team (RT)

1. **Roles and Responsibilities** - assign clear roles within the project team for handling disaster recovery.
2. **Team Members** - include developers, DevOps (or solution architects, or internal Gorrion consultants), project managers, and key stakeholders.

## 4. Define backup strategy and restore procedures

1. **AWS Backup** - create a AWS Backup plans and document them.
2. **Restore procedures** - create restore procedures, document them and test regularly.
3. **Backup testing** - regularly test backup integrity.
4. **Redundancy** - ensure backups are redundant, stored off-site, and encrypted.

## 5. Infrastructure-as-a-code

1. **Use IaaC** - the infrastructure for the project should be defined as code.
2. **Documentation** - process of bringing up, bringing down and updating the infrastructure should be documented.

## 6. High Availability (HA) and Redundancy

1. **Redundant components** - design systems with redundancy by using AWS services like EC2 Auto Scaling, ELB, and multi-AZ deployments for databases.
2. **Load balancing** - distribute traffic evenly.
3. **Stateless architecture** - implement stateless architecture where possible.

## 7. Disaster Recovery (DR) Site

1. **Secondary Site** - set up a secondary DR site in a different AWS region if required.
2. **Data Replication** - use Amazon RDS Multi-AZ or AWS DMS for database replication to the DR site.

## 8. Monitoring and Alerting

1. **Monitoring Tools** - implement AWS CloudWatch and custom logging solutions.
2. **Alert Thresholds** - set thresholds for key metrics and ensure alerts are properly configured to notify the team.

## 9. Regular Testing and Drills

1. Simulated Drills: Conduct scheduled disaster recovery drills to validate the recovery process.
2. Documentation Update: Post-drill, update documentation based on findings to improve recovery strategies.

## 10. Comprehensive Documentation

1. **Disaster Recovery Plan** - detail the step-by-step recovery procedures specific to this project.
2. **Contact Information** - maintain up-to-date contact info for the recovery team and stakeholders.

## 11. Security Measures

1. **Data Encryption** - ensure all data (in transit and at rest) is encrypted using tools like AWS KMS.
2. **Access Controls** - restrict access to critical systems and data based on least privilege principles.

## 12. Communication Plan

1. **Internal Communication** - establish protocols for internal team communication during a disaster.
2. **External Updates** - prepare templates for notifying external stakeholders about the status and recovery progress.

## 13. Data Synchronisation

1. **Tools** - use AWS Database Migration Service (DMS) or other tools for real-time data synchronisation.
2. **Consistency Checks** - ensure transactional consistency between primary and DR sites.

## 14. Third-Party Dependencies

1. **Service SLAs** - review and document Service Level Agreements (SLAs) with critical third-party service providers.
2. **Fallback Plans** - prepare backup plans for third-party services that are critical to the project.

## 15. Cost Management

1. **Budgeting** - monitor and optimise disaster recovery-related expenses using AWS Cost Explorer.
2. **Cost-effective Measures** - implement affordable solutions that do not compromise recovery objectives.

## 16. Post-Disaster Review
1. **Incident Analysis** - after any disaster, perform a detailed review of the incident response.
2. **Plan Update** - update the disaster recovery plan based on lessons learned and new insights gained.
