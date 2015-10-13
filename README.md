# Ditch Excel
## Is it time for you to ditch Excel and start using Python at work? Probably

It wont be that difficult. We just need to break the tasks into deal-with-able parts.

Part 1: [Breaking a field containing three elements into three fields]()

##### Breakding a field containing three elements into three fields
Description:
"My data set is set up like:

| Field 1       | Field 2       | Field 3 |
| ------------- |:-------------:|:-------:|
| x1a, x1b, x1c | y1            | z1      |
| x2a, x2b, x2c | y2            | z2      |
| x3a, x3b, x3c | y3            | z3      |

Look how Field 1 has more than one piece of information in it! What I *want* it to look like is:

| Field 1a      |Field 1b        |Field 1c        | Field 2       | Field 3 |
| --------------| -------------- | -------------- |:-------------:|:-------:|
| x1a           |  x1b           | x1c            | y1            | z1      |
| x2a           | x2b            | x2c            | y2            | z2      |
| x3a           | x3b            | x3c            | y3            | z3      |

To do that with python, we can use the code below: 
