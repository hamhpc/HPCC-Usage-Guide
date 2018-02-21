# Linux Tutorial: A Beginner's Guide

## Introduction

 According to WikiPedia, [Unix dates back to the mid 1960's](https://en.wikipedia.org/wiki/History_of_Unix). Most people use it everyday if they interact with the internet or a smartphone and don't even realize it. There are many different **flavors** or **versions** of Unix. The version of Unix that runs the Linux kernel are called Linux. Some of the most popular open source (free) Linux based systems are RedHat, CentOS, and Ubuntu. Mac OS X is a version of BSD Unix and Android is google's linux based smartphone platform. These are just a samples of popular unix operating systems.
 
 The reason you may not realize you are using Unix is because it works the best as a server platform. For example, when you send email, there's a good chance it's going through a Unix server somewhere on the Internet. 
 
 Unix is a very powerful multiuser operating system and has a steeper learning curve over the commodity desktop computer we have in our homes (like Mac OS X and Windows). Your desktop PC has a GUI.. a Graphical User Interface, where you manipulate the screen with a mouse and keyboard. 
 
 Unix systems can operate without any graphic user interface at all! Plus being a multiuser system multiple people can use the system at the same time from different locations. 
 
## The Unix Operating System 
 With all Unix operating systems, they have basically three main parts. The Kernel, a Shell, and Processes. 

### Kernel
 The Kernel's function is to handle providing time on the CPU and memory to execute programs. It also handle's the filesystem, and communication's in response to system calls. Since we're using CentOS, we are running a Linux kernel on the HPC Cluster.
 
### Shell
 The Shell is called a command line interpreter. It is a program that you run that will interpret the commands that you give to it. There are a few different types of SHELL(s). The most popular are Bash and Tcsh. 
 
 Bash and Tcsh are available for your account on this cluster installation. Unless Tcsh is requested, Bash is the default shell when you request an account. However, this can be changed after you get an account by contacting the [HPC Admin][HPC Admin]
 
 In recent years, Apple has helped make Bash a more popular SHELL since this is the default SHELL on Mac OS X. 
 
### Processes

Processes are programs that have been executed on the system and obtain a unique process id called a PID. Processes can be large programs that calculate lots of things or simple commands (like when using the command shell and typing copy (cp)). A process is the result of using the shell to give the kernel a task. 
   
## How is it structured? 
### General Directory Structure
#### Root
#### Boot
#### Var
#### Etc
#### Sbin
#### Bin
#### Lib
### Shared Applications (/usr/local/)
#### /usr/local/bin
#### /usr/local/global
#### /usr/local/Dist
### Your Home Directory (/home/username)
#### public_html

## How do you access it?

### Terminal
### Your Account
#### changing your password
#### customizing your environment
   
## Working with Files and Permissions
### Look at File permissions
### Change permissions on a file
### Change ownership/group of a file

## Executing commands
#### manual (man)
#### copy (cp)
#### move (mv)
#### remove (rm)
#### list (ls)
#### clear (clear)
#### concatenate (cat)
#### less (less) 
#### more (more)
#### head (head)
#### tail (tail)
#### which (which)

## Searching
#### less (less)
#### grep (grep)
#### word count (wc)
#### find (find)

## Redirecting I/O
#### Pipe (|)
#### standard input and standard output

## Processes
#### checking processes
#### ps
#### top

## Job control
#### put a running command in the background
#### bring forward a backgrounded process
#### show all active backgrounded processes
#### kill backgrounded process

## Text editors
### vi
### emacs
### nano

## Regular expressions

## The sed editor

## the awk programming language

## using X Graphical applications

## misc useful commands
#### find/replace in VI
   when in VI you can replace text in a file with syntax like the following: 
   
    :.,$s/phrase1/phrase2/g
    
It's read as: from here (dot) , to the end of the file ($) switch (s/) phrase1 with (/) phrase2 globally (/g)
   
## Tutorials & Useful Links

[Vi Tutorial]()

[Bash Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

[Bash Loop "While" Instructional Video](https://www.youtube.com/watch?v=ozKpndnotto)

[An A-Z Index of the Bash command line for Linux](http://ss64.com/bash/)

[Sed Tutorial](http://www.grymoire.com/Unix/Sed.html)

[Awk Tutorial](http://www.grymoire.com/Unix/Awk.html)

[Github tutorial](https://www.youtube.com/watch?v=0fKg7e37bQE)


[torque]: http://docs.adaptivecomputing.com/torque/6-1-0/adminGuide/help.htm
[maui]: http://www.adaptivecomputing.com/products/open-source/maui/
[linux-tutorial]: /linux-tutorial/index.md
[ssh]: /usage/ssh.md
[contact]: /contact.md
[HPC Admin]: mailto:ROOT_EMAIL_TO_CHANGE
