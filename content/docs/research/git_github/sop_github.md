---
title: "Standard Operating Procedures: GitHub"
summary: "Standard Operating Procedures for using the Gator-AIM GitHub group account managed by Dr. Mei Liu’s Lab Group."
weight: 4
---

This SOP outlines procedures for accessing and utilizing the GitHub Group account (Gator-AIM) by members of the Biomedical Informatics Lab under Dr. Mei Liu. It applies to all lab members, including doctoral students, data scientists, master's students, postdocs, temporary research assistants, and outside collaborators. These procedures ensure effective collaboration, data security, and proper management of our projects and research outputs.

## Lab GitHub Account Overview
The lab GitHub account is managed by lab admins (Professor, Data Scientists) for version control and collaboration on various research projects. Roles and access levels are designated primarily at the repository level, allowing for tailored permissions based on individual projects and team needs. Here's an overview of typical roles and their access permissions:

- **Admins (Professor, Data Scientists)**: Full access across all repositories, including user management and repository settings adjustments. Admins can create new repositories and assign roles to team members as required for specific projects.

- **Maintainers (Postdocs, Doctorate Students)**: Assigned on a per-repository basis, maintainers manage branches and merge pull requests within their specific projects. This role allows them to ensure that changes and updates align with project goals without impacting other lab activities.

- **Contributors (Master Students, Graduate Research Assistants, Volunteers)**: Also designated at the repository level, contributors can push changes to specific branches and manage issues within the projects they are involved in. This role is critical for day-to-day development tasks and iterative improvements.

- **Read-Only (Outside Collaborators)**: Have the ability to view and clone repositories but cannot make direct changes. This access is typically granted to external partners or collaborators who need insight into the project but do not directly contribute to the codebase.

## Access and Permissions
- **Requesting Access**: New members must contact lab admins with their GitHub username and a brief role description.
- **Granting Access**: Access is granted by the lab admins. Upon approval, admins will assign access levels based on the member’s role and project involvement.
- **Git Setup**: Please refer to the [Git Setup Guide](/docs/research/git_github/git_gettingstarted/) for instructions on setting up Git on HiPerGator and connecting it to GitHub.

## Usage Procedures
Effective use of our GitHub resources requires adherence to the following established procedures:

- **Repository Setup**: Admins or maintainers are responsible for creating repositories. This includes setting up the repository with appropriate naming conventions and access settings to ensure consistency and security.

- **Branch Management**: Utilize branches to manage different stages of development. Specific branches should be used for developing features, and the main/master branches should be kept protected to maintain the integrity of the released or production-ready code.

- **Code Reviews**: To maintain high code quality and ensure data security, all pull requests must be reviewed by at least one maintainer before merging. This review process not only helps catch errors and enforce coding standards but also checks for potential data security issues, such as unintended inclusion of sensitive data in the codebase.
  
- **Issue Tracking**: Use GitHub issues to track bugs, feature requests, and other tasks. This ensures that all team members are aware of ongoing problems and developments.

- **Collaborative Workflow**: For a detailed guide on integrating the HiPerGator, personal GitHub accounts, and the lab GitHub account, refer to our workflow guide in [Git Workflow Guidelines](/docs/research/git_github/git_workflow/).


## Collaboration and Communication
Effective collaboration and clear communication are foundational to the success of our projects. Here’s how we use our key communication tools:

- **Task Management with Asana**: Asana is our primary platform for managing tasks and project workflows. For detailed guidelines on how to use Asana effectively within our projects, please refer to the [Asana Guidelines](/docs/research/asana/).

- **Daily Communication**: We use Microsoft Teams and email for our daily communications. Teams is utilized for instant messaging, quick updates, discussions, and collaborative sessions, serving as our main channel for day-to-day communication. Email is reserved for more formal communications, sharing official documents, and longer discussions that require a formal record.

- **Regular Updates**: Commit changes regularly with descriptive messages and keep GitHub issues and pull requests updated. This includes reviewing pull requests, discussing issues, and labeling to communicate the status and next steps. Regular updates on GitHub help maintain transparency and facilitate coordination with the version control aspects of our projects.

## Security and Confidentiality  
Protecting our data and unpublished results is essential in our academic research operations.

- **Data Security**:
  - **Restricted Data**: Never store restricted data in any GitHub repositories. Please refer to the [UF Data Classification Guidelines](https://policy.ufl.edu/policy/data-classification-policy/) to determine the sensitivity level of the data.
  - **Jupyter/R Markdown Files**: Before uploading Jupyter notebooks or R Markdown files to GitHub, ensure that all output cells are cleared to prevent the accidental disclosure of sensitive data. For step-by-step guides on how to clear outputs:
    - [Clearing Outputs in Jupyter Notebooks](/docs/research/hipergator/hipergator_jupyter/)
    - [Clearing Outputs in R Markdown](/docs/research/hipergator/hipergator_r/)
  - **Automating Cleanup**: Consider implementing scripts or using tools that automatically clear outputs before files are pushed to the repository, reducing the risk of human error.

- **Public vs Private Repositories**: We recommend using private repositories for unpublished research results. Exceptions may apply, but always consider the implications of sharing your research results publicly before deciding to use a public repository.

- **Access Review**:
  - **Regular Audits**: Perform regular audits of repository access permissions to ensure that access is limited to individuals actively involved in the project and only as needed. Schedule these audits quarterly or after significant changes to the team.
  - **Principle of Least Privilege**: Adhere to the principle of least privilege, ensuring that team members have only the access necessary for their tasks. Adjust access rights promptly as roles or project needs change.


## Training and Support
Our group offers comprehensive resources to ensure all team members are equipped to use GitHub effectively:

- **Training Sessions**: 
  - **External Training**: UF IT provides regularly scheduled [training sessions](https://training.it.ufl.edu/training/items/git-and-github-.html) to help new and existing members become proficient with GitHub.
  - **Internal Training**: Additional training sessions are available upon request from our lab admins, offering tailored guidance and answering specific queries related to our projects.

- **Documentation**: Each GitHub repository within our group includes up-to-date README files that provide an overview of the project, setup instructions, and usage guidelines.
  
- **Support**: If you encounter issues that require more direct or immediate assistance, please reach out to the lab admins, primarily our data scientists via email or Teams message.
  

## Review and Amendments

Ensuring our SOP remain current and effective is vital for the smooth operation of our lab. Here’s how we manage reviews and amendments:

- **SOP Review**: The SOP will be reviewed annually or as necessary to adapt to new GitHub features, evolving lab needs, or updated security policies.

- **Feedback and Changes**: We encourage all team members to provide feedback on the SOP. All proposed amendments will be reviewed by the admins, and changes will be implemented based on consensus and alignment with lab goals and policies.
