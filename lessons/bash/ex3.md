# Exercises. Part 3

-   The following command will invoke a program called Git to download some Python files.
```
$ git clone https://github.com/uiuc-cse/rankine.git
```     
    Execute this line and then go into the directory `rankine` and list its contents.
    These scripts are designed to input and output their data through streams.
    For instance, execute `python grab_stations.py `. 
    
    -   What is the output?
    -   How can we capture this output as a file?
    -   The programs are designed to work in series:<br>
        `grab_stations.py` feeds data into `grab_forecast.py` <br>
        `grab_forecast.py` feeds data into `plot_forecast.py`.<br>
        Write a single line command to effect this entire process.

<!--
```
python grab-stations.py > stations.txt
python grab-forecast.py < stations.txt > forecast.txt
python plot-forecast.py < forecast.txt
```
-->

####Navigate to the `data/pipes` directory for the following exercises.

-   If we run sort on the file `numbers.txt`, what is the output?  If we run
    `sort -n` on the same input, what do we get instead? why `-n`
    has this effect.

-   What is the difference between
    `$ wc -l < mydata.dat`
    and
    `$ wc -l mydata.dat`

-   The command `uniq` removes adjacent duplicated lines from its input.
    For example, run the following commands:
    
```
$ cat salmon.txt
$ uniq salmon.txt
```

- Why do you think `uniq` only removes adjacent duplicated lines<sup>*</sup>?<br>
&nbsp;<sub> ***Hint**: think about very large data sets.</sub><br><br>
- Which other command could you combine with it in a pipe to remove all duplicated lines?

-   Examine the file called `animals.txt` using less.  What text passes through
    each of the pipes and the final redirect in the pipeline below?
    
```
$ cat animals.txt | head -5 | tail -3 | sort -r > final.txt
```

-   The command:

```    
$ cut -d, -f 2 animals.txt
``` 
produces the following output:
    
```
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```
    
- What other command(s) could be added to this in a pipeline to find out what animals the file contains (without any duplicates in their names)?