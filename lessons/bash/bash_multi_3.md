[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/training)

## <a name="filesfolders2"></a><a href="#contents" style="text-decoration:none; color:black;">Manipulating Files and Directories</a>

Over time you will start manipulating files and directories. This will include creating, copying, moving, removing and renaming files and directories. It is essential to have an organized file system especially when you start dealing with multiple files from multiple processes. This section will discuss the baisc simple commands necessary to manipulate files and directories. 

The first basic command is `mkdir`. This command **m**a**k**es a **dir**ectory in the file system. Like many other commands there are multiple flags that can be used with this command, however the basic useage is `mkdir directory_name`. For example:

	$ ls
	bin data usr
	$ mkdir home
	$ ls
	bin data home usr
	
To **c**o**p**y a file or directory you can use the `cp` command. This second basic command allows the user to copy a file or directory and specify a desination. This command has the format `cp source destination`. For Example:
		
	$ ls 
	bin data home usr
	$ cp home thesis
	bin data home thesis usr
	
The next basic command is `mv` which easily enough stands for **m**o**v**e. Similar to `cp` in this command you specify a source and a destination however unlike `cp` it will only keep the desitnation. For this reason `mv` is used to rename files. To move a file you can type the following in the command line:

	$ ls 
	bin data home thesis usr
	$ mv thesis home/
	$ ls 
	bin data home usr
	$ cd home	
	$ ls
	thesis
	
Notice that the directory `thesis` is no longer in the root directory but instead in the home directory. To rename a file you can specify the `source` as long as the source is not within the current directory. For example:

	$ ls
	thesis
	$ mv thesis paper
	$ ls
	paper
	
Finally there a few different ways to remove a file or directory. For example:
	
	$ ls
	cse.txt mend.cfg music papers school thesis
	$ rm mend.cfg
	$ ls
	cse.txt music papers school thesis 
	$ rm thesis
	rm: thesis: is a directory
	
You simplify cannot remove a directory using the `rm` command. It turns out that to remove a directory there are is a special `rmdir` command. 

	$ rmdir thesis
	$ ls
	cse.txt music papers school
	
Another option is to use the flag `-d` which attempts to remove directories as well as other file types. For example:

	$ rm -d school
	$ ls
	cse.txt music papers
	
We now know how copy, move, rename, and remove a file. But what about creating a new file? There are a few different ways you can create a new file. To create a blank file you can use the `touch` command. For example:

	$ touch ae410.txt
	$ ls
	ae410.txt cse.txt music papers
	
In some cases the `touch` command is used to update the timestamp on a file if the file already exists. 

To open a new file you can use a different editors. For exmaple if I wanted to open a new file and begin editting it I could use the text editors `vi` `vim` `nano` among others. In this case lets use `vi` to open a new file called `cse450.txt`:

	$ vi cse450.txt
	
The `cat` command allows you to view but not edit a file. For example if we want to view the file `cse450.txt` we can:

	$ cat cse450.txt
	This is what is inside the cse450.txt file.
	
Lets say that there are a lot of files that you want to copy, move, rename, or remove. We can use what are called *Wildcards*. 

- `*` - represents zero or more characters
- `?` - represents a single character
- `[]` - represents a range of characters

These commands allow the user to ask for a specifc pattern or set of files and directories. For example lets say we have the following in our directory, 

	$ ls
	ae410.txt cse.txt dir5 dir37 dir40 
	file1.txt file2.txt music papers
	
And we want to know what files we have that start with the letter `f` we can use the `*` command. 

	$ ls f*
	file1.txt file2.txt
	
If we cant to find all files that have exactly 3 characters as an extension we can use the `?` command:

	$ ls *.???
	ae410.txt cse.txt file1.txt file2.txt
	
The last wildcard listed above is the `[]` command which can be used to specify a list of characters that you want to find. For example if you want to remove all files that start with the letter **a** and **c** you can type in the command line

	$ ls
	ae410.txt cse.txt dir5 dir37 dir40 
	file1.txt file2.txt music papers
	*
	$ ls
	dir5 dir37 dir40 file1.txt 
	file2.txt music papers
	
As a reminder if there is a command that you don't know exactly how to use or if you want to find out what the flags are reference the `man` pages. 

###Do [Exercise #2](./ex2.html)

<br>
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black; border-top:1px solid #CCC; line-height:300%;">
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">Contents</a></td>
<td style=" border:0px solid black;"></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_2.html">⬅ Previous</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="font-weight:bold;" href="./bash_multi_3.html">Manipulating Files and Directories</a></td>
<td style="border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_4.html">Next ➡</a></td>
</table>
