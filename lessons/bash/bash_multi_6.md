[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/training)

## <a name="findingthings"></a><a href="#contents" style="text-decoration:none; color:black;">Finding Things</a>

In this last section of the tutorial you are going to learn about finding useful data within your files. 

The first commmand and most powerful is the `grep` command. Lets say you want to find the line within a file that contains a specific string. We can then use the `grep` command to print that whole line to the terminal. For example lets consider the following file and its contents:

	$ cat example.txt
	This line is about cars.
	This line is about airplanes.
	This line only has one sentence.
	
If we wanted to print to the terminal the line that mentions the string `airplanes` then we can type the following command:

	$ grep 'airplanes' example.txt
	This line is about airplanes.

We could also print to the terminal which line the string is in:

	$ grep -n 'airplanes' example.txt
	2:This line is about airplanes.
	
You can refer to the `man` pages to see all of the available flags with this command. 

Another useful command is the `wc` command. This command will output the word, line, character, and byte count of a file. The information printed can be adjusted based on what flags are attatched when typing the commmand. For example if we want to know the line count of a file:

	$ wc -l example.txt
		3 example.txt

These commands start to become powerful when you have a large amount of files that you want to look through. For example lets you that you have a large amount of files with the *.txt extension and you want to find the number of lines in each of them and print the results to a file. You can type the following

	$ wc -l *.txt > length
	
Another useful command is the `find` command. This command will isolate specific files that it **finds** and execute a specifc command to those files. For example if you want to `rm` all files that fit the `find` condition then you could type:

	$ find ~/ -name '*.txt' -exec rm {} \;

###Do [Exercise #6](./ex6.html)

<br>
<table style="width:100%; border-collapse: collapse; border:0px solid black;" >
<tr style="border:0px solid black; border-top:1px solid #CCC; line-height:300%;">
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi.html">Contents</a></td>
<td style=" border:0px solid black;"></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_5.html">⬅ Previous</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="font-weight:bold;" href="./bash_multi_6.html">Finding Things</a></td>
<td style=" border:0px solid black; text-align:center; font-size:20px;"><a style="text-decoration:none;" href="./bash_multi_7.html">Next ➡</a></td>
</table>


