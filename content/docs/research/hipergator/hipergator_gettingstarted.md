---
title: "Getting Started with HiPerGator"
summary: "Introduction of HiPerGator and a guide to getting started"
weight: 1
---

## Get the GATORLINK
GatorLink serves as an individual’s computer network identity at the University of Florida. Anyone accessing UF computing services must have a GatorLink username and password. Your GatorLink ID is linked to your UFID. To get started, visit the  [UF HelpDesk](https://it.ufl.edu/helpdesk/self-help/)

## Register for an account

 Follow the instructions on the [HiPerGator Account Request](https://www.rc.ufl.edu/access/account-request/) page. Every new user of HiPerGator requires a faculty sponsor to register. The faculty sponsor for our group is Dr. Yonghui Wu [📧](mailto:yonghui.wu@ufl.edu). Before registering, please send an email to the lab administrator to inform Dr. Wu of your request.

## Login to HiPerGator
   - **Command Line Access**:
     ```sh
     ssh <gatorlink>@hpg2.rc.ufl.edu
     ```
   - **Open OnDemand (OOD) Access**:
     Visit [Open OnDemand](https://ood.rc.ufl.edu/) and log in with your Gatorlink credentials.

## Transferring data
   All sensitive data must be stored on HiPerGator. Do not download restricted data onto personal devices. Use the following methods to transfer data:
   - **SFTP**: Use `sftp.rc.ufl.edu` for SFTP, SCP, and rsync activities. More info: [Data Transfer Guide](https://wiki.rc.ufl.edu/doc/Transfer_Data)
   - **Globus**: A high-performance data transfer tool. More info: [Globus Guide](https://wiki.rc.ufl.edu/doc/Globus)
   - **Open OnDemand (OOD)**: Navigate to the [OOD Dashboard](https://ood.rc.ufl.edu/pun/sys/dashboard) and use the `Files` dropdown to select storage locations.
