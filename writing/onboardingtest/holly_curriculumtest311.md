<!--title={Working within a box: box()}-->

<!--badges={Algorithmns:36}-->

<!--concepts{Indexing 2D Lists, For Loops}-->

# Working Within a Box


Step 1: Define variable to check if square is empty

Using a variable to check if element in square is empty. If it isn't then check if element is in `elems` . If the element is in elems then remove the element from elems.

Step 2: Append all non-zero elements into `elems`.

Within our nested for-loop that iterate through all the elements inside a specified box, we just need all non-zero elements to be appended into `elems`. 
So we will first use the variable `e` which we will denote as the current element indexed at in the box:

```python
def box(grid,r_i,c_i):
	elems = list(range(1,10))
```



The reason being that is that we have the list `elems` which contains the numbers 1-9. Since each box in a Sudoku board can only contain numbers from 1-9 without repeats, we will remove the values in `elems` that exist in the specified box. Thus, returning  `elems` will provide a list of numbers that are still needed within the box to fill in for the empty elements.

Step 3: Write a nested for-loop to iterate through the rows

Now remember, since a box consists of the 3 rows and 3 columns comprises 9 values, we will need a nested for-loop. So now you must be wondering, what is the range for iterating through our for-loops? The possible values passed in for `r_i` and `c_i` are in `range(0,3)` which implies that it can be any number from 0, 1, or 2. This is the case because the box is a 3x3 segment in our 9x9 Sudoku board. There are a total of 9 boxes within the Sudoku board. Thus, the range for our for-loops we be defined as such:

```python
	for r in range(r_i*3,r_i*3+3):
		for c in range(c_i*3,c_i*3+3):
```

Now consider if we want to check the first box (the top left box in a Sudoku board). The values of `r_i` and `c_i` passed into the function would be 0 and 0. If we plug that into our for-loops we would look like this:

````python
	for r in range(0*3,0*3+3):
		for c in range(0*3,0*3+3):
````

We could see that for `r` and `c` we would loop from 0 to 2 which would cover all the elements within the first box: (0,0), (0,1), (0,2), (1,0), (1,1), (1,2), (2,0), (2,1), and (2,2). Remember that `range(0,3)` means we iterate from 0 to 2, not 0 to 3.

Our function looks like this thus far:

```python
# This returns all elements in a given box
def box(grid,r_i,c_i):
	elems = list(range(1,10))
	for r in range(r_i*3,r_i*3+3):
		for c in range(c_i*3,c_i*3+3):
			# implement logic in here
```

Step 4: Check if element `e` is non-zero

Given `e`, the current element in our nested for-loop, we will now check if it is non-zero and exists inside of `elems`. If both cases are true, then we will remove the value, denoted by `e`, from `elems`.

```python
if e != 0 and e in elems:
  elems.remove(e)
```
Step 5: Return `elems`

At last, we just return `elems` after iterating through our entire nested for-loop and `box()` is done!

```python
# This returns all elements in a given box
# 9 boxes will be iterated.
def box(grid,r_i,c_i):
	elems = list(range(1,10))
	for r in range(r_i*3,r_i*3+3):
		for c in range(c_i*3,c_i*3+3):
			e = grid[r][c]
			if e != 0 and e in elems:
				elems.remove(e)
	return elems
```

----------------------------------------------FEEDBACK--------------------------------------------------
# Abstract:
A step-by-step tutorial that explains now to work with a box to make Sudoku board for beginners.

# Changes:
* fixed some grammatical issues
* broke up run-on sentences
* technical term errors (nested for-loop instead of nested-for loop)

# Strength:
* coding examples well explained and there is enough of them to show  how it is done
* easy for beginner to understand because it gets down to the detailed logics of the baseic instead of having readers deduct the reasonings
* easy to follow and discuss with the step-by-step strategy

# Weakness:
* from personal experience I think it would be helpful to put the complete implementation at the top of the tutorial, and then if there is any confusing part then people can search the parts accordingly. I think that gives more of a general sense of what exactly they need to do to implement it
* in step 3, it would be easier to read if the numbers are only used when it is important to not confuse the readers. I left it but I think the first sentence is already explained
* I don't feel like it's really necessary to write out how 0, 0 is plugged in in stage 3, I think it's pretty self-explanatory (or if it's for absolute beginners, maybe show it in a different format because straight up plugging into code is not making a ton of progress in explaining)
