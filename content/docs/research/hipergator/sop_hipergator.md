---
title: "Standard Operating Procedure: HiPerGator"
summary: "Standard Operating Procedure for accessing and utilizing HiPerGator in the Biomedical Informatics Lab under Dr. Mei Liu."
weight: 7
---


This SOP outlines the procedures for accessing and utilizing the HiPerGator supercomputer resources by members of the Biomedical Informatics Lab under Dr. Mei Liu.
Applicable to all lab members, including postdocs, doctoral students, data scientists, master’s students, and temporary research assistants.

## Account Overview
- **Group Faculty Sponsor**: Dr. Mei Liu
- **Access**: Each member is granted individual access credentials which must be used in accordance with university policies, this SOP, and the [UF HOBI HiPerGator Usage Guidelines](https://github.com/uf-hobi-informatics-lab/hipergator_use_guideline/).

## Directory Structure and Usage

For detailed information on the directory structure and usage, please refer to the [HiPerGator Storage](/docs/research/hipergator/hipergator_storage/)  page and the [HiPerGator QOS](/docs/research/hipergator/hipergator_qos/)  page.

- **Home Directory (/home/user_name)**
  - **Purpose**: For storing software builds, conda environments, configuration files, and scripts.
  - **Access**: Private to each member.
  - **Space Limitation**: Storage space in this directory is limited. Do not store datasets here.

- **Blue Directory (/mei.liu/blue/user_name)**
  - **Purpose**: For active research projects and fast-access data storage needs.
  - **Access**: Shared among all group members by default.
  - **Usage**: Store actively used data and project files in this directory. Ideal for data requiring high-speed access.

- **Orange Directory (/mei.liu/orange/user_name)**
  - **Purpose**: For backups and less frequently accessed data.
  - **Access**: Shared among all group members by default.
  - **Usage**: Use this directory for backing up important files and storing large data not regularly accessed. Do not use it for data-intensive operations.


## Access and Security
For detailed information on how to set up the HiPerGator account, please refer to the [HiPerGator Setup Guide](/docs/research/hipergator/hipergator_gettingstarted/).

- **Requesting Access**: New account access can be requested through the [Request HiPerGator Account](https://www.rc.ufl.edu/access/account-request/) link. Additionally, send an email to the lab admin to coordinate with the faculty sponsor for approval of your request.
- **Credentials**: Use your UF credentials to access HiPerGator. Do not share your login information with others.
- **Data Security**: All restricted data must be stored on HiPerGator. Members should not download non-aggregated data onto personal or work devices to ensure data security. Please refer to the [UF Data Classification Guidelines](https://policy.ufl.edu/policy/data-classification-policy/) to determine the sensitivity level of the data.

## Data Management

- **File Organization**: Maintain a clear directory structure and naming convention for files and folders to ensure easy access and collaboration. For more details, see the [Coding Guidelines](/docs/research/git_github/coding_guidelines/).
- **Data Transfer**: Use secure data transfer methods such as SFTP or SSH for transferring data to and from HiPerGator. For more details, see the [HiPerGator Setup Guide](/docs/research/hipergator/hipergator_gettingstarted/).
- **Regular Backups**: Schedule regular backups for important data—whether raw data or data that need to be "frozen" as a reference point—to the Orange Directory to prevent data loss.

## Resource Utilization
- **Job Scheduling**: Utilize the SLURM scheduler for running computational tasks. Ensure that jobs are correctly prioritized and do not unnecessarily consume resources. For jobs that require extra resources, follow the departmental coordination policies detailed in the [HiPerGator QOS](/docs/research/hipergator/hipergator_qos/) page. For more information on SLURM, please refer to the [HiPerGator SLURM Guide](/docs/research/hipergator/hipergator_scheduler/).
- **Monitoring Usage**: Regularly monitor your data storage and compute usage. Stay within assigned quotas for our group (see [HiPerGator QOS](/docs/research/hipergator/hipergator_qos/) for allocated quotas) unless additional resources are approved. Methods for managing usage can be found on the [HiPerGator QOS](/docs/research/hipergator/hipergator_qos/) page.

## Compliance and Etiquette
- **Network Requirements**: Access to HiPerGator must be done via the UF Health network or secure VPN. For details, see [UF Health Networks](/docs/research/wifi_network/) and [UF Health VPN](/docs/research/vpn/).
- **Resource Usage and Reporting Issues**: Follow the [UF HOBI HiPerGator guidelines](https://github.com/uf-hobi-informatics-lab/hipergator_use_guideline/) and [HiPerGator QoS](/docs/research/hipergator/hipergator_qos/) for resource usage. Report any issues promptly to ensure efficient resolution and compliance with lab policies.
  
## Training and Support
- **Training Sessions**:
  - **External Training**: The UFRC provides training courses on HiPerGator usage. You can access these courses at [HiPerGator Training](https://www.coursera.org/groups/hipergator-account-training-ywszh/invitation).
  - **Internal Training**: Additional training sessions are available upon request from our data scientists. These sessions offer tailored guidance and answers to specific queries.

- **Support**: If you encounter issues that require more direct or immediate assistance, please reach out to the [UFIT RC Support System](https://www.rc.ufl.edu/get-support/).


## Integrating GitHub with HiPerGator
- **Code Management**: Members should refer to the [GitHub SOP](/docs/research/git_github/sop_github/) for detailed instructions on using Git on HiPerGator and processes related to sharing code with our lab's GitHub account.
- **Collaborative Workflow**: For a comprehensive guide on integrating HiPerGator, personal GitHub accounts, and the lab GitHub account, refer to our [Git Workflow Guidelines](/docs/research/git_github/git_workflow/).
  
## Review and Amendments
- **SOP Review**:The SOP will be reviewed annually or as necessary to adapt to changes in technology, university policies, or lab requirements.
- **Feedback and Changes**: We encourage all team members to provide feedback on the SOP. All proposed amendments will be reviewed by the admins, and changes will be implemented based on consensus and alignment with lab goals and policies.
