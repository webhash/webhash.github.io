---
title : Basics of Compute Canada 
tags : [computecanada, slurm, scheduling]
---

### Compute Canada 

- Has multiple server clusters through out canada and is built for researchers and universities to do their research work 

- We login using SSH and lands on a login node

- Computer canada uses SLURM scheduling system 

- We should always use the scheduler to submit jobs 

- Exceptions are made for compilation and other tasks not expected to consume more than about 10 CPU-minutes and about 4 gigabytes of RAM, such tasks can run on login node

- A job submitted won't necessarily start immediately, as the scheduler would decide when to run the job

- As a user we need to specify to scheduler how much resources like memory, cpus, etc is required by our job 

- Scheduler decides on the basis of information provided by the user when it can schedule the requested job

- SLURM provides [sbatch](https://slurm.schedmd.com/sbatch.html sbatch) command to allow user to submit a job 

- User creates a batch file that contains not only the task to run but also the resources required

- Below is the example of a simple job 

{% highlight batch linenos %}
#!/bin/bash
# inform the os that we shall be using bash 
#SBATCH --account=def-somegroup  
# group to which resources shall be accounted
#SBATCH --time=2 
# time in minutes for the job 
#SBATCH --mem=256 
# memory in MB
#SBATCH --cpus-per-task=1 
# number of cores requested
#SBATCH --output=output_name.out 
# the name of the output file 
#SBATCH --job-name=some-name 
# name for the job 

echo 'Hello World'
sleep 60

{% endhighlight %}

- we can use ```~/.bashrc``` file to hardcode the group information 

{% highlight batch linenos %}
export SLURM_ACCOUNT=def-someuser
export SBATCH_ACCOUNT=$SLURM_ACCOUNT
export SALLOC_ACCOUNT=$SLURM_ACCOUNT
{% endhighlight %}

- we can also create an array job, that shall automatically request multiple jobs

- below is an example of array job submit request for 10 jobs, each shall have a unique job id

{% highlight batch linenos %}
#!/bin/bash
#SBATCH --account=def-someuser
#SBATCH --time=0-0:5
#SBATCH --array=1-10
./application_some $SLURM_ARRAY_TASK_ID
{% endhighlight %}

