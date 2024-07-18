# Maintenance Documentation

# Maintenance documentation

# Environments

## Production environment 🟢

💡 This part of documentation should be written, after the first production deployment. It should be done after Production Readiness Checklist.

### Access

💡 In this part of docs you should include:

*   links to production deployment of app: frontend, backend, mobile stores,
*   links to Password Manager with access to the production deployments

## Staging environment 🟢

💡 This part of documentation should be written, after the first staging deployment, and kept updated throughout development process.

### Access

💡 In this part of docs you should include:

*   links to staging deployment of app: frontend, backend, database.
*   links to Password Manager with access to the staging deployments
*   access to app’s cloud provider and 3rd party services

  

⚠️ Other environments should also be included, if needed. 🟡

# Local development

### Tech stack 🟢

💡 List the technologies used, focus on the main list, keep it short.

### Setup 🟢

💡 In this section list all the necessary steps to run the app locally.

It should include:

*   prerequisites (e.g. Node.js version, package manager, Docker etc.) 🟢
*   environment variables description, the template should be included in repo 🟢
*   list of commands needed to run the project locally 🟢
*   list of commands to run tests 🟡

### Coding conventions 🟢

💡 This section can be copied from [README.md](http://README.md) and should include branching, coding, and naming conventions.

# Disaster recovery 🟡

💡 This section should be done when the development is slowing down and we only maintain the project from time to time.

It should include:

*   list of people with the Password Manager access 🟢
*   list of people with production environment access, especially to infrastructure 🟢
*   information about backups, including schedule, place where backups are stored and a way of restoring latest backup 🟢
*   steps to complete to shut down, start and restart the app in case of critical bugs 🟡

# Infrastructure 🟢

💡 This section should include information about infrastructure used in project.

It should contain information about:

*   hosting 🟢
*   database 🟢
*   additional services, including: email, notifications, queues, CRON jobs, schedules, serverless functions 🟢

The hosting should be divided into frontend and backend parts.

There should be a data flow diagram attached. 🟡

If IaaC solution has been used, it should be mentioned. 🟡

# Monitoring 🟡

💡 This section should include list and access to monitoring services, list of monitoring triggers and how they work.

Example services:

*   Sentry
*   CloudWatch Alarms
*   Grafana
*   Logtail
*   Axiom
*   Kibana
*   any other solutions

# DevOps 🟡

💡 In this section, there should be informations about:

*   project maintainers 🟢
*   CI jobs 🟢
*   manual triggers, e.g. how to trigger specific CI step, CRON jobs etc 🟡
*   manual deployment instructions 🟢
*   manual IaaC deployment 🟡

# Slack channels 🟢

💡 List the channels related to project and who to ask for the access.
