[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/training)

## <a name="intro"></a><a href="#contents" style="text-decoration:none; color:black;">Introduction</a>
A shell is a program that let's the user interact with the operating system through a command line. While most computers have graphical user interfaces (GUI), shells only have a textual interface. The textual interface may seem cryptic at first but it can be very useful due to its high action-to-keystroke ratio, its support for automating reportetitive tasks, and it can also access networked machines. There are various shell programs out there with the most common one being Bash (**B**ourne **A**gain **SH**ell). To begin, let's figure out which shell we are using by typing `echo $SHELL` in the command line: 

	$ echo $SHELL
	/bin/bash
	
`echo` is a command that prints a string to the terminal. In this case the shell printed the environment variable `$SHELL`. We can also tell the shell to print anything we like such as

	$ echo Hello World!
	Hello World!
	
To print to the screen who the current user is type `whoami` and your LoginID should be printed to the terminal. If you are using your personal computer then the username will be printed to the terminal. 
	
	$ whoami
	<LoginID>
	
Similarly, if we wanted to know who else was logged into the computer type `who` and a list of the users should print to the terminal. While this workshop will not cover every command the `man` will become your best friend. The `man` command prints to the screen the manual page for all other commands recognized by the shell. For example:

	$ man mv
	
	NAME 
		mv - move (rename) files
	SYNOPSIS
		mv [OPTION] ... [-T] SOURCE DEST
		.
		.
		.
	
This command will help you later on when you want to figure out how to use a specific command. 


<!--
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black;">
<td style=" border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi.html">⬅ Content</a></td>
<td style="border:0px solid black; text-align:center;">Introduction</td>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_1.html">Files and Directories</a>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_2.html">Manipulating Files and Directories</a>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_3.html">Pipes and Filters</a>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_4.html">Shell Scripts</a>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_5.html">Finding Things</a>
<td style="border:0px solid black; text-align:center;"><a style="text-decoration:none;" href="./bash_main_multi_1.html"> Next ➡ </a></td>
</table>
-->

<br>
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black; border-top:1px solid #CCC; line-height:300%;">
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">Contents</a></td>
<td style=" border:0px solid black;"></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">⬅ Previous</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="font-weight:bold;" href="./bash_multi_1.html">Introduction</a></td>
<td style="border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_2.html">Next ➡</a></td>
</table>
