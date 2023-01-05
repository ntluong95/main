<h3><a href="https://github.com/mclix85/datacamp" target="_blank">View Source Code</a></h3>

<h3>Course Description</h3>

<p class="course__description">Python is a general-purpose programming language that is becoming ever more popular for data science. Companies worldwide are using Python to harvest insights from their data and gain a competitive edge. Unlike other Python tutorials, this course focuses on Python specifically for data science. In our Introduction to Python course, you’ll learn about powerful ways to store and manipulate data, and helpful data science tools to begin conducting your own analyses. Start DataCamp’s online Python curriculum now.</p>

# Python Basics

<p class="chapter__description">
    An introduction to the basic concepts of Python. Learn how to use Python interactively and by using a script. Create your first variables and acquaint yourself with Python's basic data types.
  </p>
  
## Hello Python!



### The Python Interface


<div class>
<p>In the Python script on the right, you can type Python code to solve the exercises. If you hit <em>Run Code</em> or <em>Submit Answer</em>, your python script (<code>script.py</code>) is executed and the output is shown in the IPython Shell. <em>Submit Answer</em> checks whether your submission is correct and gives you feedback.</p>
<p>You can hit <em>Run Code</em> and <em>Submit Answer</em> as often as you want. If you're stuck, you can click <em>Get Hint</em>, and ultimately <em>Get Solution</em>.</p>
<p>You can also use the IPython Shell interactively by simply typing commands and hitting Enter. When you work in the shell directly, your code will not be checked for correctness so it is a great way to experiment.</p>
</div>

<li>Experiment in the IPython Shell; type <code>5 / 8</code>, for example.</li>

<li>Add another line of code to the Python script on the top-right (not in the Shell): <code>print(7 + 10)</code>.</li>
<li>Hit <em>Submit Answer</em> to execute the Python script and receive feedback.</li>
<div>

```python
# Example, do not modify!
print(5 / 8)
```

```
## 0.625
```
</div>

<div>

```python
# Put code below here
print(7 + 10)
```

```
## 17
```
</div>

<p class="">Great! On to the next one!</p>

### When to use Python?


<div class><p>Python is a pretty versatile language. For which applications can you use Python?</p></div>

- [ ] You want to do some quick calculations.
- [ ] For your new business, you want to develop a database-driven website.
- [ ] Your boss asks you to clean and analyze the results of the latest satisfaction survey.
- [x] All of the above.

<p class="">Correct! Python is an extremely versatile language.</p>

### Any comments?


<div class>
<p>Something that Hugo didn't mention in his videos is that you can add <strong>comments</strong> to your Python scripts. Comments are important to make sure that you and others can understand what your code is about.</p>
<p>To add comments to your Python script, you can use the <code>#</code> tag. These comments are not run as Python code, so they will not influence your result. As an example, take the comment in the editor, <code># Division</code>; it is completely ignored during execution.</p>
</div>
<div class="exercise--instructions__content">
<p>Above the <code>print(7 + 10)</code>, add the comment </p>
<pre><code># Addition
</code></pre>
</div>

<div>

</div>
<div>

```python
# Division
print(5 / 8)
```

```
## 0.625
```
</div>
<div>

```python
# Addition
print(7 + 10)
```

```
## 17
```
</div>

<p class="">Great!</p>

### Python as a calculator


<div class>
<p>Python is perfectly suited to do basic calculations. Apart from addition, subtraction, multiplication and division, there is also support for more advanced operations such as:</p>
<ul>
<li>Exponentiation: <code>\*\*</code>. This operator raises the number to its left to the power of the number to its right. For example <code>4\*\*2</code> will give <code>16</code>.</li>
<li>Modulo: <code>%</code>. This operator returns the remainder of the division of the number to the left by the number on its right. For example <code>18 % 7</code> equals <code>4</code>.</li>
</ul>
<p>The code in the script gives some examples.</p>
</div>
<div class="exercise--instructions__content"><p>Suppose you have $100, which you can invest with a 10% return each year. After one year, it's \(100 \times 1.1 = 110\) dollars, and after two years it's \(100 \times 1.1 \times 1.1 = 121\). Add code to calculate how much money you end up with after 7 years, and print the result.</p></div>

<div>

</div>

<div>

</div>

<div>

```python
# Addition, subtraction
print(5 + 5)
```

```
## 10
```

```python
print(5 - 5)
```

```
## 0
```
</div>
<div>

```python
# Multiplication, division, modulo, and exponentiation
print(3 * 5)
```

```
## 15
```

```python
print(10 / 2)
```

```
## 5.0
```

```python
print(18 % 7)
```

```
## 4
```

```python
print(4 ** 2)
```

```
## 16
```
</div>
<div>

```python
# How much is your $100 worth after 7 years?
print(100 * 1.1 ** 7)
```

```
## 194.87171000000012
```
</div>
<p class="">Time for another video!</p>

## Variables and Types



### Variable Assignment


<div class>
<p>In Python, a variable allows you to refer to a value with a name. To create a variable use <code>=</code>, like this example:</p>
<pre><code>x = 5
</code></pre>
<p>You can now use the name of this variable, <code>x</code>, instead of the actual value, <code>5</code>.</p>
<p>Remember, <code>=</code> in Python means <em>assignment</em>, it doesn't test equality!</p>
</div>

<li>Create a variable <code>savings</code> with the value 100.</li>

<li>Check out this variable by typing <code>print(savings)</code> in the script.</li>

```python
# Create a variable savings
savings = 100

# Print out savings
print(savings)
```

```
## 100
```

<p class="">Great! Let's try to do some calculations with this variable now!</p>

### Calculations with variables


<div class>
<p>Remember how you calculated the money you ended up with after 7 years of investing $100? You did something like this:</p>
<pre><code>100 * 1.1 ** 7
</code></pre>
<p>Instead of calculating with the actual values, you can use variables instead. The <code>savings</code> variable you've created in the previous exercise represents the $100 you started with. It's up to you to create a new variable to represent <code>1.1</code> and then redo the calculations!</p>
</div>

<li>Create a variable <code>growth_multiplier</code>, equal to <code>1.1</code>.</li>

<li>Create a variable, <code>result</code>, equal to the amount of money you saved after <code>7</code> years. </li>

<li>Print out the value of <code>result</code>.</li>

```python
# Create a variable growth_multiplier
growth_multiplier = 1.1

# Calculate result
result = savings * growth_multiplier ** 7

# Print out result
print(result)
```

```
## 194.87171000000012
```

<p class="">Great!</p>

### Other variable types


<div class>
<p>In the previous exercise, you worked with two Python data types:</p>
<ul>
<li>
<code>int</code>, or integer: a number without a fractional part. <code>savings</code>, with the value <code>100</code>, is an example of an integer.</li>
<li>
<code>float</code>, or floating point: a number that has both an integer and fractional part, separated by a point. <code>growth_multiplier</code>, with the value <code>1.1</code>, is an example of a float.</li>
</ul>
<p>Next to numerical data types, there are two other very common data types:</p>
<ul>
<li>
<code>str</code>, or string: a type to represent text. You can use single or double quotes to build a string.</li>
<li>
<code>bool</code>, or boolean: a type to represent logical values. Can only be <code>True</code> or <code>False</code> (the capitalization is important!).</li>
</ul>
</div>

<li>Create a new string, <code>desc</code>, with the value <code>"compound interest"</code>.</li>

<li>Create a new boolean, <code>profitable</code>, with the value <code>True</code>.</li>

```python
# Create a variable desc
desc = "compound interest"

# Create a variable profitable
profitable = True
```

<p class="">Nice!</p>

### Guess the type


<div class>
<p>To find out the type of a value or a variable that refers to that value, you can use the <a href="https://docs.python.org/3/library/functions.html#type"><code>type()</code></a> function. Suppose you've defined a variable <code>a</code>, but you forgot the type of this variable. To determine the type of <code>a</code>, simply execute:</p>
<pre><code>type(a)
</code></pre>
<p>We already went ahead and created three variables: <code>a</code>, <code>b</code> and <code>c</code>. You can use the IPython shell to discover their type. Which of the following options is correct?</p>
</div>

<div>

</div>

<div>

```python
# edited/added
a=194.87171000000012
b='True'
```
</div>
<div>

```python
type(a)
```

```
## <class 'float'>
```
</div>
<div>

```python
type(b)
```

```
## <class 'str'>
```
</div>


- [ ] <code>a</code> is of type <code>int</code>, <code>b</code> is of type <code>str</code>, <code>c</code> is of type <code>bool</code>
- [ ] <code>a</code> is of type <code>float</code>, <code>b</code> is of type <code>bool</code>, <code>c</code> is of type <code>str</code>
- [x] <code>a</code> is of type <code>float</code>, <code>b</code> is of type <code>str</code>, <code>c</code> is of type <code>bool</code>
- [ ] <code>a</code> is of type <code>int</code>, <code>b</code> is of type <code>bool</code>, <code>c</code> is of type <code>str</code>


<p class="">Correcto perfecto!</p>

### Operations with other types


<div class>
<p>Hugo mentioned that different types behave differently in Python.</p>
<p>When you sum two strings, for example, you'll get different behavior than when you sum two integers or two booleans.</p>
<p>In the script some variables with different types have already been created. It's up to you to use them.</p>
</div>


<li>Calculate the product of <code>savings</code> and <code>growth_multiplier</code>. Store the result in <code>year1</code>.</li>

<li>What do you think the resulting type will be? Find out by printing out the type of <code>year1</code>.</li>

<li>Calculate the sum of <code>desc</code> and <code>desc</code> and store the result in a new variable <code>doubledesc</code>.</li>

<li>Print out <code>doubledesc</code>. Did you expect this?</li>
<div>

```python
# edited/added
savings = 100
growth_multiplier = 1.1
desc = "compound interest"

# Assign product of savings and growth_multiplier to year1
year1 = savings * growth_multiplier

# Print the type of year1
print(type(year1))
```

```
## <class 'float'>
```
</div>
<div>

```python
# Assign sum of desc and desc to doubledesc
doubledesc = desc + desc

# Print out doubledesc
print(doubledesc)
```

```
## compound interestcompound interest
```

<p class="">Nice. Notice how <code>desc + desc</code> causes <code>"compound interest"</code> and <code>"compound interest"</code> to be pasted together.</p>

### Type conversion


<div class>
<p>Using the <code>+</code> operator to paste together two strings can be very useful in building custom messages.</p>
<p>Suppose, for example, that you've calculated the return of your investment and want to summarize the results in a string. Assuming the integer <code>savings</code> and float <code>result</code> are defined, you can try something like this:</p>
<pre><code>print("I started with $" + savings + " and now have $" + result + ". Awesome!")
</code></pre>
<p>This will not work, though, as you cannot simply sum strings and integers/floats.</p>
<p>To fix the error, you'll need to explicitly convert the types of your variables. More specifically, you'll need <a href="https://docs.python.org/3/library/functions.html#func-str"><code>str()</code></a>, to convert a value into a string. <code>str(savings)</code>, for example, will convert the integer <code>savings</code> to a string.</p>
<p>Similar functions such as <a href="https://docs.python.org/3/library/functions.html#int"><code>int()</code></a>, <a href="https://docs.python.org/3/library/functions.html#float"><code>float()</code></a> and <a href="https://docs.python.org/3/library/functions.html#bool"><code>bool()</code></a> will help you convert Python values into any type.</p>
</div>

<li>Hit <em>Run Code</em> to run the code. Try to understand the error message.</li>

<li>Fix the code such that the printout runs without errors; use the function <a href="https://docs.python.org/3/library/functions.html#func-str"><code>str()</code></a> to convert the variables to strings.</li>

<li>Convert the variable <code>pi_string</code> to a float and store this float as a new variable, <code>pi_float</code>.</li>
<div>

```python
# Definition of savings and result
savings = 100
result = 100 * 1.10 ** 7

# Fix the printout
#print("I started with $" + savings + " and now have $" + result + ". Awesome!")

# Definition of savings and result
savings = 100
result = 100 * 1.10 ** 7

# Fix the printout
print("I started with $" + str(savings) + " and now have $" + str(result) + ". Awesome!")
```

```
## I started with $100 and now have $194.87171000000012. Awesome!
```
</div>
<div>

```python
# Definition of pi_string
pi_string = "3.1415926"

# Convert pi_string into float: pi_float
pi_float = float(pi_string)
```

<p class="">Great! You have a profit of around $95; that's pretty awesome indeed!</p>

### Can Python handle everything?


<div class><p>Now that you know something more about combining different sources of information, have a look at the four Python expressions below.
Which one of these will throw an error? You can always copy and paste this code in the IPython Shell to find out!</p></div>

- [ ] <code>"I can add integers, like "  + str(5) + " to strings."</code>
- [ ] <code>"I said " + ("Hey " * 2) + "Hey!"</code>
- [x] <code>"The correct answer to this multiple choice exercise is answer number " + 2</code>
- [ ] <code>True + False</code>

<p class="">Correct! Because you're not converting <code>2</code> to a string with <a href="https://docs.python.org/3/library/functions.html#func-str" target="_blank" rel="noopener noreferrer">str()</a>, this will give an error.</p>

# Python Lists

<p class="chapter__description">
    Learn to store, access, and manipulate data in lists: the first step toward efficiently working with huge amounts of data.
  </p>
  
## Python Lists



### Create a list


<div class>
<p>As opposed to <code>int</code>, <code>bool</code> etc., a list is a <strong>compound data type</strong>; you can group values together:</p>
<pre><code>a = "is"
b = "nice"
my_list = ["my", "list", a, b]
</code></pre>
<p>After measuring the height of your family, you decide to collect some information on the house you're living in. The areas of the different parts of your house are stored in separate variables for now, as shown in the script.</p>
</div>

<li>Create a list, <code>areas</code>, that contains the area of the hallway (<code>hall</code>), kitchen (<code>kit</code>), living room (<code>liv</code>), bedroom (<code>bed</code>) and bathroom (<code>bath</code>), in this order. Use the predefined variables.</li>

<li>Print <code>areas</code> with the <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a> function.</li>

```python
# Area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Create list areas
areas = [hall, kit, liv, bed, bath]

print(areas)
```

```
## [11.25, 18.0, 20.0, 10.75, 9.5]
```

<p class="">Nice! A list is way better here, isn't it?</p>

### Create list with different types


<div class>
<p>A list can contain any Python type. Although it's not really common, a list can also contain a mix of Python types including strings, floats, booleans, etc.</p>
<p>The printout of the previous exercise wasn't really satisfying. It's just a list of numbers representing the areas, but you can't tell which area corresponds to which part of your house.</p>
<p>The code in the editor is the start of a solution. For some of the areas, the name of the corresponding room is already placed in front. Pay attention here! <code>"bathroom"</code> is a string, while <code>bath</code> is a variable that represents the float <code>9.50</code> you specified earlier.</p>
</div>

<li>Finish the code that creates the <code>areas</code> list. Build the list so that the list first contains the name of each room as a string and then its area. In other words, add the strings <code>"hallway"</code>, <code>"kitchen"</code> and <code>"bedroom"</code> at the appropriate locations.</li>

<li>Print <code>areas</code> again; is the printout more informative this time?</li>

```python
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# Adapt list areas
areas = ["hallway", hall, "kitchen", kit, "living room", liv, "bedroom", bed, "bathroom", bath]

# Print areas
print(areas)
```

```
## ['hallway', 11.25, 'kitchen', 18.0, 'living room', 20.0, 'bedroom', 10.75, 'bathroom', 9.5]
```

<p class="">Nice! This list contains both strings and floats, but that's not a problem for Python!</p>

### Select the valid list


<div class>
<p>A list can contain any Python type. But a list itself is also a Python type. That means that a list can also contain a list! Python is getting funkier by the minute, but fear not, just remember the list syntax:</p>
<pre><code>my_list = [el1, el2, el3]
</code></pre>
<p>Can you tell which ones of the following lines of Python code are valid ways to build a list?</p>
<p>A. <code>[1, 3, 4, 2]</code>
B. <code>[[1, 2, 3], [4, 5, 7]]</code>
C. <code>[1 + 2, "a" * 5, 3]</code></p>
</div>

- [x] A, B and C
- [ ] B
- [ ] B and C
- [ ] C

<p class="">Correct! As funny as they may look, all these commands are valid ways to build a Python list.</p>

### List of lists


<div class>
<p>As a data scientist, you'll often be dealing with a lot of data, and it will make sense to group some of this data.</p>
<p>Instead of creating a flat list containing strings and floats, representing the names and areas of the rooms in your house, you can create a list of lists. The script in the editor can already give you an idea.</p>
<p>Don't get confused here: <code>"hallway"</code> is a string, while <code>hall</code> is a variable that represents the float <code>11.25</code> you specified earlier.</p>
</div>

<li>Finish the list of lists so that it also contains the bedroom and bathroom data. Make sure you enter these in order!</li>

<li>Print out <code>house</code>; does this way of structuring your data make more sense?</li>

<li>Print out the type of <code>house</code>. Are you still dealing with a list?</li>
<div>

```python
# area variables (in square meters)
hall = 11.25
kit = 18.0
liv = 20.0
bed = 10.75
bath = 9.50

# house information as list of lists
house = [["hallway", hall],
         ["kitchen", kit],
         ["living room", liv],
         ["bedroom", bed],
         ["bathroom", bath]]
         
# Print out house
print(house)
```

```
## [['hallway', 11.25], ['kitchen', 18.0], ['living room', 20.0], ['bedroom', 10.75], ['bathroom', 9.5]]
```
</div>
<div>

```python
# Print out the type of house
print(type(house))
```

```
## <class 'list'>
```
</div>
<p class="">Great! Get ready to learn about list subsetting!</p>

## Subsetting Lists



### Subset and conquer


<div class>
<p>Subsetting Python lists is a piece of cake. Take the code sample below, which creates a list <code>x</code> and then selects "b" from it. Remember that this is the second element, so it has index 1. You can also use negative indexing.</p>
<pre><code>x = ["a", "b", "c", "d"]
x[1]
x[-3] # same result!
</code></pre>
<p>Remember the <code>areas</code> list from before, containing both strings and floats? Its definition is already in the script. Can you add the correct code to do some Python subsetting?</p>
</div>

<li>Print out the second element from the <code>areas</code> list (it has the value <code>11.25</code>).</li>

<li>Subset and print out the last element of <code>areas</code>, being <code>9.50</code>. Using a negative index makes sense here!</li>

<li>Select the number representing the area of the living room (<code>20.0</code>) and print it out.</li>
<div>

```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Print out second element from areas
print(areas[1])
```

```
## 11.25
```
</div>
<div>

```python
# Print out last element from areas
print(areas[-1])
```

```
## 9.5
```
</div>
<div>

```python
# Print out the area of the living room
print(areas[5])
```

```
## 20.0
```
</div>
<p class="">Good job!</p>

### Subset and calculate


<div class>
<p>After you've extracted values from a list, you can use them to perform additional calculations. Take this example, where the second and fourth element of a list <code>x</code> are extracted. The strings that result are pasted together using the <code>+</code> operator:</p>
<pre><code>x = ["a", "b", "c", "d"]
print(x[1] + x[3])
</code></pre>
</div>

<li>Using a combination of list subsetting and variable assignment, create a new variable, <code>eat_sleep_area</code>, that contains the sum of the area of the kitchen and the area of the bedroom.</li>

<li>Print the new variable <code>eat_sleep_area</code>.</li>

```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Sum of kitchen and bedroom area: eat_sleep_area
eat_sleep_area = areas[3] + areas[-3]

# Print the variable eat_sleep_area
print(eat_sleep_area)
```

```
## 28.75
```

<p class="">Bellissimo!</p>

### Slicing and dicing


<div class>
<p>Selecting single values from a list is just one part of the story. It's also possible to <em>slice</em> your list, which means selecting multiple elements from your list. Use the following syntax:</p>
<pre><code>my_list[start:end]
</code></pre>
<p>The <code>start</code> index will be included, while the <code>end</code> index is <em>not</em>.</p>
<p>The code sample below shows an example. A list with <code>"b"</code> and <code>"c"</code>, corresponding to indexes 1 and 2, are selected from a list <code>x</code>:</p>
<pre><code>x = ["a", "b", "c", "d"]
x[1:3]
</code></pre>
<p>The elements with index 1 and 2 are included, while the element with index 3 is not.</p>
</div>

<li>Use slicing to create a list, <code>downstairs</code>, that contains the first 6 elements of <code>areas</code>.</li>

<li>Do a similar thing to create a new variable, <code>upstairs</code>, that contains the last 4 elements of <code>areas</code>.</li>

<li>Print both <code>downstairs</code> and <code>upstairs</code> using <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a>.</li>

```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Use slicing to create downstairs
downstairs = areas[0:6]

# Use slicing to create upstairs
upstairs = areas[6:10]

# Print out downstairs and upstairs
print(downstairs)
```

```
## ['hallway', 11.25, 'kitchen', 18.0, 'living room', 20.0]
```

```python
print(upstairs)
```

```
## ['bedroom', 10.75, 'bathroom', 9.5]
```

<p class="">Great!</p>

### Slicing and dicing (2)


<div class>
<p>In the video, Hugo first discussed the syntax where you specify both where to begin and end the slice of your list:</p>
<pre><code>my_list[begin:end]
</code></pre>
<p>However, it's also possible not to specify these indexes. If you don't specify the <code>begin</code> index, Python figures out that you want to start your slice at the beginning of your list. If you don't specify the <code>end</code> index, the slice will go all the way to the last element of your list. To experiment with this, try the following commands in the IPython Shell:</p>
<pre><code>x = ["a", "b", "c", "d"]
x[:2]
x[2:]
x[:]
</code></pre>
</div>

<li>Create <code>downstairs</code> again, as the first <code>6</code> elements of <code>areas</code>. This time, simplify the slicing by omitting the <code>begin</code> index.</li>

<li>Create <code>upstairs</code> again, as the last <code>4</code> elements of <code>areas</code>. This time, simplify the slicing by omitting the <code>end</code> index.</li>

```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Alternative slicing to create downstairs
downstairs = areas[:6]

# Alternative slicing to create upstairs
upstairs = areas[6:]
```

<p class="">Wonderful!</p>

### Subsetting lists of lists


<div class>
<p>You saw before that a Python list can contain practically anything; even other lists! To subset lists of lists, you can use the same technique as before: square brackets. Try out the commands in the following code sample in the IPython Shell:</p>
<pre><code>x = [["a", "b", "c"],
     ["d", "e", "f"],
     ["g", "h", "i"]]
x[2][0]
x[2][:2]
</code></pre>
<p><code>x[2]</code> results in a list, that you can subset again by adding additional square brackets.</p>
<p>What will <code>house[-1][1]</code> return? <code>house</code>, the list of lists that you created before, is already defined for you in the workspace. You can experiment with it in the IPython Shell.</p>
</div>


```python
# edited/added
house = [['hallway', 11.25],
 ['kitchen', 18.0],
 ['living room', 20.0],
 ['bedroom', 10.75],
 ['bathroom', 9.5]]
print(house[-1][1])
```

```
## 9.5
```

- [ ] A float: the kitchen area
- [ ] A string: <code>"kitchen"</code>
- [x] A float: the bathroom area
- [ ] A string: <code>"bathroom"</code>


<p class="">Correctomundo! The last piece of the list puzzle is manipulation.</p>

## Manipulating Lists



### Replace list elements


<div class>
<p>Replacing list elements is pretty easy. Simply subset the list and assign new values to the subset. You can select single elements or you can change entire list slices at once.</p>
<p>Use the IPython Shell to experiment with the commands below. Can you tell what's happening and why?</p>
<pre><code>x = ["a", "b", "c", "d"]
x[1] = "r"
x[2:] = ["s", "t"]
</code></pre>
<p>For this and the following exercises, you'll continue working on the <code>areas</code> list that contains the names and areas of different rooms in a house.</p>
</div>

<li>Update the area of the bathroom area to be 10.50 square meters instead of 9.50.</li>

<li>Make the <code>areas</code> list more trendy! Change <code>"living room"</code> to <code>"chill zone"</code>.</li>

```python
# Create the areas list
areas = ["hallway", 11.25, "kitchen", 18.0, "living room", 20.0, "bedroom", 10.75, "bathroom", 9.50]

# Correct the bathroom area
areas[-1] = 10.50

# Change "living room" to "chill zone"
areas[4] = "chill zone"
```

<p class="">Sweet! As the code sample showed, you can also slice a list and replace it with another list to update multiple elements in a single command.</p>

### Extend a list


<div class>
<p>If you can change elements in a list, you sure want to be able to add elements to it, right? You can use the <code>+</code> operator:</p>
<pre><code>x = ["a", "b", "c", "d"]
y = x + ["e", "f"]
</code></pre>
<p>You just won the lottery, awesome! You decide to build a poolhouse and a garage. Can you add the information to the <code>areas</code> list?</p>
</div>

<li>Use the <code>+</code> operator to paste the list <code>["poolhouse", 24.5]</code> to the end of the <code>areas</code> list. Store the resulting list as <code>areas_1</code>.</li>

<li>Further extend <code>areas_1</code> by adding data on your garage. Add the string <code>"garage"</code> and float <code>15.45</code>. Name the resulting list <code>areas_2</code>.</li>

```python
# Create the areas list (updated version)
areas = ["hallway", 11.25, "kitchen", 18.0, "chill zone", 20.0,
         "bedroom", 10.75, "bathroom", 10.50]

# Add poolhouse data to areas, new list is areas_1
areas_1 = areas + ["poolhouse", 24.5]

# Add garage data to areas_1, new list is areas_2
areas_2 = areas_1 + ["garage", 15.45]
```

<p class="">Cool! The list is shaping up nicely!</p>

### Delete list elements


<div class>
<p>Finally, you can also remove elements from your list. You can do this with the <code>del</code> statement:</p>
<pre><code>x = ["a", "b", "c", "d"]
del(x[1])
</code></pre>
<p>Pay attention here: as soon as you remove an element from a list, the indexes of the elements that come after the deleted element all change!</p>
<p>The updated and extended version of <code>areas</code> that you've built in the previous exercises is coded below. You can copy and paste this into the IPython Shell to play around with the result.</p>
<pre><code>areas = ["hallway", 11.25, "kitchen", 18.0,
        "chill zone", 20.0, "bedroom", 10.75,
         "bathroom", 10.50, "poolhouse", 24.5,
         "garage", 15.45]
</code></pre>
<p>There was a mistake! The amount you won with the lottery is not that big after all and it looks like the poolhouse isn't going to happen. You decide to remove the corresponding string and float from the <code>areas</code> list.</p>
<p>The <code>;</code> sign is used to place commands on the same line. The following two code chunks are equivalent:</p>
<pre><code># Same line
command1; command2</code>

<code># Separate lines
command1
command2
</code></pre>
<p>Which of the code chunks will do the job for us?</p>
</div>

- [ ] <code>del(areas[10]); del(areas[11])</code>
- [ ] <code>del(areas[10:11])</code>
- [x] <code>del(areas[-4:-2])</code>
- [ ] <code>del(areas[-3]); del(areas[-4])</code>

<p class="">Correct! You'll learn about easier ways to remove specific elements from Python lists later on.</p>

### Inner workings of lists


<div class>
<p>At the end of the video, Hugo explained how Python lists work behind the scenes. In this exercise you'll get some hands-on experience with this.</p>
<p>The Python code in the script already creates a list with the name <code>areas</code> and a copy named <code>areas_copy</code>. Next, the first element in the <code>areas_copy</code> list is changed and the <code>areas</code> list is printed out. If you hit <em>Run Code</em> you'll see that, although you've changed <code>areas_copy</code>, the change also takes effect in the <code>areas</code> list. That's because <code>areas</code> and <code>areas_copy</code> point to the same list.</p>
<p>If you want to prevent changes in <code>areas_copy</code> from also taking effect in <code>areas</code>, you'll have to do a more explicit copy of the <code>areas</code> list. You can do this with <a href="https://docs.python.org/3/library/functions.html#func-list"><code>list()</code></a> or by using <code>[:]</code>.</p>
</div>
<div class="exercise--instructions__content"><p>Change the second command, that creates the variable <code>areas_copy</code>, such that <code>areas_copy</code> is an explicit copy of <code>areas</code>. After your edit, changes made to <code>areas_copy</code> shouldn't affect <code>areas</code>. Submit the answer to check this.</p></div>

<div>

```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Create areas_copy
areas_copy = areas

# Change areas_copy
areas_copy[0] = 5.0

# Print areas
print(areas)
```

```
## [5.0, 18.0, 20.0, 10.75, 9.5]
```
</div>

<div>

```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Create areas_copy
areas_copy = list(areas)

# Change areas_copy
areas_copy[0] = 5.0

# Print areas
print(areas)
```

```
## [11.25, 18.0, 20.0, 10.75, 9.5]
```

<p class="">Nice! The difference between explicit and reference-based copies is subtle, but can be really important. Try to keep in mind how a list is stored in the computer's memory.</p>

# Functions and Packages

<p class="">You'll learn how to use functions, methods, and packages to efficiently leverage the code that brilliant Python developers have written. The goal is to reduce the amount of code you need to solve challenging problems!</p>

## Functions



### Familiar functions


<div class>
<p>Out of the box, Python offers a bunch of built-in functions to make your life as a data scientist easier. You already know two such functions: <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a> and <a href="https://docs.python.org/3/library/functions.html#type"><code>type()</code></a>. You've also used the functions <a href="https://docs.python.org/3/library/functions.html#func-str"><code>str()</code></a>, <a href="https://docs.python.org/3/library/functions.html#int"><code>int()</code></a>, <a href="https://docs.python.org/3/library/functions.html#bool"><code>bool()</code></a> and <a href="https://docs.python.org/3/library/functions.html#float"><code>float()</code></a> to switch between data types. These are built-in functions as well.</p>
<p>Calling a function is easy. To get the type of <code>3.0</code> and store the output as a new variable, <code>result</code>, you can use the following:</p>
<pre><code>result = type(3.0)
</code></pre>
<p>The general recipe for calling functions and saving the result to a variable is thus:</p>
<pre><code>output = function_name(input)
</code></pre>
</div>

<li>Use <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a> in combination with <a href="https://docs.python.org/3/library/functions.html#type"><code>type()</code></a> to print out the type of <code>var1</code>.</li>

<li>Use <a href="https://docs.python.org/3/library/functions.html#len"><code>len()</code></a> to get the length of the list <code>var1</code>. Wrap it in a <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a> call to directly print it out.</li>

<li>Use <a href="https://docs.python.org/3/library/functions.html#int"><code>int()</code></a> to convert <code>var2</code> to an integer. Store the output as <code>out2</code>.</li>
<div>

```python
# Create variables var1 and var2
var1 = [1, 2, 3, 4]
var2 = True

# Print out type of var1
print(type(var1))
```

```
## <class 'list'>
```
</div>

<div>

```python
# Print out length of var1
print(len(var1))
```

```
## 4
```
</div>
<div>

```python
# Convert var2 to an integer: out2
out2 = int(var2)
```
</div>

<p class="">Great job! The <code>len()</code> function is extremely useful; it also works on strings to count the number of characters!</p>

### Help!


<div class>
<p>Maybe you already know the name of a Python function, but you still have to figure out how to use it. Ironically, you have to ask for information about a function with another function: <a href="https://docs.python.org/3/library/functions.html#help"><code>help()</code></a>. In IPython specifically, you can also use <code>?</code> before the function name.</p>
<p>To get help on the <a href="https://docs.python.org/3/library/functions.html#max"><code>max()</code></a> function, for example, you can use one of these calls:</p>
<pre><code>help(max)
?max
</code></pre>
<p>Use the Shell to open up the documentation on <a href="https://docs.python.org/3/library/functions.html#complex"><code>complex()</code></a>. Which of the following statements is true?</p>
</div>

- [ ] <a href="https://docs.python.org/3/library/functions.html#complex" target="_blank" rel="noopener noreferrer"><code>complex()</code></a> takes exactly two arguments: <code>real</code> and <code>[, imag]</code>.
- [ ] <a href="https://docs.python.org/3/library/functions.html#complex" target="_blank" rel="noopener noreferrer"><code>complex()</code></a> takes two arguments: <code>real</code> and <code>imag</code>. Both these arguments are required.
- [x] <a href="https://docs.python.org/3/library/functions.html#complex" target="_blank" rel="noopener noreferrer"><code>complex()</code></a> takes two arguments: <code>real</code> and <code>imag</code>. <code>real</code> is a required argument, <code>imag</code> is an optional argument.
- [ ] <a href="https://docs.python.org/3/library/functions.html#complex" target="_blank" rel="noopener noreferrer"><code>complex()</code></a> takes two arguments: <code>real</code> and <code>imag</code>. If you don't specify <code>imag</code>, it is set to 1 by Python.

<p class="">Perfect!</p>

### Multiple arguments


<div class>
<p>In the previous exercise, the square brackets around <code>imag</code> in the documentation showed us that the <code>imag</code> argument is optional. But Python also uses a different way to tell users about arguments being optional.</p>
<p>Have a look at the documentation of <a href="https://docs.python.org/3/library/functions.html#sorted"><code>sorted()</code></a> by typing <code>help(sorted)</code> in the IPython Shell.</p>
<p>You'll see that <a href="https://docs.python.org/3/library/functions.html#sorted"><code>sorted()</code></a> takes three arguments: <code>iterable</code>, <code>key</code> and <code>reverse</code>.</p>
<p><code>key=None</code> means that if you don't specify the <code>key</code> argument, it will be <code>None</code>. <code>reverse=False</code> means that if you don't specify the <code>reverse</code> argument, it will be <code>False</code>.</p>
<p>In this exercise, you'll only have to specify <code>iterable</code> and <code>reverse</code>, not <code>key</code>. The first input you pass to <a href="https://docs.python.org/3/library/functions.html#sorted"><code>sorted()</code></a> will be matched to the <code>iterable</code> argument, but what about the second input? To tell Python you want to specify <code>reverse</code> without changing anything about <code>key</code>, you can use <code>=</code>:</p>
<pre><code>sorted(___, reverse = ___)
</code></pre>
<p>Two lists have been created for you in the editor. Can you paste them together and sort them in descending order?</p>
<p>Note: For now, we can understand an <a href="https://docs.python.org/2/glossary.html#term-iterable"><em>iterable</em></a> as being any collection of objects, e.g. a List.</p>
</div>

<li>Use <code>+</code> to merge the contents of <code>first</code> and <code>second</code> into a new list: <code>full</code>.</li>

<li>Call <a href="https://docs.python.org/3/library/functions.html#sorted"><code>sorted()</code></a> on <code>full</code> and specify the <code>reverse</code> argument to be <code>True</code>. Save the sorted list as <code>full_sorted</code>.</li>

<li>Finish off by printing out <code>full_sorted</code>.</li>

```python
# Create lists first and second
first = [11.25, 18.0, 20.0]
second = [10.75, 9.50]

# Paste together first and second: full
full = first + second

# Sort full in descending order: full_sorted
full_sorted = sorted(full, reverse = True)

# Print out full_sorted
print(full_sorted)
```

```
## [20.0, 18.0, 11.25, 10.75, 9.5]
```

<p class="">Cool! Head over to the video on Python methods.</p>

## Methods



### String Methods


<div class>
<p>Strings come with a bunch of methods. Follow the instructions closely to discover some of them. If you want to discover them in more detail, you can always type <code>help(str)</code> in the IPython Shell.</p>
<p>A string <code>place</code> has already been created for you to experiment with.</p>
</div>

<li>Use the <a href="https://docs.python.org/3/library/stdtypes.html#str.upper"><code>upper()</code></a> method on <code>place</code> and store the result in <code>place_up</code>. Use the syntax for calling methods that you learned in the previous video.</li>

<li>Print out <code>place</code> and <code>place_up</code>. Did both change?</li>

<li>Print out the number of o's on the variable <code>place</code> by calling <a href="https://docs.python.org/3/library/stdtypes.html#str.count"><code>count()</code></a> on <code>place</code> and passing the letter <code>'o'</code> as an input to the method. We're talking about the variable <code>place</code>, not the word <code>"place"</code>!</li>
<div>

```python
# string to experiment with: place
place = "poolhouse"

# Use upper() on place: place_up
place_up = place.upper()

# Print out place and place_up
print(place)
```

```
## poolhouse
```

```python
print(place_up)
```

```
## POOLHOUSE
```
</div>
<div>

```python
# Print out the number of o's in place
print(place.count('o'))
```

```
## 3
```
</div>

<p class="">Nice! Notice from the printouts that the <a href="https://docs.python.org/3/library/stdtypes.html#str.upper" target="_blank" rel="noopener noreferrer">upper()</a> method does not change the object it is called on. This will be different for lists in the next exercise!</p>

### List Methods


<div class>
<p>Strings are not the only Python types that have methods associated with them. Lists, floats, integers and booleans are also types that come packaged with a bunch of useful methods. In this exercise, you'll be experimenting with:</p>
<ul>
<li>
<a href="https://docs.python.org/3/library/stdtypes.html#str.index"><code>index()</code></a>, to get the index of the first element of a list that matches its input and</li>
<li>
<a href="https://docs.python.org/3/library/stdtypes.html#str.count"><code>count()</code></a>, to get the number of times an element appears in a list.</li>
</ul>
<p>You'll be working on the list with the area of different parts of a house: <code>areas</code>.</p>
</div>

<li>Use the <a href="https://docs.python.org/3/library/stdtypes.html#str.index"><code>index()</code></a> method to get the index of the element in <code>areas</code> that is equal to <code>20.0</code>. Print out this index.</li>

<li>Call <a href="https://docs.python.org/3/library/stdtypes.html#str.count"><code>count()</code></a> on <code>areas</code> to find out how many times <code>9.50</code> appears in the list. Again, simply print out this number.</li>
<div>

```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Print out the index of the element 20.0
print(areas.index(20.0))
```

```
## 2
```
</div>
<div>

```python
# Print out how often 9.50 appears in areas
print(areas.count(9.50))
```

```
## 1
```
</div>

<p class="">Nice! These were examples of <code>list</code> methods that did not change the list they were called on.</p>

### List Methods (2)


<div class>
<p>Most list methods will change the list they're called on. Examples are:</p>
<ul>
<li>
<a href="https://docs.python.org/3/library/stdtypes.html#typesseq-mutable"><code>append()</code></a>, that adds an element to the list it is called on,</li>
<li>
<a href="https://docs.python.org/3/library/stdtypes.html#typesseq-mutable"><code>remove()</code></a>, that removes the first element of a list that matches the input, and</li>
<li>
<a href="https://docs.python.org/3/library/stdtypes.html#typesseq-mutable"><code>reverse()</code></a>, that reverses the order of the elements in the list it is called on.</li>
</ul>
<p>You'll be working on the list with the area of different parts of the house: <code>areas</code>.</p>
</div>

<li>Use <a href="https://docs.python.org/3/library/stdtypes.html#typesseq-mutable"><code>append()</code></a> twice to add the size of the poolhouse and the garage again: <code>24.5</code> and <code>15.45</code>, respectively. Make sure to add them in this order.</li>

<li>Print out <code>areas</code>
</li>

<li>Use the <a href="https://docs.python.org/3/library/stdtypes.html#typesseq-mutable"><code>reverse()</code></a> method to reverse the order of the elements in <code>areas</code>.</li>

<li>Print out <code>areas</code> once more.</li>
<div>

```python
# Create list areas
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Use append twice to add poolhouse and garage size
areas.append(24.5)
areas.append(15.45)

# Print out areas
print(areas)
```

```
## [11.25, 18.0, 20.0, 10.75, 9.5, 24.5, 15.45]
```
</div>
<div>

```python
# Reverse the orders of the elements in areas
areas.reverse()

# Print out areas
print(areas)
```

```
## [15.45, 24.5, 9.5, 10.75, 20.0, 18.0, 11.25]
```
</div>
<p class="">Great!</p>

## Packages



### Import package


<div class>
<p>As a data scientist, some notions of geometry never hurt. Let's refresh some of the basics.</p>
<p>For a fancy clustering algorithm, you want to find the circumference, \(C\), and area, \(A\), of a circle. When the radius of the circle is <code>r</code>, you can calculate \(C\) and \(A\) as:</p>
<p>$$C = 2 \pi r$$
$$A = \pi r^2 $$</p>
<p>To use the constant <code>pi</code>, you'll need the <code>math</code> package. A variable <code>r</code> is already coded in the script. Fill in the code to calculate <code>C</code> and <code>A</code> and see how the <a href="https://docs.python.org/3/library/functions.html#print"><code>print()</code></a> functions create some nice printouts.</p>
</div>

<li>Import the <code>math</code> package. Now you can access the constant <code>pi</code> with <code>math.pi</code>.</li>

<li>Calculate the circumference of the circle and store it in <code>C</code>.</li>

<li>Calculate the area of the circle and store it in <code>A</code>.</li>
<div>

```python
# Definition of radius
r = 0.43

# Import the math package
import math

# Calculate C
C = 2 * r * math.pi

# Build printout
print("Circumference: " + str(C))
```

```
## Circumference: 2.701769682087222
```
</div>
<div>

```python
# Calculate A
A = math.pi * r ** 2

# Build printout
print("Area: " + str(A))
```

```
## Area: 0.5808804816487527
```
</div>
<p class="">Nice! If you know how to deal with functions from packages, the power of <em>a lot</em> of Python programmers is at your fingertips!</p>

### Selective import


<div class>
<p>General imports, like <code>import math</code>, make <strong>all</strong> functionality from the <code>math</code> package available to you. However, if you decide to only use a specific part of a package, you can always make your import more selective:</p>
<pre><code>from math import pi
</code></pre>
<p>Let's say the Moon's orbit around planet Earth is a perfect circle, with a radius <code>r</code> (in km) that is defined in the script.</p>
</div>

<li>Perform a selective import from the <code>math</code> package where you only import the <code>radians</code> function.</li>

<li>Calculate the distance travelled by the Moon over 12 degrees of its orbit. Assign the result to <code>dist</code>. You can calculate this as <code>r * phi</code>, where <code>r</code> is the radius and <code>phi</code> is the angle in radians. To convert an angle in degrees to an angle in radians, use the <a href="https://docs.python.org/3/library/math.html#math.radians"><code>radians()</code></a> function, which you just imported.</li>

<li>Print out <code>dist</code>.</li>

```python
# Definition of radius
r = 192500

# Import radians function of math package
from math import radians

# Travel distance of Moon over 12 degrees. Store in dist.
dist = r * radians(12)

# Print out dist
print(dist)
```

```
## 40317.10572106901
```

<p class="">Nice! Head over to the next exercise.</p>

### Different ways of importing


<div class>
<p>There are several ways to import packages and modules into Python. Depending on the import call, you'll have to use different Python code.</p>
<p>Suppose you want to use the function <a href="http://docs.scipy.org/doc/numpy-1.10.0/reference/generated/numpy.linalg.inv.html"><code>inv()</code></a>, which is in the <code>linalg</code> subpackage of the <code>scipy</code> package. You want to be able to use this function as follows:</p>
<pre><code>my_inv([[1,2], [3,4]])
</code></pre>
<p>Which <code>import</code> statement will you need in order to run the above code without an error?</p>
</div>

- [ ] <code>import scipy</code>
- [ ] <code>import scipy.linalg</code>
- [ ] <code>from scipy.linalg import my_inv</code>
- [x] <code>from scipy.linalg import inv as my_inv</code>

<p class="">Correct! The <code>as</code> word allows you to create a local name for the function you're importing: <code>inv()</code> is now available as <code>my_inv()</code>.</p>

# NumPy

<p class="">NumPy is a fundamental Python package to efficiently practice data science. Learn to work with powerful tools in the NumPy array, and get started with data exploration.</p>

## Numpy



### Your First NumPy Array


<div class>
<p>In this chapter, we're going to dive into the world of baseball. Along the way, you'll get comfortable with the basics of <code>numpy</code>, a powerful package to do data science.</p>
<p>A list <code>baseball</code> has already been defined in the Python script, representing the height of some baseball players in centimeters. Can you add some code here and there to create a <code>numpy</code> array from it?</p>
</div>

<li>Import the <code>numpy</code> package as <code>np</code>, so that you can refer to <code>numpy</code> with <code>np</code>.</li>

<li>Use <a href="http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array"><code>np.array()</code></a> to create a <code>numpy</code> array from <code>baseball</code>. Name this array <code>np_baseball</code>.</li>

<li>Print out the type of <code>np_baseball</code> to check that you got it right.</li>

```python
# Import the numpy package as np
import numpy as np

# Create list baseball
baseball = [180, 215, 210, 210, 188, 176, 209, 200]

# Create a Numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out type of np_baseball
print(type(np_baseball))
```

```
## <class 'numpy.ndarray'>
```

<p class="">Great job!</p>

### Baseball players' height


<div class>
<p>You are a huge baseball fan. You decide to call the MLB (Major League Baseball) and ask around for some more statistics on the height of the main players. They pass along data on more than a thousand players, which is stored as a regular Python list: <code>height_in</code>. The height is expressed in inches. Can you make a <code>numpy</code> array out of it and convert the units to meters?</p>
<p><code>height_in</code> is already available and the <code>numpy</code> package is loaded, so you can start straight away (Source: <a href="http://wiki.stat.ucla.edu/socr/index.php/SOCR_Data_MLB_HeightsWeights">stat.ucla.edu</a>).</p>
</div>


<li>Create a <code>numpy</code> array from <code>height_in</code>. Name this new array <code>np_height_in</code>.</li>

<li>Print <code>np_height_in</code>.</li>

<li>Multiply <code>np_height_in</code> with <code>0.0254</code> to convert all height measurements from inches to meters. Store the new values in a new array, <code>np_height_m</code>.</li>

<li>Print out <code>np_height_m</code> and check if the output makes sense.</li>
<div>

```python
# edited/added
import pandas as pd
mlb = pd.read_csv("datasets/baseball.csv")

# height_in is available as a regular list
height_in = mlb['Height'].tolist()

# Import numpy
import numpy as np

# Create a numpy array from height_in: np_height_in
np_height_in = np.array(height_in)

# Print out np_height_in
print(np_height_in)
```

```
## [74 74 72 ... 75 75 73]
```
</div>
<div>

```python
# Convert np_height_in to m: np_height_m
np_height_m = np_height_in * 0.0254

# Print np_height_m
print(np_height_m)
```

```
## [1.8796 1.8796 1.8288 ... 1.905  1.905  1.8542]
```

<p class="">Nice! In the blink of an eye, <code>numpy</code> performs multiplications on more than 1000 height measurements.</p>

### Baseball player's BMI


<div class>
<p>The MLB also offers to let you analyze their weight data. Again, both are available as regular Python lists: <code>height_in</code> and <code>weight_lb</code>. <code>height_in</code> is in inches and <code>weight_lb</code> is in pounds.</p>
<p>It's now possible to calculate the BMI of each baseball player. Python code to convert <code>height_in</code> to a <code>numpy</code> array with the correct units is already available in the workspace. Follow the instructions step by step and finish the game!</p>
</div>

<li>Create a <code>numpy</code> array from the <code>weight_lb</code> list with the correct units. Multiply by <code>0.453592</code> to go from pounds to kilograms. Store the resulting <code>numpy</code> array as <code>np_weight_kg</code>.</li>

<li>Use <code>np_height_m</code> and <code>np_weight_kg</code> to calculate the BMI of each player. Use the following equation: $$ \mathrm{BMI} = \frac{\mathrm{weight (kg)}}{\mathrm{height (m)}^2}$$ Save the resulting <code>numpy</code> array as <code>bmi</code>.</li>

<li>Print out <code>bmi</code>.</li>

```python
# height_in and weight_lb are available as regular lists
weight_lb = mlb['Weight'].tolist()

# Import numpy
import numpy as np

# Create array from height_in with metric units: np_height_m
np_height_m = np.array(height_in) * 0.0254

# Create array from weight_lb with metric units: np_weight_kg
np_weight_kg = np.array(weight_lb) * 0.453592

# Calculate the BMI: bmi
bmi = np_weight_kg / np_height_m ** 2

# Print out bmi
print(bmi)
```

```
## [23.11037639 27.60406069 28.48080465 ... 25.62295933 23.74810865
##  25.72686361]
```

<p class="">Cool! Time to step up your game!</p>

### Lightweight baseball players


<div class>
<p>To subset both regular Python lists and <code>numpy</code> arrays, you can use square brackets:</p>
<pre><code>x = [4 , 9 , 6, 3, 1]
x[1]
import numpy as np
y = np.array(x)
y[1]
</code></pre>
<p>For <code>numpy</code> specifically, you can also use boolean <code>numpy</code> arrays:</p>
<pre><code>high = y &gt; 5
y[high]
</code></pre>
<p>The code that calculates the BMI of all baseball players is already included. Follow the instructions and reveal interesting things from the data!</p>
</div>

<li>Create a boolean <code>numpy</code> array: the element of the array should be <code>True</code> if the corresponding baseball player's BMI is below 21. You can use the <code>&lt;</code> operator for this. Name the array <code>light</code>.</li>

<li>Print the array <code>light</code>.</li>

<li>Print out a <code>numpy</code> array with the BMIs of all baseball players whose BMI is below 21. Use <code>light</code> inside square brackets to do a selection on the <code>bmi</code> array.</li>
<div>

```python
# height_in and weight_lb are available as a regular lists

# Import numpy
import numpy as np

# Calculate the BMI: bmi
np_height_m = np.array(height_in) * 0.0254
np_weight_kg = np.array(weight_lb) * 0.453592
bmi = np_weight_kg / np_height_m ** 2

# Create the light array
light = bmi < 21

# Print out light
print(light)
```

```
## [False False False ... False False False]
```
</div>
<div>

```python
# Print out BMIs of all baseball players whose BMI is below 21
print(bmi[light])
```

```
## [20.54255679 20.54255679 20.69282047 20.69282047 20.34343189 20.34343189
##  20.69282047 20.15883472 19.4984471  20.69282047 20.9205219 ]
```
</div>
<p class="">Wow! It appears that only 11 of the more than 1000 baseball players have a BMI under 21!</p>

### NumPy Side Effects


<div class>
<p>As Hugo explained before, <code>numpy</code> is great for doing vector arithmetic. If you compare its functionality with regular Python lists, however, some things have changed.</p>
<p>First of all, <code>numpy</code> arrays cannot contain elements with different types. If you try to build such a list, some of the elements' types are changed to end up with a homogeneous list. This is known as <em>type coercion</em>.</p>
<p>Second, the typical arithmetic operators, such as <code>+</code>, <code>-</code>, <code>*</code> and <code>/</code> have a different meaning for regular Python lists and <code>numpy</code> arrays.</p>
<p>Have a look at this line of code:</p>
<pre><code>np.array([True, 1, 2]) + np.array([3, 4, False])
</code></pre>
<p>Can you tell which code chunk builds the exact same Python object? The <code>numpy</code> package is already imported as <code>np</code>, so you can start experimenting in the IPython Shell straight away!</p>
</div>

- [ ] <code>np.array([True, 1, 2, 3, 4, False])</code>
- [x] <code>np.array([4, 3, 0]) + np.array([0, 2, 2])</code>
- [ ] <code>np.array([1, 1, 2]) + np.array([3, 4, -1])</code>
- [ ] <code>np.array([0, 1, 2, 3, 4, 5])</code>


<p class="">Great job! <code>True</code> is converted to 1, <code>False</code> is converted to 0.</p>

### Subsetting NumPy Arrays


<div class>
<p>You've seen it with your own eyes: Python lists and <code>numpy</code> arrays sometimes behave differently. Luckily, there are still certainties in this world. For example, subsetting (using the square bracket notation on lists or arrays) works exactly the same. To see this for yourself, try the following lines of code in the IPython Shell:</p>
<pre><code>x = ["a", "b", "c"]
x[1]

np_x = np.array(x)
np_x[1]
</code></pre>
<p>The script in the editor already contains code that imports <code>numpy</code> as <code>np</code>, and stores both the height and weight of the MLB players as <code>numpy</code> arrays.</p>
</div>

<li>Subset <code>np_weight_lb</code> by printing out the element at index 50.</li>

<li>Print out a sub-array of <code>np_height_in</code> that contains the elements at index 100 up to <strong>and including</strong> index 110.</li>
<div>

```python
# height_in and weight_lb are available as a regular lists

# Import numpy
import numpy as np

# Store weight and height lists as numpy arrays
np_weight_lb = np.array(weight_lb)
np_height_in = np.array(height_in)

# Print out the weight at index 50
print(np_weight_lb[50])
```

```
## 200
```
</div>
<div>

```python
# Print out sub-array of np_height_in: index 100 up to and including index 110
print(np_height_in[100:111])
```

```
## [73 74 72 73 69 72 73 75 75 73 72]
```
</div>
<p class="">Nice! Time to learn something new: 2D Numpy arrays!</p>

## 2D Numpy Arrays



### Your First 2D NumPy Array


<div class>
<p>Before working on the actual MLB data, let's try to create a 2D <code>numpy</code> array from a small list of lists.</p>
<p>In this exercise, <code>baseball</code> is a list of lists. The main list contains 4 elements. Each of these elements is a list containing the height and the weight of 4 baseball players, in this order. <code>baseball</code> is already coded for you in the script.</p>
</div>

<li>Use <a href="http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array"><code>np.array()</code></a> to create a 2D <code>numpy</code> array from <code>baseball</code>. Name it <code>np_baseball</code>.</li>

<li>Print out the type of <code>np_baseball</code>.</li>

<li>Print out the <code>shape</code> attribute of <code>np_baseball</code>. Use <code>np_baseball.shape</code>.</li>
<div>

```python
# Create baseball, a list of lists
baseball = [[180, 78.4],
            [215, 102.7],
            [210, 98.5],
            [188, 75.2]]

# Import numpy
import numpy as np

# Create a 2D numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out the type of np_baseball
print(type(np_baseball))
```

```
## <class 'numpy.ndarray'>
```
</div>
<div>

```python
# Print out the shape of np_baseball
print(np_baseball.shape)
```

```
## (4, 2)
```

<p class="">Great! You're ready to convert the actual MLB data to a 2D <code>numpy</code> array now!</p>

### Baseball data in 2D form


<div class>
<p>You have another look at the MLB data and realize that it makes more sense to restructure all this information in a 2D <code>numpy</code> array. This array should have 1015 rows, corresponding to the 1015 baseball players you have information on, and 2 columns (for height and weight).</p>
<p>The MLB was, again, very helpful and passed you the data in a different structure, a Python list of lists. In this list of lists, each sublist represents the height and weight of a single baseball player. The name of this embedded list is <code>baseball</code>.</p>
<p>Can you store the data as a 2D array to unlock <code>numpy</code>'s extra functionality?</p>
</div>

<li>Use <a href="http://docs.scipy.org/doc/numpy-1.10.0/glossary.html#term-array"><code>np.array()</code></a> to create a 2D <code>numpy</code> array from <code>baseball</code>. Name it <code>np_baseball</code>.</li>

<li>Print out the <code>shape</code> attribute of <code>np_baseball</code>.</li>

```python
# baseball is available as a regular list of lists

# Import numpy package
import numpy as np

# Create a 2D numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out the shape of np_baseball
print(np_baseball.shape)
```

```
## (4, 2)
```

<p class="">Slick! Time to show off some killer features of multi-dimensional <code>numpy</code> arrays!</p>

### Subsetting 2D NumPy Arrays


<div class>
<p>If your 2D <code>numpy</code> array has a regular structure, i.e. each row and column has a fixed number of values, complicated ways of subsetting become very easy. Have a look at the code below where the elements <code>"a"</code> and <code>"c"</code> are extracted from a list of lists.</p>
<pre><code># regular list of lists
x = [["a", "b"], ["c", "d"]]
[x[0][0], x[1][0]]</code>

<code># numpy
import numpy as np
np_x = np.array(x)
np_x[:,0]
</code></pre>
<p>For regular Python lists, this is a real pain. For 2D <code>numpy</code> arrays, however, it's pretty intuitive! The indexes before the comma refer to the rows, while those after the comma refer to the columns. The <code>:</code> is for slicing; in this example, it tells Python to include all rows.</p>
<p>The code that converts the pre-loaded <code>baseball</code> list to a 2D <code>numpy</code> array is already in the script. The first column contains the players' height in inches and the second column holds player weight, in pounds. Add some lines to make the correct selections. Remember that in Python, the first element is at index 0!</p>
</div>


<li>Print out the 50th row of <code>np_baseball</code>.</li>

<li>Make a new variable, <code>np_weight_lb</code>, containing the entire second column of <code>np_baseball</code>.</li>

<li>Select the height (first column) of the 124th baseball player in <code>np_baseball</code> and print it out.</li>
<div>

```python
# edited/added
baseball = pd.read_csv("datasets/baseball.csv")[['Height', 'Weight']]

# baseball is available as a regular list of lists

# Import numpy package
import numpy as np

# Create np_baseball (2 cols)
np_baseball = np.array(baseball)

# Print out the 50th row of np_baseball
print(np_baseball[49,:])
```

```
## [ 70 195]
```
</div>
<div>

```python
# Select the entire second column of np_baseball: np_weight_lb
np_weight_lb = np_baseball[:,1]

# Print out height of 124th player
print(np_baseball[123, 0])
```

```
## 75
```

<p class="">This is going well!</p>

### 2D Arithmetic


<div class>
<p>Remember how you calculated the Body Mass Index for all baseball players? <code>numpy</code> was able to perform all calculations element-wise (i.e. element by element). For 2D <code>numpy</code> arrays this isn't any different! You can combine matrices with single numbers, with vectors, and with other matrices.</p>
<p>Execute the code below in the IPython shell and see if you understand:</p>
<pre><code>import numpy as np
np_mat = np.array([[1, 2],
                   [3, 4],
                   [5, 6]])
np_mat * 2
np_mat + np.array([10, 10])
np_mat + np_mat
</code></pre>
<p><code>np_baseball</code> is coded for you; it's again a 2D <code>numpy</code> array with 3 columns representing height (in inches), weight (in pounds) and age (in years).</p>
</div>


<li>You managed to get hold of the changes in height, weight and age of all baseball players. It is available as a 2D <code>numpy</code> array, <code>updated</code>. Add <code>np_baseball</code> and <code>updated</code> and print out the result.</li>

<li>You want to convert the units of height and weight to metric (meters and kilograms respectively). As a first step, create a <code>numpy</code> array with three values: <code>0.0254</code>, <code>0.453592</code> and <code>1</code>. Name this array <code>conversion</code>.</li>

<li>Multiply <code>np_baseball</code> with <code>conversion</code> and print out the result.</li>
<div>

```python
# edited/added
baseball = pd.read_csv("datasets/baseball.csv")[['Height', 'Weight', 'Age']]
n = len(baseball)
updated = np.array(pd.read_csv("datasets/update.csv", header = None))

# baseball is available as a regular list of lists
# updated is available as 2D numpy array

# Import numpy package
import numpy as np

# Create np_baseball (3 cols)
np_baseball = np.array(baseball)

# Print out addition of np_baseball and updated
print(np_baseball + updated)
```

```
## [[ 75.2303559  168.83775102  23.99      ]
##  [ 75.02614252 231.09732309  35.69      ]
##  [ 73.1544228  215.08167641  31.78      ]
##  ...
##  [ 76.09349925 209.23890778  26.19      ]
##  [ 75.82285669 172.21799965  32.01      ]
##  [ 73.99484223 203.14402711  28.92      ]]
```
</div>
<div>

```python
# Create numpy array: conversion
conversion = np.array([0.0254, 0.453592, 1])

# Print out product of np_baseball and conversion
print(np_baseball * conversion)
```

```
## [[ 1.8796  81.64656 22.99   ]
##  [ 1.8796  97.52228 34.69   ]
##  [ 1.8288  95.25432 30.78   ]
##  ...
##  [ 1.905   92.98636 25.19   ]
##  [ 1.905   86.18248 31.01   ]
##  [ 1.8542  88.45044 27.92   ]]
```

<p class="">Great job! Notice how with very little code, you can change all values in your <code>numpy</code> data structure in a very specific way. This will be very useful in your future as a data scientist!</p>

## Numpy: Basic Statistics



### Average versus median


<div class>
<p>You now know how to use <code>numpy</code> functions to get a better feeling for your data. It basically comes down to importing <code>numpy</code> and then calling several simple functions on the <code>numpy</code> arrays:</p>
<pre><code>import numpy as np
x = [1, 4, 8, 10, 12]
np.mean(x)
np.median(x)
</code></pre>
<p>The baseball data is available as a 2D <code>numpy</code> array with 3 columns (height, weight, age) and 1015 rows. The name of this <code>numpy</code> array is <code>np_baseball</code>. After restructuring the data, however, you notice that some height values are abnormally high. Follow the instructions and discover which summary statistic is best suited if you're dealing with so-called <em>outliers</em>.</p>
</div>

<li>Create <code>numpy</code> array <code>np_height_in</code> that is equal to first column of <code>np_baseball</code>.</li>

<li>Print out the mean of <code>np_height_in</code>.</li>

<li>Print out the median of <code>np_height_in</code>.</li>

```python
# np_baseball is available

# Import numpy
import numpy as np

# Create np_height_in from np_baseball
np_height_in = np_baseball[:,0]

# Print out the mean of np_height_in
print(np.mean(np_height_in))
```

```
## 73.6896551724138
```
</div>
<div>

```python
# Print out the median of np_height_in
print(np.median(np_height_in))
```

```
## 74.0
```
</div>

<p class="">An average height of 1586 inches, that doesn't sound right, does it? However, the median does not seem affected by the outliers: 74 inches makes perfect sense. It's always a good idea to check both the median and the mean, to get an idea about the overall distribution of the entire dataset.</p>

### Explore the baseball data


<div class>
<p>Because the mean and median are so far apart, you decide to complain to the MLB. They find the error and send the corrected data over to you. It's again available as a 2D Numpy array <code>np_baseball</code>, with three columns.</p>
<p>The Python script in the editor already includes code to print out informative messages with the different summary statistics. Can you finish the job?</p>
</div>

<li>The code to print out the mean height is already included. Complete the code for the median height. Replace <code>None</code> with the correct code.</li>

<div>

</div>

<div>

</div>

<li>Use <a href="http://docs.scipy.org/doc/numpy-1.10.0/reference/generated/numpy.std.html"><code>np.std()</code></a> on the first column of <code>np_baseball</code> to calculate <code>stddev</code>. Replace <code>None</code> with the correct code.</li>

<li>Do big players tend to be heavier? Use <a href="http://docs.scipy.org/doc/numpy-1.10.0/reference/generated/numpy.corrcoef.html"><code>np.corrcoef()</code></a> to store the correlation between the first and second column of <code>np_baseball</code> in <code>corr</code>. Replace <code>None</code> with the correct code.</li>
<div>

```python
# np_baseball is available

# Import numpy
import numpy as np

# Print mean height (first column)
avg = np.mean(np_baseball[:,0])
print("Average: " + str(avg))
```

```
## Average: 73.6896551724138
```
</div>
<div>

```python
# Print median height. Replace 'None'
med = np.median(np_baseball[:,0])
print("Median: " + str(med))
```

```
## Median: 74.0
```
</div>
<div>

```python
# Print out the standard deviation on height. Replace 'None'
stddev = np.std(np_baseball[:,0])
print("Standard Deviation: " + str(stddev))
```

```
## Standard Deviation: 2.312791881046546
```
</div>
<div>

```python
# Print out correlation between first and second column. Replace 'None'
corr = np.corrcoef(np_baseball[:,0], np_baseball[:,1])
print("Correlation: " + str(corr))
```

```
## Correlation: [[1.         0.53153932]
##  [0.53153932 1.        ]]
```
</div>
<p class="">Great! Time to use all of your new data science skills in the last exercise!</p>

### Blend it all together


<div class>
<p>In the last few exercises you've learned everything there is to know about heights and weights of baseball players. Now it's time to dive into another sport: soccer.</p>
<p>You've contacted FIFA for some data and they handed you two lists. The lists are the following:</p>
<pre><code>positions = ['GK', 'M', 'A', 'D', ...]
heights = [191, 184, 185, 180, ...]
</code></pre>
<p>Each element in the lists corresponds to a player. The first list, <code>positions</code>, contains strings representing each player's position. The possible positions are: <code>'GK'</code> (goalkeeper), <code>'M'</code> (midfield), <code>'A'</code> (attack) and <code>'D'</code> (defense). The second list, <code>heights</code>, contains integers representing the height of the player in cm. The first player in the lists is a goalkeeper and is pretty tall (191 cm).</p>
<p>You're fairly confident that the median height of goalkeepers is higher than that of other players on the soccer field. Some of your friends don't believe you, so you are determined to show them using the data you received from FIFA and your newly acquired Python skills.</p>
</div>


<li>Convert <code>heights</code> and <code>positions</code>, which are regular lists, to numpy arrays. Call them <code>np_heights</code> and <code>np_positions</code>.</li>

<li>Extract all the heights of the goalkeepers. You can use a little trick here: use <code>np_positions == 'GK'</code> as an index for <code>np_heights</code>. Assign the result to <code>gk_heights</code>.</li>

<li>Extract all the heights of all the other players. This time use <code>np_positions != 'GK'</code> as an index for <code>np_heights</code>. Assign the result to <code>other_heights</code>.</li>

<li>Print out the median height of the goalkeepers using <a href="http://docs.scipy.org/doc/numpy-1.10.0/reference/generated/numpy.median.html"><code>np.median()</code></a>. Replace <code>None</code> with the correct code.</li>

<li>Do the same for the other players. Print out their median height. Replace <code>None</code> with the correct code.</li>
<div>

```python
# edited/added
fifa =  pd.read_csv("datasets/fifa.csv", skipinitialspace=True, usecols=['position', 'height'])
positions = list(fifa.position)
heights = list(fifa.height)

# heights and positions are available as lists

# Import numpy
import numpy as np

# Convert positions and heights to numpy arrays: np_positions, np_heights
np_positions = np.array(positions)
np_heights = np.array(heights)

# Heights of the goalkeepers: gk_heights
gk_heights = np_heights[np_positions == 'GK']

# Heights of the other players: other_heights
other_heights = np_heights[np_positions != 'GK']

# Print out the median height of goalkeepers. Replace 'None'
print("Median height of goalkeepers: " + str(np.median(gk_heights)))
```

```
## Median height of goalkeepers: 188.0
```
</div>
<div>

```python
# Print out the median height of other players. Replace 'None'
print("Median height of other players: " + str(np.median(other_heights)))
```

```
## Median height of other players: 181.0
```

<p class="">Wonderful! You were right and the disbelievers were wrong! This exercise marks the end of the Intro to Python for Data Science course. See you in another course!</p>
