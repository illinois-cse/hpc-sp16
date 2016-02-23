[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/training)

## <a name="shellscripts"></a><a href="#contents" style="text-decoration:none; color:black;">Shell Scripts</a>

There will come a time when using bash that typing in specific commands in the command line will become cumbersome. This is where shell scripts come in. A user can write a series of commands in a shell script that the computer will then execute sequencially. It is important to know that commands that work on the command line will work the same way when implemented in a script. Likewise if a series of commands are implemented in a script, the same result will occur if the user inputs the commands manually in the command line. The following section will introduce the concept of shell scripts, how to write them, and how to exectue them. 

Consider the following simple script:
	
	#!/bin/bash
	echo This script lists the files in the directory
	ls

Lets break down the script and how its works. In the first line you'll see `#!/bin/bash` is written. Every shell script should start with this exact line, this tells Linux which interpreter to use for this file. The second command is the `echo` command which prints everything that follows it. And finally we have the `ls` command which just lists the directory. If a user were to execute this series of command manually it would look like this:

	$ echo This script lists the files in the directory
	This script lists the files in the directory
	$ ls
	bin data home usr
	
	
Remember that Linux is an extensionless system therefore when writing a shell script you don't have to append the `.sh` extension, however doing this will help you identify which files are shell scripts and which are not. 

In a shell script lines that start with `#` are considered comments and will not be interpreted. There are some exeptions however, including the first line of every script. 

You can also declare variables within a shell script. This can be done in the following way:

	#!/bin/bash
	# Declare variable
	str='Hello World!'
	echo $str
	
Notice that when we are defining the variable there are no spaces on either side of the `=` sign. Addtionally when you want to refer to the varible you have to place `$` sign right infront of the variable to signify that you are refereing to a variable. The previous script will output:

	$ ./script.sh
	Hello World!
	
To run the shell script we typed `./` and then the filename. Remember a few sections back that `.` specifies the current directory. When executing a shell script you are essentially telling the computer that the script you are attempting to execute is in the current directory. An absolute path would also work. If the script in is the directory above your current directory you could use `../` to run the script. 

It may be the case that when you write a shell script your system does not yet know it's an executable script. To change this adjust the permissions on the file by typing:
	
	$ chmod +x script.sh

There are a few automaticly set variables when running a script. These are: 

`$0`: The name script filename

`$1`...`$9`: The command line arguements

`$#`: The number of command line arguements

`$*`: All of the command line arguements

As in any other progamming language you can also implement `if`,`else`,`fi` statments, `for` loops, and `while` loops. For example you can write the following in a script:

	#!/bin/bash
	count=100
	if [ $count -eq 100 ]
	then 
		echo "Count is 100"
	else 
		echo "Count is not 100"
	fi

This script defines the variable `count` and executes the `echo` command if the variable `count` equals a certain value. Notice that the statement ends with `fi`. Sometimes it is useful to run a command until a certain requirement is met. For example, lets consider the following `while` loop:

	#!/bin/bash
	count=1
	while(($n <= 5))
	do 
		echo "This loop has run $n times"
		n=$((n+1))
	done
	
The output of this script will be:

	This loop has run 1 times
	This loop has run 2 times
	This loop has run 3 times
	This loop has run 4 times
	This loop has run 5 times
	
Take a look at the structure of the while loop. The basic structure of the while loop can be broken down to:
	
	while <condition>
	do
		<commands>
	done

Similar to the `while` loop, the `for` loop will execute a command a command a number of times. However instead of executing the command untl a condition is met a `for` loop will only execute the command for a pre-specified number of times. For example:

	#!/bin/bash
	for value in {1..5}
	do 
		echo "This loop has run $n times"
	done	 

This loop will produce the exact same result as the `while` loop. However you are not limited to just numerical values. You can also execute a command based on the items within a variable. This could be 

	names='Name1 Name2 Name3'
	
More advanced loop could include the `break` and `continue` commands. The `break` command tells bash to exit the loop when a condition is met. The `continue` command tells bash to skip the current iteration and move on to the next iteration within the loop. For example:

	#!/bin/bash
	for value in {1..10}
	do 
		if [ $value -eq 5 ]
		then
			echo The current count is $value
			continue
		fi
		if [ $value -eq 7 ]
		then
			echo The count is $value
			echo Now exiting loop
			break
		fi
	done
	
You can also prompt the user to select from a list of choices using the `select`,`do`,`done` sequence. For example the following script will prompt the user to run or quit:

	#!/bin/bash
	options='Continue Quit'
	PS3='Choose 1) or 2) to Continue or Quit: '
	select option in $options
	do
		if [ $option == 'Continue' ]
		then
			continue
		fi
		if [ $option == 'Quit' ]
		then
			break
		fi
	done
	
###Do [Exercise #5](./ex5.html)

<br>
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black; border-top:1px solid #CCC; line-height:300%;">
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">Contents</a></td>
<td style=" border:0px solid black;"></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_4.html">⬅ Previous</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="font-weight:bold;" href="./bash_multi_5.html">Shell Scripts</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_6.html">Next ➡</a></td>
</table>

