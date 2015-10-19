# Computational Python

## Olav Vahtras

KTH

---

layout: false


## Scripting overview

### Scripts

* Programs in a flexible high-level language
* Interpreted 
* Not compiled (as C, C++, Fortran)
* Examples: python, perl, sed, awk, bash, ruby, tcl

---

## Bash

* Bourne-again shell: http://www.gnu.org/software/bash
* Some combinations of commands are used often
* Collect command-line commands in a file
* Execute file

### To execute a bash script

* Collect the commands in file ``filename``

```bash
    $ bash filename
```

* if the first line is 

```
    #!/bin/bash 
then  make the file executable and run

```bash
    $ chmod +x filename
    $ ./filename
```
---

### Shell syntax

Basic support for looping

```bash
    $ for i in a b c; do echo $i; done
    a
    b
    c
```

and branching

```
    $ if -n "$var" ; then echo yes; else echo no; fi
```

Note the semi-colon (before do, before done)

---

### Example

A sample submit script 

```bash
    #!/bin/bash
    module add mpi
    processes_per_node=8
    total_processes=`expr $processes_per_node \* $SP_PROCS`
    PRG="$1"
    shift
    ARGS="$*"
    mpirun -np $total_processes -machinefile $SP_HOSTFILE $PRG $ARGS
```


* The first line tells the shell which program to execute the commands
* module sets up and redefines environment variables
* define a local shell variable ppn
* define total as the output of another shell command
* set PRG to the first argument
* set ARGS to the remaining argument
* execute the parallel program

---

### Sed

* stream editor
* A version of the unix editor line-based editor 'ed'
* not for files
* does operations on stdin
* puts results on stdout


    $ echo yo | sed "s/o/es/"
    yes

---
### Awk

* Text processing languange
* Named after its authors (Aho-Weinberger-Kernighan)
* Structure /regexp/ {command}
* When processing a text file, if  a line matches the rule (regexp) execute (command) on the line. 

```
    $ awk '{length > 72}' filename
```

```
    $ awk -F : '/^olav/ {print $6}' /etc/passwd
    /home/olav
```

---
### Perl

* Practical extraction and report language
* Advanced text processing
* Complex data structures
* Object-oriented programming model
* And much more...

--

### but...

Andreas Stefik, Susanna Siebert, Melissa Stefik, and Kim Slattery: An Empirical Comparison of the Accuracy Rates of Novices using the Quorum, Perl, and Randomo Programming Languages. PLATEAU 2011.

*We present here an empirical study comparing the accuracy rates of novices writing software in three programming languages: Quorum, Perl, and Randomo. ... 
Results showed that while Quorum users were afforded significantly greater accuracy compared to those using Perl and Randomo, **Perl users were unable to write programs more accurately than those using a language designed by chance.** *


---
### Why python?

* Simple syntax - easy to learn
* Powerful language
* Fast development time
* Fun

---

### Python 2 or 3?

* Slightly incompatible
* Most differences deal with text

--
```
    print "hello"   #2. A statement
    print("hello") #3. A function call
```

* Python 2 is more supported
* on a systems you do not control Python 2 is most likely to be installed

---

### What does the literature recommend?  2 or 3?

> *A programmer may try to get you to install Python 3 and learn that. Say, "When all of the Python code on your computer is Python 3, then I'll try to learn it." That should keep them busy for about 10 years. I repeat, do not use Python 3. Python 3 is not used very much, and if you learn Python 2 you can easily learn Python 3 when you need it. If you learn Python 3 then you'll still have to learn Python 2 to get anything done. Just learn Python 2 and ignore people saying Python 3 is the future.*

Learn Python the Hard Way, Zed A. Shaw

--

> *Python 3.0 introduced a number of backward-incompatible changes to the language, so we expect that most major Python libraries and frameworks, including Django, will take a few years to catch up. If you're new to python and wondering whether to learn Python 2.x or Python 3.x, out advice is to stick with Python 2.x.*

The definitive guide to Django, Adrian Holovaty and Jacob Kaplan-Moss

---

> *Python 3.0 is really only suitable for experimental use by seasoned Python veterans. If you are looking for stability and production quality code, stick with Python 2.x ...*

Python Essential Reference, David M. Beazly

--

### On the other hand

> *For both Ubuntu and Debian, we have ongoing project goals to make Python 3 the default, preferred Python version in the distros*

> *What this does not mean:*

> */usr/bin/python will point to Python 3. No, this is not going to happen (unless PEP 394 advocates otherwise, which is doubtful for the foreseeable future). /usr/bin/python and /usr/bin/python2 will point to Python 2.7 and /usr/bin/python3 will point to the latest supported Python 3 version.  Python 2 will be removed from the archive. No, this is not going to happen. We expect Python 2.7 to remain supported and available in Ubuntu for quite a long time, given that PEP 373 promises upstream bug fix maintenance support until 2020*

<https://wiki.ubuntu.com/Python/3>
