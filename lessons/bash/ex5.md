# Exercises. Part 5
-   Leah has several hundred data files, each of which is formatted like this:
    
```
2013-11-05,deer,5
2013-11-05,rabbit,22
2013-11-05,raccoon,7
2013-11-06,rabbit,19
2013-11-06,deer,2
2013-11-06,fox,1
2013-11-07,rabbit,18
2013-11-07,bear,1
```
    
-   Write a shell script called `species.sh` that takes any number of
    filenames as command-line parameters, and uses `cut`, `sort`, and `uniq`
    to print a list of the unique species appearing in each of those files
    separately.  (Test this on the files in `data/pipes/animals`)

-   Write a shell script called `longest.sh` that takes the name of a directory
    and a filename extension as its parameters, and prints out the name of the
    most recently modified file in that directory with that extension. For example:

    ```
    $ bash largest.sh /tmp/data pdb
    ```

    would print the name of the `.pdb` file in `/tmp/data` that has been changed
    most recently.

-   If you run the command:
    `history | tail -5 > recent.sh`
    the last command in the file is the `history` command itself, _i.e._, the
    shell has added `history` to the command log before actually running it.
    In fact, the shell always adds commands to the log before running them.
    Why do you think it does this?

-   Joel's data directory contains three files: `fructose.dat`, `glucose.dat`,
    and `sucrose.dat`. Explain what the following script, `example.sh`, would
    do when run as `bash example.sh *.dat`:
    
```
	echo *.*
	for filename in $1 $2 $3
	do
	    cat $filename
	done
	echo $*.dat
```

-   The `history` shows the last thousand or so commands that you've used.  What does this
    code do?  (Test `awk '{print $1}' data/pdb/methane.pdb` to see what this `awk` does.)
    
```
    awk '{print $1}' ~/.bash_history | sort | uniq -c | sort -n | tail -10 | sort -n -r
```
