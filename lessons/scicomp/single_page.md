[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/)

# Scientific Computing on a Cluster
#### [CSE Training](cse.illinois.edu/training) • Spring 2016

This workshop is intended to give you a whirlwind tour of the issues underlying scientific computing, particularly as that is executed today on distributed clusters.  What you should walk out of here with today is at least a list of topics to dig deeper into, because semester-long courses could be written with the outline we use to introduce scientific computing.



## What is Scientific Computing?
*   Building computational models of real-life (physical, chemical, biological,...) phenomena
*   Often requires massive linear-algebraic solution methods—thus **HPC**
*   This workshop is designed to answer the question:<br>
 	 "I've got an account on a supercomputer (cluster) — what do I do?"


## What is High-Performance Computing (HPC)?

<!--
[Slides](http://slides.com/uiuc-cse/hpc-fa14-2#/)
-->

#### Strategies

<div style="margin:0; width:100%;text-align:right; font-size:18px;">
<a href="http://www.cray.com/company/history/seymour-cray"><img src="./img/SeymourCray_retouched.jpg" alt="Seymour Cray"></a><br>
If you were plowing a field, which would you rather use: Two strong oxen or 1024 chickens?
<p style="text-align:right; margin-top:0;"><b>--- Seymour Cray</b></p>
</div>

#### Concepts
-   **vectorization**: single operation across multiple data
-   **distributed computing**: multiple units on multiple data for same overall process
-   **threading**: context-switching processes operating over multiple control flows or multiple data
-   ([Davis et al. 2012](http://link.springer.com/article/10.1007%2Fs11227-012-0789-3))


#### Hardware mapping
-   **multicore**
-   **GPGPU**
-   **cluster** (nodes and head node)

<br>

####  Scalability
Let's imagine we are solving a problem of size **N** (that is, we have to make **N** operations) and there is **P** processing elements (CPUs, cores, processes, threads, *etc.*) at our disposal. To execute code on a massively parallel machine, we have to be sure that our code effectively uses computer resourses (time- and energy-wise). We can measure how much faster the computer code that performs these operations is by calculating its speedup when we use more processing element:

-   **Speedup**
    $$ S\left(\rm N, P\right) = \dfrac{time\,({\rm N, 1})}{time\,(\rm N, P)} $$
    

-   **Strong scaling**<br>
    For tasks that require a lot of computational time (*i.e.* CPU-bound tasks), a better measure is the so-called **strong scaling**. It tells us how the solution time varies with the *number of processors* **P** for a fixed **total problem size** ***N***.
    $$W\left(\rm N, P\right) = \dfrac{time\,(\rm N, 1)}{{\rm P} \cdot time\,(\rm N, P)}=\dfrac{S(\rm N, P)}{\rm P}$$
    Usually, the goal is to find the optimum number of processing units that gives reasonable performance at an affordable computational cost.


-   **Weak scaling**<br>
    For tasks that require a lot of computational resources other than time (*e.g.* memory, in which case the task is called memory-bound), a better measure is the so-called **weak scaling**. It tells us how the solution time varies with the *number of processors* **P** for a fixed problem size **per processor** ***n = N / P***.
    $$E({\rm N, P}) = \dfrac{time\,(\rm N, 1)}{time\,(\rm N\cdot P,P)}$$


#### Implementations (software libraries)
-   **Architecture**:  MPI, OpenMP, CUDA/OpenCL
-   **Numerics**:  BLAS, LAPACK, GNU SL, Intel MKL, Trilinos
<br>
<br>

## Executing Scientific Code

#### 1. Shells & architecture

99.999% of a time, you will be accesssing a supercomputer (*i.e.*, a **cluster** of computers) remotely.<br>
99.999% of a time, you will be using `ssh` program to do that.

<br>
<div style="width:80%!important; margin:0 auto;">
<img src="./img/cluster.svg">
</div>

#### 2. Environment
Be aware of the **environment**:  `$PATH`, `$LD_LIBRARY_PATH`, `module`

#### 3. Queueing / Scheduling

Most popular queueing systems are: PBS and slurm.<br>
**PBS**: Portable Batch System<br>
**SLURM**:  Simple Linux Utility for Resource Management<br>
All of them require the so-called **submission scripts**, that are **shell scripts** (bash, sh, ksh, zsh, csh) with a set of special commands to the queueing system.

#### 4. Job Scripts (`mpiexec`, etc.)

Remember, you **can not** do a simple `./myprogram.exe`.<br> You always have to do something like `mpiexec -n 16 ./a.out`. 

#### 5. Checkpoint often if your code supports it.

This is a common sense when working on a supercomputer. You don't want to lose a lot of time when emergency happens. 

<br><br>


## Compiling Scientific Code

```
wget https://github.com/maxim-belkin/hpc-sp16/raw/gh-pages/lessons/scicomp/hpc-code-examples.tar.gz
tar -xvzf hpc-code-examples.tar.gz
module load gcc
```

#### Compiling & building (`gcc`, `make`)
-  `$LD_LIBRARY_PATH`
-   Examples:  OpenMP, MPI, GNU SL, Intel MKL
    - MPI:  why would you want to request fewer cores per node?

##### Common workflow:
-   `./configure && make && make install`
    -   `mpicc` compiler wrapper including MPI headers and linked libraries
    -   `-show`, `-std=c99`, `-o`
    -   OpenMP:  `$OMP_NUM_THREADS` environment variable
    -   local installations (`ln` and `~/bin`)
    -   troubleshooting with libraries:  try `ldd mpiexec`

<br><br>

## Developing Scientific Code

<br>

<div style="margin:0; width:100%;text-align:right; font-size:18px;">
Why do we never have time to do it right, but always have time to DO IT OVER?
<p style="text-align:right; margin-top:0;"><b>--- Anonymous</b></p>
</div>

- Design (and only) then code.

- Daisie Huang [Scientific coding and software engineering: what's the difference?](http://www.software.ac.uk/blog/2015-02-06-scientific-coding-and-software-engineering-whats-difference)

- Carry out studies of the strong and weak scaling, as well as profiling so that you aren't wasting cluster cycles.


### Design

*Design* refers to the decisions you need to make about what the software will do and how it will work.  This includes deciding the language and libraries that you require, and the target platform.

- Modularize your code as much as practical.

- Don't reinvent the wheel—find existing libraries:  Boost, SciPy, Netlib, Scalapack, PETSc, etc.

-   Language support and libraries for HPC
    -   Fortran; C/C++; Python; R; MATLAB (why to choose each)
    -   MKL (BLAS/LAPACK/ScaLAPACK,BLACS), OpenBLAS; CUDA; MVAPICH2, OpenMPI;
        GSL; Boost; PETSc
    -   MPI:  MVAPICH2 v. OpenMPI:  broadly speaking, MVAPICH2 exhibits better
        scaling than OpenMPI for many problems at higher numbers of nodes
        and bandwidth [source](http://hpc.inspur.com/images/News/2012/11/23/11EB9AD954D64F86AF46AADB2ECF289E.pdf)
    -   Compiler versions and features (Intel, GCC (esp. 4.9+))
    -   [Language microbenchmarks across languages](http://julialang.org/benchmarks/)


### Construction

*Construction* refers to the process of actually coding the software.

You are not a serious software developer.  That is not to say that you are not serious, nor that you do not develop software; however, you think of yourself as an engineer first and as a coder only incidentally.

There are extremely sophisticated tool chains in use in software development today, but we are going to highlight only a few immediately useful selections.

#### External to coding
- Take the time to learn your development environment of choice well—there are language-aware code editors including code completion:  IDEs (Eclipse, XCode), `vi` (YouCompleteMe), `emacs`.

- Write self-documenting code:  good variable and function names that follow a convention.  If you don't have a convention yet, look at a lot of code on GitHub and see what you like, but be consistent.
    -   What does "using a convention" mean?
    -   [GNU coding standards](https://www.gnu.org/prep/standards/html_node/index.html)


- Use a compilation system:
    - [Make](https://www.gnu.org/software/make/)
    - [CMake](http://www.cmake.org/)
    - [GNU Autotools](https://en.wikipedia.org/wiki/GNU_build_system) (`./configure && make && make install`), etc.
    [Autotools tutorial](https://www.lrde.epita.fr/~adl/autotools.html)
    -    This also lets you query the hardware to optimize at compile time.

            >configure.ac
                AC_INIT(cache_test.c)
                AM_INIT_AUTOMAKE(cache_test, 1.0)
                : ${CFLAGS="-O2 -std=c99"}
                AC_PROG_CC
                AC_OUTPUT(Makefile)
            aclocal
            autoconf
            >Makefile.am
                bin_PROGRAMS = cache_test
                cache_test_SOURCES = cache_test.c
            automake --add-missing
            touch NEWS README AUTHORS ChangeLog

            ./configure
            make
        
        -   [Overview of Autotools toolchain](http://ptgmedia.pearsoncmg.com/images/1578701902/samplechapter/1578701902.pdf)

- Use version control:  **Git**, SVN, Mercurial, etc.
    -   `git clone https://github.com/losalamos/CLAMR`

- Use an issue-tracking system:  **GitHub**, Bugzilla, etc.

- Don't create new file formats:  find something existing that works (`HDF5`, `PDB`, `XYZ`, etc.).

#### Internal to coding
- Use configuration files and command-line flags rather than hard-coding values.

- Compile with all debug flags set (`-Wall -Werror -g`), and aim to compile with zero warnings.

- Avoid loops (they "cost" computer time).  Unroll them if you must use them.

- Optimize aggressively (`gcc -O3`) only after you've finished debugging the code.

Other potentially useful utilities include documentation generators and integrated development environments.


### Access

- Always include certain standard files when distributing your software:  `README`, `INSTALL`, `CITATION`, `LICENSE`.

- Have a long-term data management plan (now a requirement for NSF, other grants).
    - http://www.ljmu.ac.uk/lea/77337.htm
    - dryad, re3, research data service


### Testing


<div style="margin:0; width:100%;text-align:right; font-size:18px;">
Before software can be reusable it first has to be usable.
<p style="text-align:right; margin-top:0;"><b>--- Ralph Johnson </b></p>
</div>

- Learn to use (and then actually use!) debugging and profiling tools.

    - Debuggers let you step through your code line-by-line and view the contents of variables and the results of evaluations _interactively_.  (This is invaluable for C/C++/Fortran programming.)
    	- [`gdb`](https://www.gnu.org/software/gdb/)
    	- `lldb` (if you are developing code on a Mac)
    
    - Profilers query the code frequently to build up a picture of how often your execution point is in any one part of the program.  This lets you characterize performance and identify bottlenecks.
    	- `gprof`
    	- [TAU](https://www.cs.uoregon.edu/research/tau/home.php)
    	- [Valgrind]() is an extremely versatile tool which lets you characterize memory performance, find memory leaks, and profile your code.  `memcheck` and `cachegrind` are two of the most commonly used utilities.

```
$ module load valgrind
$ valgrind --tool=memcheck --leak-check=yes --show-reachable=yes -v ./cache_test 10000
==12877== Memcheck, a memory error detector
==12877== Copyright (C) 2002-2013, and GNU GPL'd, by Julian Seward et al.
==12877== Using Valgrind-3.9.0 and LibVEX; rerun with -h for copyright info
==12877== Command: ./cache_test 10000
...
--12877-- Valgrind library directory: /usr/local/apps/valgrind/3.9.0/lib/valgrind
...
Matrix size:  10000x10000
--12877-- REDIR: 0x4eaa520 (free) redirected to 0x4c273fd (free)
--12877-- REDIR: 0x4ea9640 (malloc) redirected to 0x4c27a23 (malloc)
==12877== 
==12877== HEAP SUMMARY:
==12877==     in use at exit: 0 bytes in 0 blocks
==12877==   total heap usage: 10,001 allocs, 10,001 frees, 400,080,000 bytes allocated
==12877== 
==12877== All heap blocks were freed -- no leaks are possible
==12877== 
==12877== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 6 from 6)
--12877-- 
--12877-- used_suppression:      6 dl-hack3-cond-1 /usr/local/apps/valgrind/3.9.0/lib/valgrind/default.supp:1196
==12877== 
==12877== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 6 from 6)
  
$ valgrind --tool=cachegrind ./cache_test 10000
==12881== Cachegrind, a cache and branch-prediction profiler
==12881== Copyright (C) 2002-2013, and GNU GPL'd, by Nicholas Nethercote et al.
==12881== Using Valgrind-3.9.0 and LibVEX; rerun with -h for copyright info
==12881== Command: ./cache_test 10000
==12881== 
--12881-- warning: L3 cache found, using its data for the LL simulation.
Matrix size:  10000x10000
==12881== 
==12881== I   refs:      504,082,163
==12881== I1  misses:            868
==12881== LLi misses:            860
==12881== I1  miss rate:        0.00%
==12881== LLi miss rate:        0.00%
==12881== 
==12881== D   refs:      201,473,856  (100,934,392 rd   + 100,539,464 wr)
==12881== D1  misses:    112,537,715  ( 12,524,791 rd   + 100,012,924 wr)
==12881== LLd misses:     97,883,166  (     54,665 rd   +  97,828,501 wr)
==12881== D1  miss rate:        55.8% (       12.4%     +        99.4%  )
==12881== LLd miss rate:        48.5% (        0.0%     +        97.3%  )
==12881== 
==12881== LL refs:       112,538,583  ( 12,525,659 rd   + 100,012,924 wr)
==12881== LL misses:      97,884,026  (     55,525 rd   +  97,828,501 wr)
==12881== LL miss rate:         13.8% (        0.0%     +        97.3%  )
```

First, learn to use debugging and profiling tools.  Two that are supported on Campus Cluster are `gdb` and `valgrind`.  `gdb`, the GNU Debugger, is designed to work with many programming languages besides C, but it can be painful to get it to work with a parallel program.  (Actually, any parallel debugging is uniquely painful.)  Anyway, if you intend to use `gdb`, you need to compile your code using the `-g` flag and `gcc`.

The other tool, `valgrind`, monitors memory behavior.  It can detect cache misses, memory leaks, and other problems which can lead to poor code performance and excessive memory demand.

- Develop and use a unit-testing scheme (even a simple one).
    Unit tests are ways of (1) confirming that the code you write runs as it should; and (2) verifying that changes you have made to a function do not break expected functionality.
    Now, formally, you're supposed to write the tests before you write the code, but most of us engineers don't map out our code ahead of time so specifically that that's feasible.  So we'll just look at an example of the type of tests you can do.

    -   `interval`
            git clone https://github.com/uiuc-cse/interval.git

    - [Stack Overflow:  Is it worthwhile to write unit tests for scientific research codes?](https://scicomp.stackexchange.com/questions/206/is-it-worthwhile-to-write-unit-tests-for-scientific-research-codes)

    - [Check](http://check.sourceforge.net/) is a unit-testing framework for C code.  


### Debugging

<div style="margin:0; width:100%;text-align:right; font-size:18px;">
It’s hard enough to find an error in your code when you’re looking for it;<br> its even harder when you’ve _assumed_ your code is _error-free_.
<p style="text-align:right; margin-top:0;"><b>--- Steve McConnell </b></p>
</div>

-   Your confusion is a clue that something is wrong—don't ignore it.
    -   Either your mental model of what the code is doing is wrong;
    -   or the model you have built isn't correct for the problem you've set it.

-   <div style="margin:0; width:100%;text-align:right; font-size:18px;">
Premature optimization is the root of all evil.
<p style="text-align:right; margin-top:0;"><b>--- Donald Knuth </b></p>
</div>


-   `gdb` is a representative debugger.  Graphical interfaces for this and other tools exist, but behind the scenes they are just interacting with this program.

[![](http://imgs.xkcd.com/comics/future_self.png)](http://xkcd.com/)

-   Numerical error worksheet ([`numerical-error.ipynb`](https://github.com/maxim-belkin/hpc-sp16/raw/gh-pages/lessons/scicomp/numerical-error.ipynb))
To enable jupyter notebook:<br>

```
source /class/cs101/etc/venv/cse/bin/activate /class/cs101/etc/venv/cse/
jupyter notebook
```

[![](https://bytebucket.org/davis68/resources/raw/f7c98d2b95e961fae257707e22a58fa1a2c36bec/logos/baseline_cse_wdmk.png?token=be4cc41d4b2afe594f5b1570a3c5aad96a65f0d6)](http://cse.illinois.edu/)
