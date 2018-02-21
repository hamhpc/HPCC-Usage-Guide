# Matlab Client Cluster Installation

## Introduction

Matlab is software provided by [MathWorks, Inc.](http://mathworks.com). 

If your Organization has purchased licenses for [MATLAB Distributed Computing Server (MDCS)](http://www.mathworks.com/products/distriben/) then you can configure the Matlab application on your local machine to utilize this cluster.  Please [contact your Administrator][HPC Admin] to find out if the software is installed and how many processes you are licensed for. 

## Requirements

  * In order to complete this process ,you'll need to make sure you have access to a Matlab account that has valid licensing for the Matlab client and the parallel computing toolbox. 
  * Make sure you have an account on the HPC Cluster that is configured with Matlab Distributed Compute Server (MDCS) software. You'll want to check with the cluster administrator for configuration details of the MDCS software on the cluster. 
  * (optional) Know how to [ssh into the cluster][ssh] using your account so that you can utilize the queue commands to check on the status of the jobs in conjunction with what Matlab can report about your running jobs on the cluster. 

## Obtain Mathworks account

In order to perform the installation you'll need access to a Mathworks account that has permission to use the Matlab client installer and licensing for this client install as well as a license for the parallel cluster toolbox. This is required in order to use the cluster for Matlab processing. Once you have an account proceed with the rest of the installation. Contact your IT group that manages institutional licensing for help with getting an account with the correct licenses. 

## Installation of Matlab

### Download Matlab Client

Login to the Mathworks site and [download a copy of the latest installer](http://www.mathworks.com/downloads/web_downloads/) (R2016a in this example). 

![download-matlab-client](img/download-matlab-client.png)

### Select OS Type 

![select-os-type](img/select-os-type.png)

### Run the installer

![execute-installer](img/execute-installer.png)}

### Accept License

![/accept-license](img/accept-license.png)

### Login to Mathworks for license information

![login-to-mathworks-for-license-information](img/login-to-mathworks-for-license-information.png)

### Install Software

![](img/install-software.png)

### Select license

![](img/select-license.png)

### Choose Installation location

![](img/choose-install-folder.png)

### Select Products

![](img/select-products-to-install.png)

### Install PBS integration scripts

![](img/install-pbs-integration-scripts.png)

You can get it from [Mathworks site](http://www.mathworks.com/matlabcentral/fileexchange/52815-parallel-computing-toolbox-integration-for-matlab-distributed-computing-server-with-pbs)

### Find the integration scripts

![](img/find-integration-scripts.png)

### Update independentSubmitFcn.m 

![](img/update-submit-functions.png)

### Update communicatingSubmitFcn.m

![](img/update-communicatingsubmitfcnm.png)

### Start Matlab and verify parallel toolbox is installed

![](img/start-matlab-and-verify-parallel-toolbox-is-installed.png)

### Manage Cluster profiles 

![](img/manage-cluster-profiles.png)

### Import Cluster Profile

If your administrator provided a default profile template for your organization you can simply import that profile and skip the following steps to manually create a cluster profile. Continue with the Validate Profile section. 

### Manually create cluster profile

![](img/manually-create-cluster-profile.png)

### Edit the new profile

![](img/edit-the-new-profile.png)

### Update basic configuration

Fill in the following fields: 

  *  Description - This is what you will use to describe this cluster so that you can distinguish it from the list of cluster profiles. 
  *  JobStorageLocation - This is the directory on your local computer where you will store your Matlab jobs. Typically, this is something like /Users/<USERNAME>/Documents/MATLAB (on OSX) but can be any location that you choose. 
  *  NumWorkers - This is the total number of cores that is licensed for Matlab use. You may need to contact the administrator to find out this information. 
  *  ClusterMatlabRoot - This is the directory location of where the Matlab MDCS software is installed on the cluster (/usr/local/Dist/MATLAB/R2016a)
  *  RequiresMathWorksHostedLicensing - use default
  *  LicenseNumber - leave blank

![](img/update-basic-configuration.png)

### Update Submit Functions

![](img/update-submit-functions.png)

### Update cluster environment

![](img/update-cluster-environment.png)

### Update Files and Folders

![](img/update-files-and-folders.png)

### Update Workers

![](img/update-workers.png)

### Update Job and Task Functions

![](img/update-job-tasks-and-functions.png)

### Validate Profile

Now that you have the profile configured you should run the validation tests to make sure your jobs will successfully run on the compute cluster. 

## Other Resources

  * [Getting Started with Serial and Parallel MATLAB Locally](serial-parallel-matlab-local.pdf)
  * [Getting Started with Serial and Parallel MATLAB Remote](serial-parallel-matlab-remote.pdf)
  * [Parallel Computing Code Examples](https://www.mathworks.com/products/parallel-computing/code-examples.html)
  * [Parallel Computing Toolbox Documentation](http://www.mathworks.com/help/distcomp/index.html)
  * [Parallel and GPU Computing Tutorials](https://www.mathworks.com/videos/series/parallel-and-gpu-computing-tutorials-97719.html)
  * [Parallel Computing Toolbox Video's](https://www.mathworks.com/products/parallel-computing/videos.html)
  * [Parallel Computing Toolbox Webinar's](https://www.mathworks.com/products/parallel-computing/webinars.html)

[ssh]: /usage/ssh.md
[contact]: /contact.md
[HPC Admin]: mailto:ROOT_EMAIL_TO_CHANGE
