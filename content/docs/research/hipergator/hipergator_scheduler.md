---
title: "SLURM Scheduler"
summary: "Guide on using the SLURM scheduler for running jobs on HiPerGator."
weight: 5
---

HiPerGator uses Simple Linux Utility for Resource Management (SLURM) to allocate resources and schedule jobs. Below are sample SLURM scripts and guidelines for building your own batch jobs.

## Sample SLURM Scripts

### Basic, Single-Threaded Job
This script is a template for single-processor applications. Use the `--mem-per-cpu` flag to request the appropriate amount of memory for your job. Test your application to set a reasonable memory value based on actual usage. The `%j` in the `--output` line substitutes the job ID in the output file name. You can also add a `-e` or `--error` line with a filename to separate output and error logs.

```
#!/bin/bash
#SBATCH --job-name=serial_job_test    # Job name
#SBATCH --mail-type=END,FAIL          # Mail events (NONE, BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=email@ufl.edu     # Where to send mail  
#SBATCH --ntasks=1                    # Run on a single CPU
#SBATCH --mem=1gb                     # Job memory request
#SBATCH --time=00:05:00               # Time limit hrs:min:sec
#SBATCH --output=serial_test_%j.log   # Standard output and error log
pwd; hostname; date

module load python

echo "Running plot script on a single CPU core"

python /data/training/SLURM/plot_template.py

date
```

### Multi-Threaded SMP Job

This script serves as a template for applications that use multiple processors on a single server or physical computer. These applications, known as threaded, OpenMP, PTHREADS, or shared memory applications, require all processors to be on the same node.

These applications need shared memory and can only run on one node. Keep in mind:

- Set `--ntasks=1` and `--cpus-per-task` to the number of threads you want to use.
- Inform the application about the number of processors:
  - For some applications, set `OMP_NUM_THREADS` to match `--cpus-per-task`.
  - For others, use a command line option.
    
```
#!/bin/bash
#SBATCH --job-name=parallel_job      # Job name
#SBATCH --mail-type=END,FAIL         # Mail events (NONE, BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=email@ufl.edu    # Where to send mail   
#SBATCH --nodes=1                    # Run all processes on a single node  
#SBATCH --ntasks=1                   # Run a single task    
#SBATCH --cpus-per-task=4            # Number of CPU cores per task
#SBATCH --mem=1gb                    # Job memory request
#SBATCH --time=00:05:00              # Time limit hrs:min:sec
#SBATCH --output=parallel_%j.log     # Standard output and error log
pwd; hostname; date

echo "Running prime number generator program on $SLURM_CPUS_ON_NODE CPU cores"

/data/training/SLURM/prime/prime

date
```

If you run multi-processing code, such as using Python's multiprocessing module, ensure you specify a single node and the number of tasks your code will use as in:

```
#!/bin/bash
#SBATCH --job-name=parallel_job_test # Job name
#SBATCH --mail-type=END,FAIL         # Mail events (NONE, BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=email@ufl.edu    # Where to send mail	
#SBATCH --nodes=1                    # Run all processes on a single node	
#SBATCH --ntasks=4                   # Number of processes
#SBATCH --mem=1gb                    # Total memory limit
#SBATCH --time=01:00:00              # Time limit hrs:min:sec
#SBATCH --output=multiprocess_%j.log # Standard output and error log
date;hostname;pwd

module load python/3

python script.py

date
```

### Array Job

To submit multiple identical jobs without an external script, use SLURM's array jobs feature. Note: There is a maximum limit of 3000 jobs per user on HiPerGator.

For example, to run 5 tasks in an array, use the following script. `%A` represents the master job ID of the array, and `%a` represents the task ID in the output filename:

```bash
#!/bin/bash
#SBATCH --job-name=array_job_test   # Job name
#SBATCH --mail-type=FAIL            # Mail events (NONE, BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=email@ufl.edu   # Where to send mail    
#SBATCH --ntasks=1                  # Run a single task
#SBATCH --mem=1gb                   # Job Memory
#SBATCH --time=00:05:00             # Time limit hrs:min:sec
#SBATCH --output=array_%A-%a.log    # Standard output and error log
#SBATCH --array=1-5                 # Array range
pwd; hostname; date

echo This is task $SLURM_ARRAY_TASK_ID

date
```

###  GPU Job

Please see [GPU Access](https://help.rc.ufl.edu/doc/GPU_Access) for more information regarding the use of HiPerGator GPUs. Note that the order in which the environment modules are loaded is important.

-VASP
```
#!/bin/bash
#SBATCH --job-name=vasptest
#SBATCH --output=vasp.out
#SBATCH --error=vasp.err
#SBATCH --mail-type=ALL
#SBATCH --mail-user=email@ufl.edu
#SBATCH --nodes=1
#SBATCH --ntasks=8
#SBATCH --cpus-per-task=1
#SBATCH --ntasks-per-node=8
#SBATCH --distribution=cyclic:cyclic
#SBATCH --mem-per-cpu=7000mb
#SBATCH --partition=gpu
#SBATCH --gpus=a100:4
#SBATCH --time=00:30:00

module purge
module load cuda/10.0.130  intel/2018  openmpi/4.0.0 vasp/5.4.4

srun --mpi=pmix_v3 vasp_gpu
```
-NAMD
```
#!/bin/bash
#SBATCH --job-name=stmv
#SBATCH --output=std.out
#SBATCH --error=std.err
#SBATCH --nodes=1
#SBATCH --ntasks=1
#SBATCH --ntasks-per-socket=1
#SBATCH --cpus-per-task=4
#SBATCH --distribution=block:block
#SBATCH --time=30:00:00
#SBATCH --mem-per-cpu=1gb
#SBATCH --mail-type=NONE
#SBATCH --mail-user=some_user@ufl.edu
#SBATCH --partition=gpu
#SBATCH --gpus=a100:2

module load cuda/11.0.207 intel/2020.0.166 namd/2.14b2

echo "NAMD2                = $(which namd2)"
echo "SBATCH_CPU_BIND_LIST = $SBATCH_CPU_BIND_LIST"
echo "SBATCH_CPU_BIND      = $SBATCH_CPU_BIND     "
echo "CUDA_VISIBLE_DEVICES = $CUDA_VISIBLE_DEVICES"
echo "SLURM_CPUS_PER_TASK  = $SLURM_CPUS_PER_TASK "

gpuList=$(echo $CUDA_VISIBLE_DEVICES | sed -e 's/,/ /g')
N=0
devList=""
for gpu in $gpuList
do
    devList="$devList $N"
    N=$(($N + 1))
done
devList=$(echo $devList | sed -e 's/ /,/g')
echo "devList = $devList"

namd2 +p$SLURM_CPUS_PER_TASK +idlepoll +devices $devList stmv.namd 
```

## SLURM Commands
Below are some useful SLURM commands. For more detailed information, see the [SLURM Usage Guide](http://slurm.schedmd.com/slurm.html) .

### Submit Jobs
```
sbatch script
```

###  Interactive Session
An interactive SLURM session i.e. a shell prompt within a running job can be started with
```
srun <resources> --pty bash -i
```
For example, a single node 2 CPU core job with 2gb of RAM for 90 minutes can be started with
```
srun --ntasks=1 --cpus-per-task=2 --mem=2gb -t 90 --pty bash -i
```

###  Canceling Jobs
```
scancel jobID
```
or, for cancelling multiple jobs with names that follow a wildcard pattern
```
scancel pattern
```

### Checking Job Status

The basic command for checking job information is `sacct`. While full documentation is available on the SLURM webpage, here are some useful examples and templates for customization.

By default, `sacct` shows jobs in the queue or running since midnight of the current day. To view jobs from a specific date, use the start time (`-S` or `--starttime`) option. For example, to see jobs since May 1st (0501):
```
sacct -S 0501
```
To view specific information, specify the desired columns. For example, to see the number of CPUs, total memory use, and wall time of all jobs since May 1st:
```
sacct -S 0501 -o JobIDRaw,JobName,NCPUS,MaxRSS,Elapsed
```
And for the whole group:
```
sacct -S 0501 -o JobIDRaw,JobName,User,NCPUS,MaxRSS,Elapsed -a -A group_name
```
To view memory use of jobs:
```
sacct --format=User,JobID,ReqMem,MaxRss
```
The above commands retrieve information about completed jobs from the SLURM database. To check currently running jobs, use the `sstat` command. For example:
```
 sstat -j 123456.batch -o maxrss
```
For more details, see the [`sstat` manual](https://slurm.schedmd.com/sstat.html) page.


