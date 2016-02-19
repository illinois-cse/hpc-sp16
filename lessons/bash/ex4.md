# Exercises. Part 4

-   Suppose that `ls` initially displays:
    
```
fructose.dat    glucose.dat   sucrose.dat
```
    
What is the output of:
    
```
for datafile in *.dat
do    
    ls *.dat
done
```

-   In the same directory, what is the effect of this loop?
    
```
for sugar in *.dat
do
    echo $sugar
    cat $sugar > xylose.dat
done
```
    
1. Prints fructose.dat, glucose.dat, and sucrose.dat, and copies sucrose.dat to create xylose.dat.
2. Prints fructose.dat, glucose.dat, and sucrose.dat, and concatenates all three files to create xylose.dat.
3. Prints fructose.dat, glucose.dat, sucrose.dat, and xylose.dat, and copies sucrose.dat to create xylose.dat.
4. None of the above.

-   `expr` does very simple arithmetic using command-line parameters:
    
```
$ expr 3 + 5
8
$ expr 30 / 5 - 2
4
```
    
Given this, what is the output of:
    
```
for left in 2 3
do
    for right in $left
    do
        expr $left + $right
    done
done
```

-   What is the problem with multiplication with `expr`?  Can you _escape_ the `*` so that it works as expected?
