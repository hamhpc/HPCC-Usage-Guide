# Log in to the cluster using SSH

## Introduction

## SSH on Mac OS X

## SSH on Windows
### Putty
### Cygwin

## SSH for Unix/Linux

## Passwordless SSH using SSH key

## Useful commands
### sshem

Since the cluster relies on ssh without a password (once you are logged into the head node) there is a shell script to take advantage of this for checking on the nodes. If you do the command **sshem**, followed by a command to run, it will ssh into all the compute nodes and execute that command. If you don't give it an argument then it will continually log into each machine. So make sure to give it a command to run, unless you wanted to log into every box and log out. 

Here's a quick command to check the **uptime** command on all the nodes. This allows you to see the load on them (last three columns). 

    [slyoung@HEAD_NODE_SERVER ~]% sshem uptime
    node0001:  20:33:01 up 8 days, 22:39,  0 users,  load average: 11.85, 7.69, 3.51
    node0002:  20:33:02 up 13 days,  3:38,  0 users,  load average: 11.83, 7.41, 3.31
    node0003:  20:33:02 up 13 days,  3:38,  0 users,  load average: 11.98, 6.74, 2.76
    node0004:  20:33:02 up 13 days,  3:38,  0 users,  load average: 11.83, 6.70, 2.76
    node0005:  20:33:02 up 13 days,  3:38,  0 users,  load average: 11.77, 6.56, 2.69
    node0006:  20:33:02 up 13 days,  3:38,  0 users,  load average: 11.79, 6.60, 2.71
    node0007:  20:33:02 up 13 days,  3:37,  0 users,  load average: 11.80, 6.68, 2.75
    node0008:  20:33:02 up 13 days,  3:37,  0 users,  load average: 13.46, 7.58, 3.12
    node0009:  20:33:03 up 13 days,  3:37,  0 users,  load average: 11.81, 6.65, 2.73
    node0010:  20:33:03 up 13 days,  3:37,  0 users,  load average: 11.78, 6.64, 2.74
    <SNIP> (list will continue for all the available nodes)
    [slyoung@HEAD_NODE_SERVER ~]% 
  
  
