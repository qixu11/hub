---
title: "HiPerGator Storage"
summary: "Overview of disk space options and best practices for data storage on HiPerGator."
weight: 2
---


## Storage Structure

HiPerGator provides four main storage directories: Home Storage, Blue Storage, Orange Storage, and Red Storage.

### Home Storage
- **Location**: `~`, `/home/$USER`, or `$HOME`
- **Usage**: This is the very first directory you see when you log into HiPerGator. It contains critical files for setting up user shell environments and secure shell connections. It is ideal for configuration files, software builds, conda environments, text documents, and valuable scripts. Avoid using it for use it for data-intensive operation.  Do not delete `.bash*` files or the `.ssh` directory. If any essential files are accidentally removed, contact [UFRC](https://www.rc.ufl.edu/get-support/) to reset them. Home directories are somewhat protected by daily snapshots, but they are the smallest storage option available.

### Blue Storage
- **Location**: `/blue/group_name`
- **Usage**: Main high-performance parallel filesystem for job input/output (`job i/o`). It is efficient for reading and writing large files. Personal directory tree starts at `/blue/group_name/user_name`, and cannot be modified by other group members. A shared directory at `/blue/group_name/share` is available for group data sharing. Files can be distributed across multiple servers, making Blue Storage highly efficient for handling large files. However, it is less suitable for directories with numerous small files, as this can reduce its responsiveness. To use Blue Storage, change into your directory or list its contents using `cd /blue/mygroup` or `ls /blue/mygroup` to make it visible.

### Orange Storage
- **Location**: `/orange/group_name`
- **Usage**: Used for long-term storage of data not currently in use or for gentle access tasks. Orange Storage is more affordable but has limited performance compared to Blue Storage. It is suitable for storing data that does not require frequent access. To use Orange Storage, change into your directory or list its contents using `cd /orange/group_name` or `ls /orange/group_name` to make it visible.
- **Data Management Tips**: Prioritize Orange Storage for important data only, such as raw data or datasets that need to be "frozen" as reference points. Although Orange Storage is spacious, its capacity is still limited. Carefully consider what to store here to avoid consuming space with non-essential data.
<!--
### Red Storage
- **Usage**: High rates of input/output with flash-based storage. Red Storage is intended for short-term, high-performance tasks. Data is removed within 24 hours of the allocation's end date.

## Checking Quotas and Managing Storage
Use the following commands to check your storage usage and quotas:
- `home_quota`: Shows usage for HiPerGator Home directory.
- `blue_quota`: Shows usage for Blue Storage.
- `orange_quota`: Shows usage for Orange Storage.
-->

### Transferring Data
Recommended methods for data transfer:
- **SFTP**: Use `sftp.rc.ufl.edu` for SFTP, SCP, and rsync. More info: [Data Transfer Guide](https://wiki.rc.ufl.edu/doc/Transfer_Data)
- **Globus**: High-performance data transfer tool. More info: [Globus Guide](https://wiki.rc.ufl.edu/doc/Globus)
- **Open On Demand (OOD)**: Use the `Files` dropdown on the [OOD Dashboard](https://ood.rc.ufl.edu/pun/sys/dashboard) to select storage locations.





## Monitoring Storage Usage and Managing Files

Effective management of storage is crucial when working with large datasets or extensive computations on HiPerGator. Here are some tips and commands to help you monitor and manage your storage space effectively:

1. **Checking Storage Usage**: To check the current usage of your allocated storage, you can:
- Use the `du` Command:
```bash
du -sh /path/to/directory
```
This command calculates and displays the total size of the given directory.

- Use the `quota` Commands: To view the current storage usage for our entire group and how close you are to reaching our storage quota, HiPerGator provides specific quota commands:
	- `home_quota` to check the quota for your home directory.
	- `blue_quota` to check the quota for the Blue storage.
  	- `orange_quota` to check the quota for the Orange storage.
These commands will display the total used space as well as the total available space, helping you manage your group's storage capacity effectively.

2. **Locating Large Files**: Finding and managing large files is essential to optimizing storage utilization. Use the `find` command to identify files exceeding a certain size threshold:
```bash
find /path/to/search/ -type f -size +100M -exec ls -lh {} \;
```
This command lists files larger than 100 MB, helping you pinpoint potential candidates for cleanup or compression.

3. **Visualization Tools**: We can also use graphical tools like `ncdu` for a more interactive approach to explore and manage your files directly from the terminal:
```
ncdu /path/to/directory
```  
`ncdu` provides a navigable interface to view storage usage and delete files if necessary, directly from the command line.

By regularly monitoring and managing your storage on HiPerGator, you can ensure that you are using resources efficiently, avoiding potential issues with storage limits.

4. **Managing Trash Files**: It is important to regularly clean up trash files to prevent them from consuming valuable storage space in your home directory, which is typically very limited. Trash files on HiPerGator are stored in a specific directory `/home/user_name/.local/share/Trash/files/` and can accumulate over time if not managed properly.

### Best Practices for Data Storage
- **Archive Data**: For long-term storage, transfer essential data to the designated  server space.
- **Optimize Storage Allocation**: Use high-performance Blue Storage for frequently needed data and Orange Storage for less accessed items.
- **Adherence to Guidelines**: Follow the [HiPerGator usage guidelines](https://github.com/uf-hobi-informatics-lab/hipergator_use_guideline/) closely to understand departmental policies and ensure compliance.
  

