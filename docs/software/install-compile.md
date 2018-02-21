# Compiling/Building Software

 In order to build software packages to use on the system you have two options. 
 
 As a user, you can install and manage anything in your own personal home directory space. This is known as /home/<username>. Your environment is configured to look for certain specific directories (like bin and lib) within your home directory and include them in your Environment. This is a good idea for a quick script that perhaps you want to test out but not everyone on the system would ever use it. 
 
 If the program is best suited to be installed in /usr/local with all the other global applications then it's best to contact the [HPC Admin][HPC Admin] to install this software for you. If you are in doubt, you should ask your administrator before proceeding. 


## Downloading the source

When downloading the source packages they should go in your ~/src directory at the top level of your home directory. Create it, if it doesn't exist. This following process is generally the easiest way to download a source package and prepare it for building as a normal user.  

    % cd ~/src   (mkdir -p ~/src if it doesn't exsist)
    % wget http://<source domain of software>/source_package-3.2.0.tar.gz
  
Now uncompress the package in this directory and set the permissions

    % tar -zxvf source_package-3.2.0.tar.gz
    % chown -R ${USER}:${GROUP} source_package-3.2.0
    % cd source_package-3.2.0

You are now ready to start compiling this application. 

## Compile the Software

In order to make sure that the software gets installed in it's own specific location we ALWAYS tell configure the prefix. 

In this case, it's for a user's home directory so we'll use that for the prefix. The default is usually to install into /usr/local which is reserved for the HPC Admin to do, since /usr/local is reserved for installed applications that everyone utilizes. 

    % ./configure --prefix=~/
  
Once configure finishes making all the configuration files for your architecture type you'll be ready to compile the software:

    % make
  
Depending on the type of software it could be quick or take quite a few minutes. 
If you notice any errors be sure to note them as you may need to search for those problems and resolve them to successfully get the software to compile. Be sure to follow the instructions in the documentation for how to install your application. Many times there can be other applications that are dependancies and need to be installed before this application will compile. 

The main point here is the we need to make sure nothing gets configured for /usr/local (which is the default) when we run the configure command. We always specify a prefix of our home directory (--prefix=~/) to configure. 

Once the program successfully compiles it's time to install it so you can start using it. 

## Install package

The software is compiled and you're in the ~/src/<package-name>-<package version> directory. We compiled the software configured for your home directory so running make install will copy all the files to this location. 

    % make install
  
  
Either log out and back in to see the new commands or type the command **rehash** to have your PATH environmental variables updated and your new application(s) available. 

