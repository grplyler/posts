+++
author = "Ryan Plyler"
title = "How to read and write CSV files in Python"
date = "2020-09-17"
description = "How to read write and parse CSV files in Python"
tags = [
    "csv",
    "python",
    "data science"
]
categories = [
    "python",
    "snippets",
    "howto",
]
+++

Reading and writing `CSV` files it probably something you'll do at least once or twice in your
technical career. Python makes that pretty easy with a standard library module, `csv`.
Read on to view copy-paste solutions for reading and writing CSV files in python.

## The Data

Here's the data we'll be working with. This is an example from a little coursework manager
I wrote called `tuepy`. You can find the full source for that little project at [https://github.com/grplyler/tuepy](https://github.com/grplyler/tuepy)

Here's our csv data:

```
class,week,title,progress,type
BUSI 240,3,Reply 1,100,assign
BUSI 240,3,Reply 2,100,assign
BUSI 240,3,Chapter 5,100,study
BUSI 240,3,Chapter 5 HW,100,study
BUSI 240,3,Chapter 6,100,study
BUSI 240,3,Chapter 6 HW,100,study
BUSI 240,3,"Quiz 3 Chs. 5,6",100,assign
CSIS 310,3,Project 01,100,assign
CSIS 340,3,Read NIST Document,100,study
CSIS 340,3,Flipped Classroom Activities,100,assign
CSIS 352,3,Eckert Ch. 3,100,study
CSIS 352,3,Tomsho Ch. 2,100,study
CSIS 352,3,In-class Activity 1,100,study
CSIS 352,3,In-class Activity 2,100,study
CSIS 474,3,Chapter 10,0,study
CSIS 474,3,Chapter 11,50,study
BUSI 240,4,"Quiz 4, Ch. 7",0,assign
BUSI 240,4,Chapter 7,0,study
BUSI 240,4,Chapter 7 HW,0,study
BUSI 240,4,Presentation - Decision Making,0,assign
CSIS 310,4,In-Class 02,100,assign
CSIS 340,4,A/R-4 - Common Security Threats,0,assign
CSIS 340,4,Kim Ch 3. Networks,0,study
CSIS 340,4,Flipped Classroom Activities,0,assign
CSIS 352,4,Tomsho Ch. 3,0,study
CSIS 352,4,Eckert Ch. 4,0,study
CSIS 352,4,In-Class Activity,100,assign
CSIS 474,4,Sprint 1 Deliverables,15,assign
CSIS 474,4,Team Review,0,assign
CSIS 474,4,Sign NDA,0,assign
```

The structure of this data is as follows: `class`,`week`,`task`,`progress`,`type`

## Reading CSV Files

The following code loops over the csv rows and prints them out.

```python
import csv

with open("data.csv") as datafile:
    csvreader = csv.reader(datafile)

    for row in csvreader:
        print(row)
```

And if you wanted to skip the header row, simple add `next(csvreader)` before
the for loop to advance the reader one row.

```python
import csv

with open("data.csv") as datafile:
    csvreader = csv.reader(datafile)
    next(csvreader)
    for row in csvreader:
        print(row)
```

## Writing CSV Files

Writing csv is also pretty trivial:

```python
import csv

data = [
    ["CSIS 310", "4", "Build Portfolio Website", 100, "assign"],
    ["CSIS 310", "4", "Quiz 5", 100, "assign"],
    ["BUSI 240", "4", "Chatper 4", 50, "study"]
]
with open("data.csv", "w") as datafile:

    csvwriter = csv.writer(csvfile)

    # Write headers (optional)
    csvwriter.writerow(["class", "week","task","progress","type"])

    for row in data:
        csvwriter.writerow(row)
```

By using the `with` keyword, resources are freed automatically when the code block exists.

