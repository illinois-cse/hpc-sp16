[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/training)

## <a name="pipesfilters"></a><a href="#contents" style="text-decoration:none; color:black;">Pipes and Filters</a>

When we type a command or run a program we will get an output printed to the terminal. Pipes can redirect a command or a program's output to a file for future reference or to be used at a later time. In this section you will learn how to use the pipes and how to combine pipes into powerful single-purpose programs. 

The first command to learn is `>`. This pipe, used as `command > file` redirects a command's output to a file. For example:

	$ ls  
	theme.mp3 boss.mp3
	$ ls > output.txt
	$ cat output.txt
	theme.mp3
	boss.mp3
	
Sometimes you run into the problem of redirection mutliple outputs to a single file. If you use the `>` command the original file contents will be overwritten. To append new outputs to a file you can use the command `>>`. For example:

	$ cat output.txt
	theme.mp3
	boss.mp3
	$ echo Hello! >> output.txt
	$ cat output.txt
	theme.mp3
	boss.mp3
	Hello!
		
If you would like to read the contents of a file to use in your command you can use the `<` command. In this case instead of redirecting an output to a file you are redirecting a file's contents into the input of command. For example:

	$ rm *.mp3 < output.txt 
	$ cat output.txt
	Hello!

Sometimes in order to combine two command line steps you can use a pipeline. That is you can use the output of one file into the input of another file using the `|` command. For example:

	$ ls
	dir5 dir37 dir40 file1.txt 
	file2.txt music papers
	$ ls | head -3
	dir5 dir37 dir40

###Do [Exercise #3](./ex3.html)

<br>
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black; border-top:1px solid #CCC; line-height:300%;">
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">Contents</a></td>
<td style=" border:0px solid black;"></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_3.html">⬅ Previous</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="font-weight:bold;" href="./bash_multi_4.html">Pipes and Filters</a></td>
<td style="border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_5.html">Next ➡</a></td>
</table>
