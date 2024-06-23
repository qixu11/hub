---
title: "Resource Constraints"
summary: "Guidelines for the usage of computational resources and storage space for group members, including QOS limits."
weight: 6
---

To effectively utilize HiPerGator, each user must be aware of the resource constraints imposed by both UFRC and our research group. Respecting these constraints is crucial, as it ensures optimal utilization of available resources and helps maintain efficient operations across the labs that share the computing resources.

## Quality of Service (QOS) Limits

 Each account has two QOS levels: high-priority investment QOS and low-priority burst QOS. The burst QOS allows short-term borrowing of unused resources from other groups. Each user is associated with a scheduler account that determines the available QOS levels, including those from secondary group memberships.

QOS levels determine the available computational resources (CPU cores, memory, maximum run time) and their priority. For detailed information, visit the [HiPerGator QOS Limits Documentation](https://help.rc.ufl.edu/doc/Account_and_QOS_limits_under_SLURM).


## CPU Cores and Memory (RAM) Resource Limits

CPU cores and RAM are allocated to jobs independently as requested in job scripts. Consider the QOS limits, hardware limitations, and fair usage to ensure efficient and fair resource allocation. HiPerGator's compute nodes have limited resources (CPU cores, memory, memory bandwidth, network bandwidth, and local storage). Fully consuming one resource can waste others, affecting overall system performance. 

When submitting a job, if no resource request is specified, default limits are applied: 1 CPU core, 4GB memory, and 10-minute time limit. Use `--mem` for total job memory, `--mem-per-cpu` for per-core memory, and `--time` for setting appropriate time limits within QOS constraints.

To avoid job pending due to QOS limits, ensure your resource requests are within limits. If a job cannot be satisfied within QOS limits or hardware constraints, the scheduler will return an error.

Use the `slurmInfo` command to view a summary of active jobs for a group:
```
slurmInfo -pu -g groupname
```
## Time Limits
Different sets of hardware configurations have their own time limits. An example configuration is:
```
#SBATCH --time=4-00:00:00 # Walltime in hh:mm or d-hh:mm
```
### Compute Partitions

Partitions include `hpg-default`, `hpg2-compute`, and `bigmem`. If no partition is specified for a job, `hpg-default` and `hpg2-compute` are selected by default.

1.Investment QOS

- **Default**: 10 minutes
- **Maximum**: 31 days (744 hours)

2.Burst QOS

- **Default**: 10 minutes
- **Maximum**: 4 days (96 hours)

### Interactive Work

Partitions for interactive work include `hpg-dev`, `gpu`, and `hpg-ai`.

- **Default time limit**: 10 minutes
- **hpg-dev Maximum**: 12 hours
- **gpu**: 
  - 12 hours for `srun .... --pty bash -i` sessions
  - 72 hours for Jupyter sessions in Open OnDemand
- **hpg-ai**: 
  - 12 hours for `srun .... --pty bash -i` sessions

### Jupyter

- **JupyterHub**: Sessions have preset individual limits shown in the menu
- **JupyterLab in Open OnDemand**: Maximum of 72 hours for the GPU partition, other partitions follow standard limits

### GPU/HPG-AI Partitions

- **Default**: 10 minutes
- **Maximum**: 14 days


## BMI Resources Usage Guideline

As members of Dr. Wu's research group (ID: 4014, [yonghui.wu]), we share significant computational resources across various labs within our division. Currently, we have:

- **CPUs**: 2570 units
- **GPUs**: 300 units
- **Memory**: 35 TB

To ensure fair and efficient use of these resources, please adhere to the following guidelines:

### Resource Registration and Usage

- **Prior Registration**: Before submitting jobs that exceed the thresholds of 8 CPUs, 1 GPU, or 128 GB of memory for more than 3 hours, ensure to check and register your requirements on the [HPG usage table](https://docs.google.com/spreadsheets/d/1ZMgEGeWTPbycu4Bg6NmTzIUX4TtlBKTtov13cmwn3UM/edit?usp=drive_link).
- **Resource Limits**: Do not reserve more than 64 CPUs, 500 GB of memory, or 4 GPUs for any single job without additional coordination.
- **Duration of Use**: Limit node reservations to no more than 7 days unless additional arrangements are made.

### Storage Usage
- **Blue Storage**: Do not use more than 250 GB.
- **Orange Storage**: Usage is capped at 1 TB.
- **Storage Coordination**: Contact Aokun for further coordination if the remaining storage space in either Blue or Orange storage falls below 1 TB.

<!--
These rules are designed to promote equitable access and optimal use of shared resources. For additional information or to discuss coordination for exceptional cases, please reach out to the administrative contact.
-->

### Policy for Coordination

- If you need more than 256 CPUs, 1 TB of memory, 16 GPUs, or require resources for more than 7 days, you must first send a request to Aokun Chen [📧](mailto:chenaokun1990@ufl.edu) or Xing He [📧](mailto:hexing@ufl.edu), with your supervisor cc’ed, to justify your need and obtain approval.
  
