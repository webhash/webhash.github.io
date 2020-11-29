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

- SLURM provides sbatch command to allow user to submit a job 

- User creates a batch file that contains not only the task to run but also the resources required 

{% highlight batch linenos %}

#!/bin/bash
#SBATCH --account=def-somegroup  # group to which out resources shall be accounted to 
#SBATCH --time=2 #  time in minutes for which we need to run our job
#SBATCH --mem=256 # memory in MB
#SBATCH --cpus-per-task=1 # number of cores requested
#SBATCH --output=output_name.out # the name of the output file for the job sumitted 
#SBATCH --job-name=some-name # name for the job 

echo 'Hello World'

{% endhighlight %}


