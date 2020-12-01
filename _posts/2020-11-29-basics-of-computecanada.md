---
title : Basics of Compute Canada 
tags : [computecanada, slurm, scheduling]
---

### Basics of Compute Canada 

- Has multiple clusters throughout Canada and is built for researchers and universities to do their research work 

- We login using SSH and lands on a login node

- Computer Canada uses SLURM scheduling system 

- We should always use the scheduler to submit jobs 

- Exceptions are made for compilation and other tasks not expected to consume more than about 10 CPU-minutes and about 4 gigabytes of RAM, such tasks can run on login node

- A job submitted won't necessarily start immediately, as the scheduler would decide when to run the job

- As a user we need to specify to scheduler how much resources like memory, cpus, etc is required by our job 

- Scheduler decides on the basis of information provided by the user when it can schedule the requested job

## SLURM Jobs 

- SLURM provides [sbatch](https://slurm.schedmd.com/sbatch.html "sbatch") command to allow user to submit a job 

- User creates a batch file that contains not only the task to run but also the resources required

- Below is the example of a **simple job** 

{% highlight batch linenos %}
#!/bin/bash
# inform the os that we shall be using bash 
#SBATCH --account=def-somegroup  
# group to which resources shall be accounted
#SBATCH --time=2 
# time in minutes for the job 
#SBATCH --mem=256 
# memory in MB
#SBATCH -c 1 
# number of cpus requested
#SBATCH --output=output_name.out 
# the name of the output file 
#SBATCH --job-name=some-name 
# name for the job 

echo 'Hello World'
sleep 60

{% endhighlight %}

- We can use ```~/.bashrc``` file to hardcode the group information 

{% highlight batch linenos %}
export SLURM_ACCOUNT=def-someuser
export SBATCH_ACCOUNT=$SLURM_ACCOUNT
export SALLOC_ACCOUNT=$SLURM_ACCOUNT
{% endhighlight %}

- We can also create an **array job**, that shall automatically request multiple jobs

- Below is an example of array job submit request for 10 jobs, each shall have a unique job id

{% highlight batch linenos %}
#!/bin/bash
#SBATCH --account=def-someuser
#SBATCH --time=0-0:5
#SBATCH --array=1-10
./application_some $SLURM_ARRAY_TASK_ID
{% endhighlight %}

- we can also pass the array parameter through the command line via ```sbatch --array [1-10] some_script.sh```

- we can also throttle the number of jobs by using ```sbatch --array [1-10]%5 some_script.sh``` , this means that atmost 5 jobs will run at one time 

- We can also submit an **OpenMP job**, Bear in mind that for an application to use OpenMP it must be compiled with the appropriate flag. 

- Below is an example of OpenMp job request 

{% highlight batch linenos %}
#!/bin/bash
#SBATCH --account=def-someuser
#SBATCH --time=0-0:5
#SBATCH --cpus-per-task=8
export OMP_NUM_THREADS=$SLURM_CPUS_PER_TASK
./ompHello
{% endhighlight %}

- We can also submit a **MPI job**, below is an example of same 

{% highlight batch linenos %}
#!/bin/bash
#SBATCH --account=def-someuser
#SBATCH --ntasks=4               
# number of MPI processes
#SBATCH --mem-per-cpu=1024M
# memory; default unit is megabytes
#SBATCH --time=0-00:05
# time (DD-HH:MM)
srun ./mpi_program
# mpirun or mpiexec also work
{% endhighlight %}

- Large MPI jobs should use ```--nodes``` and ```--ntasks-per-node``` instead of ```--ntasks```

- We can also use the **interactive jobs** via [salloc](https://slurm.schedmd.com/salloc.html "salloc")

- It can be particularly beneficial for
  + Data exploration at the command line
  + Interactive "console tools" like R and iPython
  + Significant software development, debugging, or compiling

## Job Scheduling policies 

- Scheduling policy is based on different types of resources like cores, memory, time ... 

- Lets play around with a **sample scenario** where we follow FIFO approach

- Below is the how we can interpret the scheduling 

  ![basic scheduling](https://webhash.github.io/img/sscd/1.png "basic scheduling")

- Say we have list of 5 jobs to execute, we shall allocate the slots as soon as we have sufficient resources 

  ![run first and second job](https://webhash.github.io/img/sscd/2.png "run first and second job")
  
- No more memory is left for the third task, thus we wait for the job 1 to get over

- After job 1 is completed we can schedule the third job, which is MPI job thus it can take cores from other nodes. 

  ![run third job](https://webhash.github.io/img/sscd/3.png "run third job")
  
- Once job 2 is over we can schedule the next job as system has enough memory to do the scheduling 

  ![run fourth job](https://webhash.github.io/img/sscd/4.png "run fourth job")

- And finally we can execute the last job 

  ![run fifth job](https://webhash.github.io/img/sscd/5.png "run fifth job")
  
 - If we look at the job billing , even when fourth job didn't consume all the cores, we will bill it for 9 cores and it blocked the system by consuming all of its memory
 
  ![job billing](https://webhash.github.io/img/sscd/6.png "job billing")

- Many a times we have sequences of steps in our job and some of the steps can consume a lot for memory, for such scenarios we can use job dependency approach 

  ![job dependency](https://webhash.github.io/img/sscd/7.png "job dependency")
  
 - As we said the scenario was a sample one, because in reality, when job is submitted to the schedular queue it gets reordered based on the priority
 
 - **Factors that can impact the priority of a job**
   + Size : based on the resources requested 
   + Age : determined by the time spend in the queue 
   + Fair share : accounts's past usage affects the priority 
   + Partition : the classification node also affetcs the priority 
   


[1] created while following https://youtu.be/G0QANByJ9rY 
 
