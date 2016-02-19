# Exercises. Part 6

-   Write a short explanatory comment for the following shell script:

```
$ find . -name '*.dat' -print | wc -l | sort -n
```

-   The `-v` flag to grep inverts pattern matching, so that only lines which
    _do not_ match the pattern are printed.  Given that, which of the following
    commands will find all files in `data/chem/pdb` whose names end in `ose.dat`
    (_e.g._, `sucrose.dat` or `maltose.dat`), but do not contain the string `temp`?

``` 
1. $ find data/chem/pdb -name '*.pdb' -print | grep ose | grep -v temp
2. $ find data/chem/pdb -name ose.pdb -print | grep -v temp
3. $ grep -v temp $(find data/chem/pdb -name '*ose.pdb' -print)
4. None of the above.
```

