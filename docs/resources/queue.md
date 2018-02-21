# Queue Usage

## Introduction

In order to take advantage of a computational cluster we use some special software to manage all the commands that are to be run on them. This is essentially what separates a cluster from just a bunch of computers. If we didn't use queue software to manage the resources, they would eventually end up being mismanaged and keeping track of everything would be a nightmare. Too many users could over-commit a computer to run more than the resources it had available. Each user would have to talk to all of the other users to figure out what resources they could utilize. This is just a small example of the potential problems. 

In order to keep the system running smoothly and to make sure every user get's their "fair" share of the resources we use a system that's designed to manage this. To execute commands on the cluster we use a queue system. The software installed is the [[http://www.adaptivecomputing.com/resources/docs/torque/3-0-3/index.php|Torque/PBS]] suite of products from [[http://www.clusterresources.com|Cluster Resources/Adaptive Computing]]. 

Of Particular interest is the [[http://www.adaptivecomputing.com/resources/docs/torque/3-0-3/index.php|Documentation]] and [[http://www.adaptivecomputing.com/resources/docs/torque/3-0-3/2.1jobsubmission.php|Job Submission]]


# Job Submission and Control

## Introduction to PBS

PBS is the job queuing and management system used to balance available resources. All jobs must be submitted through PBS in order to ensure that resources are allocated properly. For all of the resources you will submit jobs using PBS syntax on the PBS server grid.hpc.hamilton.edu. 

It is imperative that jobs are only run using the PBS queue system. Because we will not be able to process system accounting for jobs run directly from command line, for both commercial or custom-written software, any jobs run manually (i.e. without PBS) will be killed.

PBS uses queues to manage resources. 

    [root@grid ~]# qstat -Q
    Queue              Max    Tot   Ena   Str   Que   Run   Hld   Wat   Trn   Ext T   Cpt
    ----------------   ---   ----    --    --   ---   ---   ---   ---   ---   --- -   ---
    default              0      0   yes   yes     0     0     0     0     0     0 E     0
    debug                0      0   yes   yes     0     0     0     0     0     0 E     0
    

The default queue is **default**. The debug queue will be bound to a small number of cpu's for quick testing of jobs. The **default** queue is the actual queue that the resources will run on. 


## Create a Job

To run a PBS job, you first prepare a PBS batch script. Each script has two sections. The top section contains parameters for PBS. The bottom section contains the commands used to run your job.

Following is an example batch script. This would be saved in a file called something like testjob.run. Any name will work but if you don't use the -N option below this file name will be chosen as the job name for you. So choose this name wisely since the queue system only shows the first few characters of it in the qstat display. Pick something that will allow you to distinguish between your jobs.

    #PBS -N testjob  
    #PBS -l nodes=1:ppn=4    
    #PBS -l mem=2GB 
    #PBS -l file=1000gb   
    #PBS -q una   
    #PBS -M <your name@DOMAIN_NAME> 
    #PBS -m bea        
    #PBS -j oe         
    #PBS -l walltime=24:00:00
    #PBS -r n
    #
    cd $PBS_O_WORKDIR
                
    <commands to run> (ie. date;uptime;echo "hello";date) 


All PBS parameters look similar. An explanation of the most common parameters you will use in your scripts:

    #PBS -N testjob
Name of the job. If omitted, uses filename.

    #PBS -l nodes=1:ppn=4
Number of nodes and processors per node to be used for the job. 

    #PBS -l mem=1GB
Amount of memory, in MB or GB, to be used.

    #PBS -l file=100gb
Amount of disk (scratch) space you need for the job (values in kb,mb,gb,tb). 

    #PBS -q una
Name of the queue to run job under.

    #PBS -M joeuser@DOMAIN_NAME
Your email address.

    #PBS -m bea
Email you when job begins, ends and aborts.

    #PBS -j oe
Merge PBS output and error files.

    #PBS -l walltime=24:00:00
How much time you need the requested resources. All jobs get 24 hours by default.
If you need more than that be sure to specify walltime in your jobs. Use your best over-guesstimate without having your jobs prematurely aborted.

    #PBS -r n
Define whether the batch job is re-runnable. Arguments are y or n. (Defaults to yes)

The remaining portion of the script contains commands to run your job. They are similar to what you would type on the command line. Make sure to include a command to change to the directory where you want the output and error files to be stored. For example:

    cd $PBS_O_WORKDIR
changes you to the directory where the run file was queue'd from. This is always a good idea to use since it will make sure all your input/output files are in the same directory. Otherwise if you don't put this in, the files will get written to the top level of your home directory. 

    date;uptime;echo "hello";date
command to run


## Submit a Job


The qsub command is used to submit jobs to PBS. Once you have prepared your batch script, the job is submitted to PBS by entering:

    % qsub scriptname

where scriptname is the actual name (ie. testjob.run) you gave to your batch script.

PBS will respond to you with something like:

    77.grid

The number preceding the system name is the job number assigned by PBS to your job.

For more information about qsub,

    % man qsub 

----


## Checking the status of a job


The qstat -a command displays information about the PBS queues and the jobs on the queues. It indicates whether your jobs are running or queued, as well as showing the state of all other jobs on the system.

     % qstat -a
                                                                                      
     Job ID               Username Queue     Jobname   SessID  NDS TSK Memory Time  S Time
     ------------------   -------- -------- ---------- ------  --- --- ------ ----- - -----
     31403.grid           luke     batch    Pentamer_p    --    --   8    --  900:0 R 100:5
     31417.grid           luke     batch    Pentamer_d    --    --   8    --  900:0 R 96:54
     31464.grid           luke     batch    2260.run    32008   --   8    --  24:00 R 07:28
     31466.grid           luke     batch    2320.run     5687   --   8    --  24:00 R 05:15
     31473.grid           luke     batch    2530.run    13688   --   8    --  24:00 R 10:22

To get a very detailed list of information about a job:

    % qstat -f <job id>
    

----

## Checking the status of a queue


There are several ways to check the status of a particular queue, or all queues.
 
To see what jobs have been submitted to the queues, type:

    % qstat -a

To see a summary of the queues, and the number of jobs running and queued for that queue, type:

    % qstat -Q

You can also run:

    % qstat -q

for similar information.

To get a list of jobs and the machines they are running on:

    % qstat -n

To see a detailed description of both the total queue resources and the resources currently in use, type:

    % qstat -Qf

Note that for any of the commands above you can specify the queue name for information just about that queue. For more information about qstat,

    % man qstat


In addition to the standard commands, some system alias commands exist too:

To get a list of all the jobs that only you have on the queue:

    % qme

To get a list of all the jobs that only you have on the queue with one additional line of the nodes that they are assigned to:

    % qme-n

----

## Remove a Job

The qdel command is used to delete a job from the queue. It can be used either when the job is running or queued.

    % qdel job_number

deletes the job with job_number as it's identifier. Before running qdel you can use the qstat command to find a job's number.

When you have lots of jobs in the queue it can be tedious to run the qdel command over and over for each command. There is a system alias command set up to do this for you. 

    % qdel-all
   
This will remove all the jobs you have on the queue system at once. (note: you can see all the system aliases by typing the //alias// command.)


----

## MPI Parallel job considerations

If you are planning to use a program that utilizes the MPI parallel execution environment there is something to take note of in terms of the command //mpiexec//. MPI is the Message Passing Interface which is one way to perform parallel calculations. It creates a ring of compute nodes using software to manage this communication. The ring is what's used to keep track of all the parallel traffic between hosts. There can be some overhead with creating an MPI ring and cleaning it up afterwards so the next user is able to have access to it. We have compiled //mpiexec// to take advantage of our queue system for this task. This mean that you don't have to worry about creating the mpi ring or any of the management. All you do is call your mpi program in your batch (PBS) script. For example, 

    % mpiexec -np 4 <parallel_program_name>
  
Because of this coupling, it isn't possible to run mpiexec outside of the queue system so you can test programs before submitting them to the queue. Normally, under MPI (we're using MPIch2) you can start your own ring on the command line and then be able to run parallel programs on the ring. 

One method to get around this is to still utilize the queue system but in an interactive state. It's called an Interactive Job...

## Interactive Job

An interactive job is one that allows you to have a command line and be able to test/run applications in real time. You create a normal PBS batch file except you just comment out or remove your command to run from the batch file. Basically the $PBS_O_WORKDIR line and below. Once you have that then just submit an interactive job to the queue:

    % qsub -I testjob.run

using the capital I switch to qsub tells it to do an interactive job on those resources specified. As soon as you type this you will end up being logged into the resource you were allocated from the queue system. You can run any type of system commands just like a normal login window. This can be the most effective way to test out your batch jobs before submitting them to run on their own. 

----

# Troubleshooting 


## Output files and Error files

When a job is started it has two output's. An output of all the commands the job ran and an output of errors with the job. If you specified the batch file directive -j (ie. #PBS -j oe) then your output and error messages are output to the same files. This directive is read like "**j**oin **o**utput and **e**rror". 

The output file gets written when the job is completed. This will be written to the top level of your home directory unless you specify the recommended change directory to the job submission directory (ie. cd $PBS_O_WORKDIR). The name of the output file will be of the format <jobname>.o<jobid>. 

using our testjob.run file from before, we specified the job name testjob (ie. #PBS -N testjob). So the output file would look something like testjob.o15. When you look at this file you'll notice these lines:

  Warning: no access to tty (Bad file descriptor).
  Thus no job control in this shell.

It is safe to ignore these messages since it is saying that this job ran in a shell environment that didn't have any job control functions. This isn't related to the cluster, it's related to the ability to control tasks within the shell. 

## tracejob

    [slyoung@HEAD_NODE_SERVER parallel]% tracejob 47
    Job: 47.biomath.colgate.edu
    01/14/2012 15:50:22  S    enqueuing into batch, state 1 hop 1
    01/14/2012 15:50:22  S    Job Queued at request of slyoung@HEAD_NODE_SERVER, owner = slyoung@HEAD_NODE_SERVER, job name = testjob, queue = batch
    01/14/2012 15:50:22  S    Job Modified at request of Scheduler@HEAD_NODE_SERVER
    01/14/2012 15:50:22  L    Job Run
    01/14/2012 15:50:22  S    Job Run at request of Scheduler@HEAD_NODE_SERVER
    01/14/2012 15:50:22  S    child reported success for job after 0 seconds (dest=node0001), rc=0
    01/14/2012 15:50:23  S    obit received - updating final job usage info
    01/14/2012 15:50:23  S    job exit status 0 handled
    01/14/2012 15:50:23  S    Exit_status=0 resources_used.cput=00:00:00 resources_used.mem=4996kb resources_used.vmem=238056kb resources_used.walltime=00:00:01
    01/14/2012 15:50:23  S    JOB_SUBSTATE_EXITING
    01/14/2012 15:50:23  S    dequeuing from batch, state COMPLETE
    [slyoung@HEAD_NODE_SERVER parallel]% 


tracejob gives you an output from the queue logs of the whole execution of the job. This information can only be looked up for a limited time until new log files are created (usually daily). 

## pbsnodes

The command pbsnodes will poll all the cluster nodes to make sure they are awake and talking to the queue server. To see all the nodes just type:

    % pbsnodes -a
    node0001
     state = free
     np = 12
     properties = batch
     ntype = cluster
     status = rectime=1326574334,varattr=,jobs=,state=free,size=18882332kb:19058396kb,netload=3025261910,gres=,loadave=0.00,ncpus=24,physmem=24599108kb,availmem=32356952kb,totmem=32987708kb,idletime=323127,nusers=0,nsessions=0,uname=Linux node0001.DOMAIN_NAME 2.6.32-131.0.15.el6.x86_64 #1 SMP Tue May 10 15:42:40 EDT 2011 x86_64,opsys=linux
     mom_service_port = 15002
     mom_manager_port = 15003
     gpus = 0
     <SNIP>... lots of repetitions of this for each one of the nodes...


Alternatively, you can just specify one node if you need to be specific:

    % pbsnodes -a node0001
   

# Exported Batch Environment Variables


When a batch job is started, a number of variables are introduced into the job’s environment which can be used by the batch script in making decisions, creating output files, etc. These variables are listed below:

PBS_JOBNAME

   * user specified jobname

PBS_O_WORKDIR

   * job’s submission directory

PBS_ENVIRONMENT 	
  * N/A 

PBS_TASKNUM
  * number of tasks requested

PBS_O_HOME 	
  * home directory of submitting user

PBS_MOMPORT 	
  * active port for mom daemon

PBS_O_LOGNAME 	
  * name of submitting user

PBS_O_LANG 	
  * language variable for job 

PBS_JOBCOOKIE 	
  * job cookie

PBS_NODENUM
  * node offset number

PBS_O_SHELL
   * script shell

PBS_O_JOBID
  * unique pbs job id
 
PBS_O_HOST 	
  * host on which job script is currently running
 
PBS_QUEUE 	
  * job queue

PBS_NODEFILE 	
  * file containing line delimited list on nodes allocated to the job

PBS_O_PATH 	
  * path variable used to locate executable within job script


----


For more detailed information see the [Torque (PBS) documentation](http://www.adaptivecomputing.com/products/open-source/torque/)





