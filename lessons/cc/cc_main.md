[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/)

# Illinois CampusCluster


[_Campus Cluster_](http://campuscluster.illinois.edu) is a campuswide resource for high-performance computing located on the University of Illinois at Urbana-Champaign, consisting of several clusters available to researchers, students, and investors.

![](./img/cluster.svg)

A cluster is typically organized as a group of connected computer _nodes_, or processing units with memory and network access (basically all modern supercomputers are clusters^([Top500](http://www.top500.org/lists/2015/11/)) ). A node is much like your laptop or desktop machine, except instead of communicating with the outside world through a keyboard or monitor it only has a network connection. These network connections are used to coordinate processes running across groups of nodes as so-called parallel programs.

To access a cluster, you use a program called a _shell_. Typically, a shell consists of a command line which allows you precise control over the tasks you invoke, the jobs you run, and the files you create.  If you've worked on a GNU/Linux system before, this should be a familiar concept to you; if not there are various online resources on using shell, including our first workshop. 

The shell allows you to access the _head nodes_, which are the public interface to the cluster.  From these head nodes, you can submit lengthy and computationally intensive _jobs_ to the _compute nodes_, which carry out the massively parallel calculations necessary for your research.

A job or _batch file_ is simply a short script of the commands necessary to run your code.  The compute nodes can then set up the libraries and environment necessary for execution and carry out the calculation.  The script can also instruct the cluster what to do with the results of the calculations.

In addition, a file system is attached for the storage of programs and data over the short and long term.


## Getting Started

In order to use Campus Cluster, you need: computer with internet access, a _user account_ on the Campus Cluster, and a _shell_ (or its emulator if you are on a Windows machine).

### User Accounts

If you do not have a user account yet, you are free to use a training guest account from the list below.  (These are sandboxed accounts which have restricted privileges, but can be used to complete the exercises in this workshop.)

If you would like a personal account, you can obtain one through your research group (if your advisor has become an investor in the Campus Cluster program) or through the [Computational Science and Engineering](http://cse.illinois.edu) program (contact [cse@cse.illinois.edu](mailto:cse@cse.illinois.edu) for more information).

### Shell

Depending on your computer's operating system, a few options are available to you.

-   **Windows**:  While the command prompt is inadequate (since it supports DOS-like instead of Unix-like commands), a number of options are available on Windows.
    -   [MobaXTerm](http://mobaxterm.mobatek.net/) is a clean and simple client for connecting to remote servers.  This is our recommendation if you need to use Campus Cluster from a Windows-based machine.
    -   [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) is the classic standard for secure shell access on Windows.  (Be careful, however:  there is a malicious version online as well<sup>[[Paganini2015]](http://securityaffairs.co/wordpress/37013/cyber-crime/malicious-putty-in-the-wild.html)</sup>!)
    -   [Cygwin](https://www.cygwin.com/) is a powerful recreation of Unix-like system features on a Windows machine, but is overkill if all you require is secure shell access to a remote cluster.
    -   [PowerShell](https://technet.microsoft.com/en-us/library/ee221100.aspx) has the advantage of being built into Windows out of the box, but has an unusual syntax that is incompatible with learning a Unix-like shell.  Feel free to explore this option (since it is quite powerful), but we won't address it further in this document.

-   **Mac OS X**:  You need to access the Terminal.  Press `⌘``Space` to open Spotlight and then type `terminal`.  Press `Return` to open the highlighted application.
    ![](./img/spotlight.png)
    
-   **Linux**:  You're good to go.  Just find the "command line" or "terminal" option in your menu.  If it's not on the menu bar itself, take a look under "Applications" or the equivalent menu.

>Although there are subtle differences, you will often hear "terminal", "command line", "shell", "prompt", and "bash" used interchangeably.

Once you have a shell open, it's time to log in for a first look at the cluster environment.

### Logging On

In your command window, you will see a _prompt_ which looks something like `yourusername@machine:directory $ `. (There are a lot of variations on this.)

After the `$`, type `ssh <user>@cc-login.campuscluster.illinois.edu`, where `<user>` is replaced by the actual user name of the account you are using to access the cluster, for the campus cluster this is most likely your NetID.

```bash
$ ssh NetID@cc-login.campuscluster.illinois.edu
NetID@cc-login.campuscluster.illinois.edu's password: 
```
	
The machine will ask you for a password in response; enter the associated password and press `Return`. Additionally, sometimes the machine will ask you a question about [RSA security](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) which you can answer `yes` to; this should only happen once on a given machine. Other machines, like Blue Waters, will have added securitity features like one-time passwords. 

You should now be logged in.  What this means is that commands you enter into this shell are interpreted not by your home machine, but by the remote cluster's login nodes.

(If you are having difficulty with the password after a couple of tries, please contact [help@campuscluster.illinois.edu](mailto:help@campuscluster.illinois.edu).)

### First Look Around

A rather long-winded message appears, nominally welcoming you to the cluster but also including a number of warnings about disk space usage and proper etiquette on the login nodes.  URLs for resources such as a [user forum](https://campuscluster.illinois.edu/forum/) and a [beginner's guide](https://campuscluster.illinois.edu/user_info/doc/beginner.html) are also listed, and you should take a look at those at your leisure in the future as they answer many specific questions this document doesn't have space to address.

Your shell is now logically situated in your _home directory_, which is represented by the shorthand `~`.  If you type `pwd`, short for "**p**rint **w**orking **d**irectory", then you can see exactly where that home directory is located with respect to the root directory `/`.  If you type `ls`, the files in your home directory will be **l**i**s**ted for you.

Other standard shell commands are available as well.  If you are familiar with these, you can play around a little now; otherwise, please check out the first workshop in this series on bash. In any case, when you are done, type `exit` at the prompt to leave Campus Cluster and return to the context of your home machine.

## Environment

The environment around any campus cluster is similar to that of any linux system. In this case you're logging into a computer through a network. Otherwise the same rules apply. (In order to effectively learn the shell, check out SWC, HPCUniversity, etc.)

###Looking and Moving Around
Once you're logged on you will notice that the same shell commands apply. Typing `pwd` wil still print the working directory, `ls` will still list the directory contents. Likewise if you want to change the directory you can type `cd` etc. 

The main difference is that you are now working on a remote computer. Notice that you typed `ssh`, or **s**ecure **sh**ell, to log on to the campus cluster. This is just allows you to connect securely to a networked machine over an unsecure network. In order to exit the campus cluster you just type `exit`. If you are on a Windows machine make sure you click on the `ssh` option under `connection type` and type in the host name (cc-login.campuscluster.illinois.edu)

###Filesystem
Once you're inside your home directory on the campus cluster you'll notice that you have a couple of folders. Generally there is a 2GB quota on your `/home` direcotry with a 4GB hard limit. Another important directory you should notice is the `/scratch` directory. This directory has a much larger storage and is generally used to run your code in and store your (probably large) output files. 

Since you're running your code on a networked machine you simply cannot click and drop files into your `scratch` folder from your laptop or desktop machines. To move files to and from the campus cluster you can use the command `scp` and it can be used in numerous ways with the two most common being:

Copy file from remote host to local host
	
```bash
$ scp NetID@cc-login.campuscluster.illinois.edu:file1.txt /some/local/directory
```
	
Copy file from local host to remote host

```bash
$ scp file1.txt NetID@cc-login.campuscluster.illinois.edu:/some/remote/directory
```

If you are moving dozens of very large data files this process can be very slow. To help speedup the process you can use file transfer protocol software such as Filezilla, gFTP, etc. 

###Modules
Sometimes the environment that a researcher doing molecular dynamics is quite different from a that of someone doing computational fluid dynamics. To modify your environment variables you can use the `module` command. To print the list of current modules you can use the `module list` command. If you want to load a module that you do not currently have you can use the `module load` command, such as:

```bash
$ module load mvapich2/2.0b-intel-14.0
```
	
You can also load your modules by editing your `.bash_rc` file. 
    
## Running Code

We will use example codes obtained as follows to illustrate compiling, queueing, and running code on Campus Cluster.

```bash
$ cp ~ccp-csetraining01/SOURCE/hpc-code-examples.tar.gz
$ tar -xvzf hpc-code-examples
$ module load gcc
```

###Queueing
Fairshare queuing divides requested resources among system users or groups (rather than just between processes).  It incorporates the historic behavior of a user and group into job priority decisionmaking.  In principle, this allows groups and users to fairly access the resource.  However, this can be frustrating for a new user to understand, particularly when one has a number of jobs in the queue and it takes a long time for them to run.

Campus Cluster operations model:  all buy nodes have guaranteed access, but available otherwise

The following command are the basic batch job commands to submit, check on, or delete a batch job on the campus cluster. 

Command       | Description
------------- | -------------
qsub          | submit batch job
qstat         | query status of batch job
qpeek         | view stdout and stderr of job
qdel          | delete bactch job

###Compiling
If you're writing scientific code, you're almost definitely using C/C++, Fortran, or Python, so it behooves us to check and see what the options for those are.

Language | Compilers
-------- | ------------
C/C++    | `icc`/`icpc` and `gcc`/`g++`
Fortran  | `ifort` and `gfortran`

Python 2.7.8 and 3.4.1 are both available, plus legacy versions. The latest versions are always preferred for compiling new programs. Libraries are also available; for instance, the Intel MKL. You can see what is required to compile with it on a specific system using the [command-line flag tool](https://software.intel.com/en-us/articles/intel-mkl-link-line-advisor/).
            
###Installing
As you do not have administrator privileges on Campus Cluster, you won't be able to `make install` your software.  You have two options:

-   Set up a "local" installation for yourself:  create and add to your `$PATH` appropriate directories like `~/bin`.
-   Create a group-wide installation if you are part of a research group and can maintain the software. Click on this [guide](https://campuscluster.illinois.edu/user_info/doc/software_guidelines.html) for more information on this. 
-   Subsequent to a successful installation, you can create a `modulefile` which works with `module` to update the environment for other users of your software application.

This machine was jointly purchased by many investors, who each contributed an amount to the total capital hardware investment and are thus entitled to a perpetual share of the available computational power.

## A Friendlier Campus Cluster
You can modify your `.bash_profile` file to include things like color in your directory listing or shorten some commands. For example you can write 
	
```bash
	# .bash_profile
	
	alias ls='ls --color=auto'
	alias q="qstat -u $USER"
```

Preventative maintenance (PM) is scheduled for the third Wednesday of each month. Long jobs submitted just prior to this time cannot run until afterwards.

You can install your own software by createing local paths for `~/bin`, `~/.local`, etc.

For more campus cluster user resources you can visit the Illinois Campus Cluster Program [website](https://campuscluster.illinois.edu). Here you will find a beginner's guide, user's guide, FAQs, as well as user forums. 

-   [Summary Handout](https://github.com/uiuc-cse/hpc-sp15/raw/gh-pages/lessons/hpc-handout.pdf)

## Credits

Neal Davis developed these materials for [Computational Science and Engineering](http://cse.illinois.edu/) at the University of Illinois at Urbana–Champaign.  Some tips were suggested by Jay Alameda and Mark van Moers of NCSA.  In addition, the support of NCSA and Campus Cluster personnel such as Wayne Hoyenga, Martin Biernat, and Kandace Turner-Jones, has also been invaluable.

<img src="http://i.creativecommons.org/l/by/4.0/88x31.png" align="left">
This content is available under a [Creative Commons Attribution 4.0 Unported License](https://creativecommons.org/licenses/by/4.0/).

[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/)
