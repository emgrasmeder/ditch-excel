# Ditch Excel
## Is it time for you to ditch Excel and start using Python at work? Probably

It wont be that difficult. We just need to break the tasks into deal-with-able parts.

Part 1: [Breaking a field containing three elements into three fields]()

##### Breakding a field containing three elements into three fields
Description:
"My data set is set up like:

| Field 1   | Field 2       | Field 3 |
| --------- |:-------------:|:-------:|
| A, C, D,  | y1            | z1      |
| A, B, D   | y2            | z2      |
| B, C      | y3            | z3      |

Look how Field 1 has more than one piece of information in it! What I *want* it to look like is:

| A             | B              | C              | D             |    Field 2       | Field 3 |
|:-------------:|:--------------:|:--------------:|:-------------:|:----------------:|:-------:|
| 1             | 0              | 1              | 1             | y1               | z1      |
| 1             | 1              | 0              | 1             | y2               | z2      |
| 0             | 1              | 1              | 0             | y3               | z3      |

We want to do that in Python. Although Megan's dataset has over 4,000 records (rows) to it, we're going to use this dataset mock-up to write our code.
If you can do a thing to one row, you can do it to 4,000. We just need to make a `for` loop that `iterates` over the entire file, line by line.
Line 1 will be handled very differently than the rest of the rows. 

For the rest of the rows: Python can very easily split an Excel row into a list, where each column is another item in the list. Therefore, we'll mock the first line of data as:
```python
line1_mock = ["A,C,D", "y1", "z1"]
```
and we want to write a function that turns `line1_mock` into `["1", "0", "1", "0", "y1", "z1"]` assuming "A", "B", "C", and "D" are the only new column headers we're dealing with. 

The easiest way I can think of doing this is to first iterate through the entire file one time to learn how many distinct new columns we'll add, and **then** add a new column for each.

With our single line of mocked data, we can write the function:
```python
def column_name_getter(the_row):
    column names = the_row[0].split(",") #turns "A,C,D" into ["A","C","D"], for example
```
there are several ways I can think of to get a running total of the set of all column names we want. One way to do this:
```python
all_column_names = []
for row in file:
    all_column_names += column_name_getter(row)
all_column_names = list(set(all_column_names))
```
This creates a proper set (like in set theory), which by definition cannot contain repeats, and then makes it a list. We can now append the items in this set to our list of columns.  
