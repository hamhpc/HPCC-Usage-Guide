# Usage

## Introduction

 Welcome to the High Performance Computing Cluster (HPCC) at ORGANIZATION_NAME_TO_CHANGE. 
 
## What is HPCC?

 The High Performance Compute Cluster (HPCC) is a collection of computers configured in a way so that they can act like one large computer. Let's give a basic example. 

Suppose you have your local computer, and let's say it has one CPU. 

You install a program on it that can calculate lots of numbers to solve a problem. 

For this example, let's say the problem is the same algorithm, but the "time" variable is the only thing that changes. You have a lot of data to calculate, so you start running it on your local computer on one CPU. When the application starts to run, you start to figure out that it will take you 6 month's to run on your personal computer using the one CPU. 

That's A LOT OF TIME! 

Well, no worries, that's why you're probably here to begin with! So if we take this same problem but instead of running it on your local computer, we run it on the HPC Cluster. If you use one CPU then you'd get the same results. HOWEVER, if you were to break this problem in half and run half on one CPU and half of it on another CPU then you'd get your results back in HALF the time... so 3 month's! 

Yea, you're probably starting to see a pattern here...

Now if I continue to break this problem up, I can get back results in minutes or hours depending on how big the problem is and how many compute resources are available at the time. This is what parallel computing is. Now, this isn't totally true, because there is a limit on how much a problem can be broken up. The communication between all the computers in the cluster can eventually slow the process down if it takes longer to send the communication back and forth while it's trying to solve the problem. 

This seems like it can be hard huh? .. well luckily we don't have to manage all this as most applications that are used are already written to take advantage of this parallel communication. Of course, you will most likely end up having to learn some [Unix skills](/linux-tutorial/index.md) so that you are comfortable working within a unix/linux system. 

## How does it work?

You could just pick a compute node, login to it, and run your command. 
 
However, being that it's a system that has many users, how can we make sure that we're not over using all the available resources? 
 
This is the backbone of the HPCC, the Queue Software. 
 
For this cluster, it's using the [Torque Resource Manager][torque] to manage the available resources. This software is responsible for taking an available "job" and running it on the computers that this "job" is allocated to. 

A "job" is the HPC slang for "the execution of your program". 

However, in addition to the [Torque Resource Manager][torque] software, the cluster also uses Scheduling Software called "maui". The [Maui Scheduler software][maui] is what makes the decisions on the schedule or who's next to run based on site's configured rules. Certain priorities can be configured with the scheduler in order to give priority to certain types of jobs or by research groups. 

Together, torque and maui make up the "Queue System Software" for the cluster. Each package has commands you can utilize to manage your jobs on the queue. By having a queue system to manage the execution of jobs across resources, it ensures that users of the system get fair and dedicated access to those requested resources. 


## Requirements

In order to begin utilizing this resource, you'll need to make sure you have some [basic knowledge of how to use Unix based systems][linux-tutorial], as well as preparing some tools to allow you to use the cluster resource. 

 To be successful in utilizing the compute cluster, you'll need to make sure you have a user account assigned to you for the research group you are working with. 

For students, you'll want to ask the Faculty that you are working with to request an account for you. 

They'll need the following: 

  * correct spelling of your first and last name 
  * email address to where you get your email
  * preferred SHELL (ie. bash/tcsh) (bash is default if you're unsure) 

While you wait for your credentials, you can continue reading in order to make sure you have all the tools you need to access the cluster. 

## Using the System

Now that you have a rough idea of what this is. How do you use it? 

Basically, there are two things you do with a cluster. 

Get your application installed so you can use it. Then creating "jobs" that will execute your programs so you can get results.

In the [next section][ssh] we'll go over how to use SSH to log into the cluster with your account. If you don't already have an account then look at the [Requirements](#requirements) section above to request one. 


## How to Get Help

Take a look at the [Contact][contact] page for information. 

[torque]: http://docs.adaptivecomputing.com/torque/6-1-0/adminGuide/help.htm
[maui]: http://www.adaptivecomputing.com/products/open-source/maui/
[linux-tutorial]: /linux-tutorial/index.md
[ssh]: /usage/ssh.md
[contact]: /contact.md
