---
layout: default
title: "Assignment 3: On Target"
---

Design due: **in class** on **Thursday, June 22nd**

MS1 Code due: **Thursday, June 29th** by 11:59 PM

MS2 Code due: **Thursday, July 6th** by 11:59 PM

Getting Started
===============

Start by downloading [CS101\_Assign03.zip](src/CS101_Assign03.zip), saving it in the directory **CS101** within your home directory.

If you are on Windows, start a **Cygwin Bash Shell** and run the following commands:

    cd h:
    cd CS101
    unzip CS101_Assign03.zip
    cd CS101_Assign03

If you are on Linux, start a terminal and run the following commands:

    cd CS101
    unzip CS101_Assign03.zip
    cd CS101_Assign03

Using **Notepad++** (or a Linux text editor such as Pluma), open the file

> **CS101/CS101\_Assign03/OnTarget.cpp**

You will add your code to this file.

When you are ready to compile the program, in the Cygwin bash shell (or Linux terminal) window type the command

    make

To run the program, type the command

    ./OnTarget.exe

# Your tasks

## Design

Your design artifact should contain control flow sketches for:

* generating the scores and storing them in an array
* computing a histogram of the scores

## Program

Your task is to write a program that simulates an archer firing arrows at a target.

The target is a circle whose diameter is 1,900 units.  The center of the target as at the point (0,0).  When an arrow hits the target, its score is calculated based on how far it was from the center of the target:

* If it was within 50 units of the center, it is a bullseye, and earns 1,000 points
* If it was between 50 and 150 units from the center, it earns 900 points
* If it was between 150 and 250 units from the center, it earns 800 points
* etc.

Any arrow more than 950 units from the center misses the target entirely, and earns 0 points.

To simulate firing an arrow, the program should compute random x and y coordinates in the following way.  Compute the sum of 8 random integers whose values are between 0 and 275, inclusive.  Then subtract 1,100 from the sum.  When calculated in this manner, both x and y coordinates will be in the range &plusmn;\[0..1,100\].

You can calculate the distance from an arrow's location and the center of the target by computing the square root of the sum of the squares of the arrow's x and y coordinates.

As a score is computed for each simulated arrow, the program should do two things:

* It should update a histogram array in which the elements store the counts of arrows earning 1,000 points, 900 points, 800 points, etc.
* It should add the score to an overall `scores` array, so that when all of the simulated arrows have been fired, the array records all of the individual scores

The program should simulate firing exactly 1,000 arrows.

The output of the program should consist of two parts.

## Milestone 1

In **Milestone 1**, the first of two milestones, you will produce a "graphical" histogram presenting a visual representation of the number of arrows earning each of the 11 possible scores.  Each character in the bar should represent 5 arrows.  The integer count for each score should be printed.  (Try to match the output shown in the examples as closely as possible.)

Example run:

```
1000: [  36] =======
 900: [ 165] =================================
 800: [ 228] =============================================
 700: [ 223] ============================================
 600: [ 184] ====================================
 500: [ 110] ======================
 400: [  36] =======
 300: [  16] ===
 200: [   2] 
 100: [   0] 
   0: [   0] 
```

## Milestone 2

In **Milestone 2**, you will write functions to compute statistics based on the scores, specifically the *mean*, *median*, and *standard deviation* of the scores. The three functions should be

```c
double computeMean(int arr[], int size);
double computeMedian(int arr[], int size);
double computeStDev(int arr[], int size);
```

Another example run:

```
1000: [  25] =====
 900: [ 167] =================================
 800: [ 278] =======================================================
 700: [ 242] ================================================
 600: [ 157] ===============================
 500: [  94] ==================
 400: [  28] =====
 300: [   6] =
 200: [   3] 
 100: [   0] 
   0: [   0] 
Median score is 700.00
Mean score is 721.90
Standard deviation is 144.19
```

# Hints

When printing the histogram, use field widths to ensure that the figures and the bars align correctly.

To compute the median, it will be helpful to arrange the scores in *sorted* order (from least to greatest).  You can do this by calling the `qsort` function as follows:

```c
qsort(scores, 1000, sizeof(int), compare);
```

This assumes that your array of scores is called `scores`, that the array has `int` elements, and that there are exactly 1,000 elements.  The `compare` function (included in the skeleton file) is used to compare scores.

See the following web page for information about computing standard deviation:

> <http://www.mathsisfun.com/data/standard-deviation.html>

Note that to compute the standard deviation, you need the mean which can be computed using the **computeMean()** function.

# Grading

Your grade (out of 100 points) is determined as follows:

### Milestone 1 (60 points)

* Design artifact: 10 points
* Simulating arrows being fired at the target: 10 points
* Scoring each arrow: 5 points
* Storing scores in an array: 10 points
* Computing histogram of scores: 10 points
* Printing histogram of scores
    * Count for each bucket: 10 points
    * Bar for each bucket: 5 points
    
### Milestone 2 (40 points)

* Computing median: 10 points
* Computing mean: 10 points
* Computing standard deviation: 10 points
* Good coding style: 10 points

<div class="callout">
To earn full credit for coding style, make sure your program uses <b>correct indentation</b>, uses <b>meaningful variable names</b>, and <b>has comments</b> explaining the purpose of each section of code.
</div>

# Submitting

Your design will be checked off in class on the day the designs are due.

To submit your program, make sure your **OnTarget.cpp** file is saved, and in the Cygwin window type type one of the following commands (depending on whether you are submitting **Milestone 1** or **Milestone 2**).

For **Milestone 1**:

    make submit_ms1

File **Milestone 2**:

    make submit_ms2

Enter your Marmoset username and password (which you should have received by email.) Note that your password will not be echoed to the screen. Make sure that after you enter your username and password, you see a message indicating that the submission was successful.

If the **make submit** command does not work, you can [submit using the web interface](../submitting.html) (see the link for details).

**Important**: Make sure that you check the file(s) you submitted to ensure that they are correct. Log into the server using the following URL (also linked off the course homepage):

> <https://cs.ycp.edu/marmoset/>

You should see a list of labs and assignments. In the row for **assign03**, click the link labeled **view**. You will see a list of your submissions. Download the most recent one (which should be listed first). Verify that it contains the correct files.

**You are responsible for making sure that your submission contains the correct file(s).**

<!-- vim:set wrap: -->
<!-- vim:set linebreak: -->
<!-- vim:set nolist: -->
