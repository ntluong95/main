---
title: "Writing Efficient Python Code"
subtitle: "Logan Thomas"
date: "10 January 2023"
author:
  - name: "Dat Tran"
output:
  rmdformats::robobook:
    keep_md: true
    thumbnails: true
    lightbox: true
    gallery: true
    use_bookdown: true
---

<style>
p {
  text-align: justify;
}

div {
  text-align: justify;
}
</style>

<h3><a href="https://github.com/mclix85/datacamp" target="_blank">View Source Code</a></h3>

<h3>Course Description</h3>

Logan is a member of the Technical Training team at Enthought – an organization that provides digital transformation, software consulting, and training services to individuals and companies worldwide. As a Scientific Software Technical Trainer, he focuses on helping students write robust, scalable, and efficient Python code. As a self-proclaimed Python enthusiast, Logan enjoys attending meetups and conferences in the Austin, Texas area to share his knowledge with others.

<h3>Course Description</h3>

As a Data Scientist, the majority of your time should be spent gleaning actionable insights from data -- not waiting for your code to finish running. Writing efficient Python code can help reduce runtime and save computational resources, ultimately freeing you up to do the things you love as a Data Scientist. In this course, you'll learn how to use Python's built-in data structures, functions, and modules to write cleaner, faster, and more efficient code. We'll explore how to time and profile code in order to find bottlenecks. Then, you'll practice eliminating these bottlenecks, and other bad design patterns, using Python's Standard Library, NumPy, and pandas. After completing this course, you'll have the necessary tools to start writing efficient Python code!

# Foundations for efficiencies

<p class="chapter__description">
    In this chapter, you'll learn what it means to write efficient Python code. You'll explore Python's Standard Library, learn about NumPy arrays, and practice using some of Python's built-in tools.  This chapter builds a foundation for the concepts covered ahead.
  </p>

## Welcome!



### Pop quiz: what is efficient

<div class=""><p>In the context of this course, what is meant by <em>efficient Python code</em>?</p></div>

- [x] Code that executes quickly for the task at hand, minimizes the memory footprint and follows Python's coding style principles.
- [ ] Code that has a fast runtime, consumes a small amount of memory and can be verbose/hard to interpret (readability doesn't matter).
- [ ] Code that returns a correct result regardless of the execution time and resource consumption.

<p class="dc-completion-pane__message dc-u-maxw-100pc">Correct! Writing efficient Python code minimizes runtime and memory usage while also following the idioms in the <em>Zen of Python</em>.</p>

### A taste of things to come


<div class>
<p>In this exercise, you'll explore both the <em>Non-Pythonic</em> and <em>Pythonic</em> ways of looping over a list. </p>
<pre><code>names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']
</code></pre>
<p>Suppose you wanted to collect the names in the above list that have six letters or more. In other programming languages, the typical approach is to create an index variable (<code>i</code>), use <code>i</code> to iterate over the list, and use an if statement to collect the names with six letters or more:</p>
<pre><code>i = 0
new_list= []
while i &lt; len(names):
    if len(names[i]) &gt;= 6:
        new_list.append(names[i])
    i += 1
</code></pre>
<p>Let's explore some more <em>Pythonic</em> ways of doing this.</p>
</div>
<div class="exercise--instructions__content"><p>Print the list, <code>new_list</code>, that was created using a <em>Non-Pythonic</em> approach.</p></div>

```python
# edited/added
names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']

# Print the list created using the Non-Pythonic approach
i = 0
new_list= []
while i < len(names):
    if len(names[i]) >= 6:
        new_list.append(names[i])
    i += 1
print(new_list)
```

```
## ['Kramer', 'Elaine', 'George', 'Newman']
```

<div class="exercise--instructions__content"><p>A more <em>Pythonic</em> approach would loop over the contents of <code>names</code>, rather than using an index variable. Print <code>better_list</code>.</p></div>

```python
# Print the list created by looping over the contents of names
better_list = []
for name in names:
    if len(name) >= 6:
        better_list.append(name)
print(better_list)
```

```
## ['Kramer', 'Elaine', 'George', 'Newman']
```

<div class="exercise--instructions__content"><p>The best <em>Pythonic</em> way of doing this is by using list comprehension. Print <code>best_list</code>.</p></div>

```python
# Print the list created by using list comprehension
best_list = [name for name in names if len(name) >= 6]
print(best_list)
```

```
## ['Kramer', 'Elaine', 'George', 'Newman']
```

<p class="">Great work! Don't get too caught up in the coding concepts just yet (you'll practice using lists, for loops, and list comprehensions later on). The important thing to notice here is that following some of Python's guiding principles allows you to write cleaner and more efficient code. <br> <br> Remember, <code>Pythonic code == efficient code</code>. You'll explore these, and other, Pythonic concepts later on in the course, but for now, this is just a taste of things to come!</p>

### Zen of Python


<div class>
<p>In the video, we covered the <em>Zen of Python</em> written by Tim Peters, which lists 19 idioms that serve as guiding principles for any Pythonista. Python has hundreds of <em>Python Enhancement Proposals</em>, commonly referred to as <em>PEPs</em>. The <em>Zen of Python</em> is one of these <em>PEPs</em> and is documented as <a href="https://www.python.org/dev/peps/pep-0020/">PEP20</a>.</p>
<p>One little Easter Egg in Python is the ability to print the <em>Zen of Python</em> using the command <code>import this</code>.  Let's take a look at one of the idioms listed in these guiding principles.</p>
<p>Type and run the command <code>import this</code> within your IPython console and answer the following question:</p>
<hr>
<p>What is the 7th idiom of the Zen of Python?</p>
</div>

- [ ] Flat is better than nested.
- [ ] Beautiful is better than ugly.
- [x] Readability counts.
- [ ] Python is the best programming language ever.

<p class="">That's correct! Python has a design philosophy that emphasizes readability. Throughout the course, you'll see that writing efficient Python code goes hand in hand with writing code that is easy to understand. Faster code is good, but faster &amp; readable code is best!</p>

## Building with built-ins



### Built-in practice: range()


<div class>
<p>In this exercise, you will practice using Python's built-in function <code>range()</code>. Remember that you can use <code>range()</code> in a few different ways:</p>
<p><strong>1)</strong> Create a sequence of numbers from 0 to a stop value (which is <em>exclusive</em>). This is useful when you want to create a simple sequence of numbers starting at zero:</p>
<pre><code>range(stop)</code>

<code># Example
list(range(11))

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
</code></pre>
<p><strong>2)</strong> Create a sequence of numbers from a start value to a stop value (which is <em>exclusive</em>) with a step size. This is useful when you want to create a sequence of numbers that increments by some value other than one. For example, a list of even numbers:</p>
<pre><code>range(start, stop, step)</code>

<code># Example
list(range(2,11,2))

[2, 4, 6, 8, 10]
</code></pre>
</div>

```python
# edited/added
```
<li>Create a <em>range object</em> that starts at zero and ends at five. Only use a <code>stop</code> argument.</li>
<li>Convert the <code>nums</code> variable into a list called <code>nums_list</code>.</li>
<li>Create a new list called <code>nums_list2</code> that starts at <strong>one</strong>, ends at <strong>eleven</strong>, and increments by <strong>two</strong> by unpacking a <em>range object</em> using the star character (<code>*</code>).</li>

```python
# Create a range object that goes from 0 to 5
nums = range(6)
print(type(nums))

# Convert nums to a list
```

```
## <class 'range'>
```

```python
nums_list = list(nums)
print(nums_list)

# Create a new list of odd numbers from 1 to 11 by unpacking a range object
```

```
## [0, 1, 2, 3, 4, 5]
```

```python
nums_list2 = [*range(1,12,2)]
print(nums_list2)
```

```
## [1, 3, 5, 7, 9, 11]
```

<p class="">Nicely done! Notice that using Python's <code>range()</code> function allows you to create a <em>range object</em> of numbers without explicitly typing them out. You can convert the <em>range object</em> into a list by using the <code>list()</code> function or by unpacking it into a list using the star character (<code>*</code>). Cool!</p>

### Built-in practice: enumerate()


<div class>
<p>In this exercise, you'll practice using Python's built-in function <code>enumerate()</code>. This function is useful for obtaining an indexed list. For example, suppose you had a list of people that arrived at a party you are hosting. The list is ordered by arrival (Jerry was the first to arrive, followed by Kramer, etc.):</p>
<pre><code>names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']
</code></pre>
<p>If you wanted to attach an index representing a person's arrival order, you <em>could</em> use the following for loop:</p>
<pre><code>indexed_names = []
for i in range(len(names)):
    index_name = (i, names[i])
    indexed_names.append(index_name)

[(0,'Jerry'),(1,'Kramer'),(2,'Elaine'),(3,'George'),(4,'Newman')]
</code></pre>
<p>But, that's not the most efficient solution. Let's explore how to use <code>enumerate()</code> to make this more efficient.</p>
</div>

```python
# edited/added
```
<li>Instead of using <code>for i in range(len(names))</code>, update the for loop to use <code>i</code> as the index variable and <code>name</code> as the iterator variable and use <code>enumerate()</code>.</li>
<li>Rewrite the previous for loop using <code>enumerate()</code> and list comprehension to create a new list, <code>indexed_names_comp</code>.</li>
<li>Create another list (<code>indexed_names_unpack</code>) by using the star character (<code>*</code>) to unpack the <em>enumerate object</em> created from using <code>enumerate()</code> on <code>names</code>. This time, <strong>start the index for</strong> <code>enumerate()</code> <strong>at one instead of zero.</strong>
</li>

```python
# Rewrite the for loop to use enumerate
indexed_names = []
for i,name in enumerate(names):
    index_name = (i,name)
    indexed_names.append(index_name) 
print(indexed_names)

# Rewrite the above for loop using list comprehension
```

```
## [(0, 'Jerry'), (1, 'Kramer'), (2, 'Elaine'), (3, 'George'), (4, 'Newman')]
```

```python
indexed_names_comp = [(i,name) for i,name in enumerate(names)]
print(indexed_names_comp)

# Unpack an enumerate object with a starting index of one
```

```
## [(0, 'Jerry'), (1, 'Kramer'), (2, 'Elaine'), (3, 'George'), (4, 'Newman')]
```

```python
indexed_names_unpack = [*enumerate(names, 1)]
print(indexed_names_unpack)
```

```
## [(1, 'Jerry'), (2, 'Kramer'), (3, 'Elaine'), (4, 'George'), (5, 'Newman')]
```

<p class="">Awesome! Using Python's built-in <code>enumerate()</code> function allows you to create an index for each item in the object you give it. You can use list comprehension, or even unpack the <em>enumerate object</em> directly into a list, to write a nice simple one-liner.</p>

### Built-in practice: map()


<div class>
<p>In this exercise, you'll practice using Python's built-in <code>map()</code> function to apply a function to every element of an object. Let's look at a list of party guests:</p>
<pre><code>names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']
</code></pre>
<p>Suppose you wanted to create a new list (called <code>names_uppercase</code>) that converted all the letters in each name to uppercase. you could accomplish this with the below for loop:</p>
<pre><code>names_uppercase = []

for name in names:
  names_uppercase.append(name.upper())

['JERRY', 'KRAMER', 'ELAINE', 'GEORGE', 'NEWMAN']
</code></pre>
<p>Let's explore using the <code>map()</code> function to do this more efficiently in one line of code.</p>
</div>

```python
# edited/added
```
<li>Use <code>map()</code> and the method <code>str.upper()</code> to convert each name in the list <code>names</code> to uppercase. Save this to the variable <code>names_map</code>.</li>
<li>Print the data type of <code>names_map</code>.</li>
<li>Unpack the contents of <code>names_map</code> into a list called <code>names_uppercase</code> using the star character (<code>*</code>).</li>
<li>Print <code>names_uppercase</code> and observe its contents.</li>

```python
# Use map to apply str.upper to each element in names
names_map  = map(str.upper, names)

# Print the type of the names_map
print(type(names_map))

# Unpack names_map into a list
```

```
## <class 'map'>
```

```python
names_uppercase = [*names_map]

# Print the list created above
print(names_uppercase)
```

```
## ['JERRY', 'KRAMER', 'ELAINE', 'GEORGE', 'NEWMAN']
```

<p class="">Well done! You used Python's built-in <code>map()</code> function to apply the <code>str.upper()</code> method to each element in the <code>names</code> object. Later on in the course, you'll explore how using <code>map()</code> can provide some efficiency improvements to your code.</p>

## The power of NumPy arrays



### Practice with NumPy arrays


<div class>
<p>Let's practice slicing <code>numpy</code> arrays and using NumPy's broadcasting concept. Remember, broadcasting refers to a <code>numpy</code> array's ability to vectorize operations, so they are performed on all elements of an object at once.</p>
<p>A two-dimensional <code>numpy</code> array has been loaded into your session (called <code>nums</code>) and printed into the console for your convenience. <code>numpy</code> has been imported into your session as <code>np</code>.</p>
</div>

```python
# edited/added
import numpy as np
nums = np.array([[ 1,  2,  3,  4,  5], [ 6,  7,  8,  9, 10]])
```
<li>Print the second row of <code>nums</code>.</li>
<li>Print the items of <code>nums</code> that are greater than six.</li>
<li>Create <code>nums_dbl</code> that doubles each number in <code>nums</code>.</li>
<li>Replace the third column in <code>nums</code> with a new column that adds <code>1</code> to each item in the original column.</li>

```python
# Print second row of nums
print(nums[1,:])

# Print all elements of nums that are greater than six
```

```
## [ 6  7  8  9 10]
```

```python
print(nums[nums > 6])

# Double every element of nums
```

```
## [ 7  8  9 10]
```

```python
nums_dbl = nums * 2
print(nums_dbl)

# Replace the third column of nums
```

```
## [[ 2  4  6  8 10]
##  [12 14 16 18 20]]
```

```python
nums[:,2] = nums[:,2] + 1
print(nums)
```

```
## [[ 1  2  4  4  5]
##  [ 6  7  9  9 10]]
```

<div class=""><p>When compared to a list object, what are two advantages of using a <code>numpy</code> array?</p></div>

- [ ] A <code>numpy</code> array is the only data structure that can be used with the <code>numpy</code> package and often has less verbose indexing syntax.
- [x] A <code>numpy</code> array contains homogeneous data types (which reduces memory consumption) and provides the ability to apply operations on all elements through broadcasting.
- [ ] A <code>numpy</code> array supports boolean indexing and has much better one-dimensional indexing capabilities.
- [ ] Both a list object and a <code>numpy</code> array are identical.

<p class="">Well done! You're slicing <code>numpy</code> arrays like a pro and learning how to take advantage of NumPy's broadcasting concept. Using <code>numpy</code> arrays allows you to take advantage of an array's memory efficient nature and easily perform mathematical operations on your data.</p>

### Bringing it all together: Festivus!


<div class>
<p>In this exercise, you will be throwing a party—a Festivus if you will! </p>
<p>You have a list of guests (the <code>names</code> list). Each guest, for whatever reason, has decided to show up to the party in 10-minute increments. For example, Jerry shows up to Festivus 10 minutes into the party's start time, Kramer shows up 20 minutes into the party, and so on and so forth.</p>
<p>We want to write a few simple lines of code, using the built-ins we have covered, to welcome each of your guests and let them know how many minutes late they are to your party. Note that <code>numpy</code> has been imported into your session as <code>np</code> and the <code>names</code> list has been loaded as well.</p>
<p>Let's welcome your guests!</p>
</div>

```python
# edited/added
def welcome_guest(guest_and_time):
    """
    Returns a welcome string for the guest_and_time tuple.
    
    Args:
        guest_and_time (tuple): The guest and time tuple to create
            a welcome string for.
            
    Returns:
        welcome_string (str): A string welcoming the guest to Festivus.
        'Welcome to Festivus {guest}... You're {time} min late.'
    
    """
    guest = guest_and_time[0]
    arrival_time = guest_and_time[1]
    welcome_string = "Welcome to Festivus {}... You're {} min late.".format(guest,arrival_time)
    return welcome_string
```
<li>Use <code>range()</code> to create a list of arrival times (10 through 50 incremented by 10). Create the list <code>arrival_times</code> by unpacking the <em>range object</em>.</li>

```python
# Create a list of arrival times
arrival_times = [*range(10, 60, 10)]

print(arrival_times)
```

```
## [10, 20, 30, 40, 50]
```

<li>You realize your clock is three minutes fast. Convert the <code>arrival_times</code> list into a <code>numpy</code> array (called <code>arrival_times_np</code>) and use NumPy broadcasting to subtract three minutes from each arrival time.</li>

```python
# Create a list of arrival times
arrival_times = [*range(10,60,10)]

# Convert arrival_times to an array and update the times
arrival_times_np = np.array(arrival_times)
new_times = arrival_times_np - 3

print(new_times)
```

```
## [ 7 17 27 37 47]
```

<li>Use list comprehension with <code>enumerate()</code> to pair each guest in the <code>names</code> list to their updated arrival time in the <code>new_times</code> array. You'll need to use the index variable created from using <code>enumerate()</code> on <code>new_times</code> to index the <code>names</code> list.</li>

```python
# Create a list of arrival times
arrival_times = [*range(10,60,10)]

# Convert arrival_times to an array and update the times
arrival_times_np = np.array(arrival_times)
new_times = arrival_times_np - 3

# Use list comprehension and enumerate to pair guests to new times
guest_arrivals = [(names[i],time) for i,time in enumerate(new_times)]

print(guest_arrivals)
```

```
## [('Jerry', 7), ('Kramer', 17), ('Elaine', 27), ('George', 37), ('Newman', 47)]
```

<li>A function named <code>welcome_guest()</code> has been pre-loaded into your session. Use <code>map()</code> to apply this function to each element of the <code>guest_arrivals</code> list and save it as the variable <code>welcome_map</code>.</li>

```python
# Create a list of arrival times
arrival_times = [*range(10,60,10)]

# Convert arrival_times to an array and update the times
arrival_times_np = np.array(arrival_times)
new_times = arrival_times_np - 3

# Use list comprehension and enumerate to pair guests to new times
guest_arrivals = [(names[i],time) for i,time in enumerate(new_times)]

# Map the welcome_guest function to each (guest,time) pair
welcome_map = map(welcome_guest, guest_arrivals)

guest_welcomes = [*welcome_map]
print(*guest_welcomes, sep='\n')
```

```
## Welcome to Festivus Jerry... You're 7 min late.
## Welcome to Festivus Kramer... You're 17 min late.
## Welcome to Festivus Elaine... You're 27 min late.
## Welcome to Festivus George... You're 37 min late.
## Welcome to Festivus Newman... You're 47 min late.
```

<p class="">Congratulations and happy Festivus! You're using Python built-ins like a pro and well on your way to writing efficient Python code. Believe it or not, there is a way to make these simple lines of code even more efficient! We'll cover this in a future chapter, so continue on to see how!</p>

# Timing and profiling code

<p class="">In this chapter, you will learn how to gather and compare runtimes between different coding approaches.  You'll practice using the line_profiler and memory_profiler packages to profile your code base and spot bottlenecks. Then, you'll put your learnings to practice by replacing these bottlenecks with efficient Python code.</p>

## Examining runtime



### Using %timeit: your turn!


<div class>
<p>You'd like to create a list of integers from 0 to 50 using the <code>range()</code> function. However, you are unsure whether using list comprehension or unpacking the <em>range object</em> into a list is faster. Let's use <code>%timeit</code> to find the best implementation.</p>
<p>For your convenience, a reference table of time orders of magnitude is provided below (faster at the top). </p>
<table>
<thead><tr>
<th>symbol</th>
<th>name</th>
<th>unit (s)</th>
</tr></thead>
<tbody>
<tr>
<td>ns</td>
<td>nanosecond</td>
<td>10<sup>-9</sup>
</td>
</tr>
<tr>
<td>µs (us)</td>
<td>microsecond</td>
<td>10<sup>-6</sup>
</td>
</tr>
<tr>
<td>ms</td>
<td>millisecond</td>
<td>10<sup>-3</sup>
</td>
</tr>
<tr>
<td>s</td>
<td>second</td>
<td>10<sup>0</sup>
</td>
</tr>
</tbody>
</table>
</div>

```python
# edited/added
```
<li>Use list comprehension and <code>range()</code> to create a list of integers from 0 to 50 called <code>nums_list_comp</code>.</li>

```python
# Create a list of integers (0-50) using list comprehension
nums_list_comp = [num for num in range(51)]
print(nums_list_comp)
```

```
## [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50]
```
<li>Use <code>range()</code> to create a list of integers from 0 to 50 and unpack its contents into a list called <code>nums_unpack</code>.</li>

```python
# Create a list of integers (0-50) using list comprehension
nums_list_comp = [num for num in range(51)]
print(nums_list_comp)

# Create a list of integers (0-50) by unpacking range
```

```
## [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50]
```

```python
nums_unpack = [*range(51)]
print(nums_unpack)
```

```
## [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50]
```

<div class=""><p>Use <code>%timeit</code> <strong>within your IPython console</strong> (i.e. <strong>not</strong> within the script.py window) to compare the runtimes for creating a list of integers from 0 to 50 using list comprehension vs. unpacking the <em>range object</em>. Don't include the <code>print()</code> statements when timing.</p>
<p><strong>Which method was faster?</strong></p></div>

- [ ] List comprehension was faster than unpacking <code>range()</code>.
- [x] Unpacking the <em>range object</em> was faster than list comprehension.
- [ ] Both methods had the same runtime.

<p class="">Nice work! You used <code>%timeit</code> to gather and compare runtimes! Although list comprehension is a useful and powerful tool, sometimes unpacking an object can save time and looks a little cleaner.</p>

### Using %timeit: specifying number of runs and loops


<div class>
<p>A list of 480 superheroes has been loaded into your session (called <code>heroes</code>). You'd like to analyze the runtime for converting this <code>heroes</code> list into a set. Instead of relying on the default settings for <code>%timeit</code>, you'd like to only use 5 runs and 25 loops per each run.</p>
<p><strong>What is the correct syntax when using <code>%timeit</code> and only using 5 runs with 25 loops per each run?</strong></p>
</div>

- [ ] <code>timeit -runs5 -loops25 set(heroes)</code>
- [ ] <code>%%timeit -r5 -n25 set(heroes)</code>
- [ ] <code>%timeit set(heroes), 5, 25</code>
- [x] <code>%timeit -r5 -n25 set(heroes)</code>

<p class="">Correct! <code>%timeit</code> lets you specify the number of runs and number of loops you want to consider with the <code>-r</code> and <code>-n</code> flags. You can use <code>-r5</code> and <code>-n25</code> to specify 5 iterations each with 25 loops when calculating the average and standard deviation of runtime for your code.</p>

### Using %timeit: formal name or literal syntax


<div class>
<p>Python allows you to create data structures using <strong>either</strong> a <em>formal name</em> or a <em>literal syntax</em>. In this exercise, you'll explore how using a <em>literal syntax</em> for creating a data structure can speed up runtimes.</p>
<table>
<thead><tr>
<th>data structure</th>
<th>formal name</th>
<th>literal syntax</th>
</tr></thead>
<tbody>
<tr>
<td>list</td>
<td><code>list()</code></td>
<td><code>[]</code></td>
</tr>
<tr>
<td>dictionary</td>
<td><code>dict()</code></td>
<td><code>{}</code></td>
</tr>
<tr>
<td>tuple</td>
<td><code>tuple()</code></td>
<td><code>()</code></td>
</tr>
</tbody>
</table>
</div>

```python
# edited/added
```
<li>Create an empty list called <code>formal_list</code> using the formal name (<code>list()</code>).</li>
<li>Create an empty list called <code>literal_list</code> using the literal syntax (<code>[]</code>).</li>

```python
# Create a list using the formal name
formal_list = list()
print(formal_list)

# Create a list using the literal syntax
```

```
## []
```

```python
literal_list = []
print(literal_list)
```

```
## []
```

<li>Print out the type of <code>formal_list</code> and <code>literal_list</code> to show that both naming conventions create a list.</li>

```python
# Create a list using the formal name
formal_list = list()
print(formal_list)

# Create a list using the literal syntax
```

```
## []
```

```python
literal_list = []
print(literal_list)

# Print out the type of formal_list
```

```
## []
```

```python
print(type(formal_list))

# Print out the type of literal_list
```

```
## <class 'list'>
```

```python
print(type(literal_list))
```

```
## <class 'list'>
```

<div class=""><p>Use <code>%timeit</code> <strong>in your IPython console</strong> to compare runtimes between creating a list using the formal name (<code>list()</code>) and the literal syntax (<code>[]</code>). Don't include the <code>print()</code> statements when timing.</p>
<p><strong>Which naming convention is faster?</strong></p></div>

- [ ] Using the formal name (<code>list()</code>) to create a list is faster.
- [x] Using the literal syntax (<code>[]</code>) to create a list is faster.
- [ ] Both naming conventions have the same runtime.

<p class="">Great job! Using Python's literal syntax to define a data structure can speed up your runtime. Consider using the literal syntaxes (like <code>[]</code> instead of <code>list()</code>, <code>{}</code> instead of <code>dict()</code>, or <code>()</code> instead of <code>tuple()</code>), where applicable, to gain some speed.</p>

### Using cell magic mode (%%timeit)


<div class>
<p>From here on out, you'll be working with a superheroes dataset. For this exercise, a list of each hero's weight in kilograms (called <code>wts</code>) is loaded into your session. You'd like to convert these weights into pounds.</p>
<p>You could accomplish this using the below for loop:</p>
<pre><code>hero_wts_lbs = []
for wt in wts:
    hero_wts_lbs.append(wt * 2.20462)
</code></pre>
<p>Or you could use a <code>numpy</code> array to accomplish this task:</p>
<pre><code>wts_np = np.array(wts)
hero_wts_lbs_np = wts_np * 2.20462
</code></pre>
<p>Use <code>%%timeit</code> <strong>in your IPython console</strong> to compare runtimes between these two approaches. Make sure to press <code>SHIFT+ENTER</code> after the magic command to add a new line before writing the code you wish to time. After you've finished coding, answer the following question:</p>
<p><strong>Which of the above techniques is faster?</strong></p>
</div>

- [ ] The for loop technique was faster.
- [x] The <code>numpy</code> technique was faster.
- [ ] Both techniques had similar runtimes.

<p class="">Nice work! You used <code>%%timeit</code> (<em>cell magic mode</em>) to time multiple lines of code. Converting the <code>wts</code> list into a NumPy array and taking advantage of NumPy array broadcasting saved you some time! Moving forward, remember that you can use <code>%timeit</code> to gather runtime for a single line of code (<em>line magic mode</em>) and <code>%%timeit</code> to get the runtime for multiple lines of code.</p>

## Code profiling for runtime



### Pop quiz: steps for using %lprun

<div class=""><p>Below is the <code>convert_units()</code> function, which converts the heights and weights of our favorite superheroes from metric units to Imperial units. </p>
<pre><code>def convert_units(heroes, heights, weights):

    new_hts = [ht * 0.39370  for ht in heights]
    new_wts = [wt * 2.20462  for wt in weights]

    hero_data = {}

    for i,hero in enumerate(heroes):
        hero_data[hero] = (new_hts[i], new_wts[i])

    return hero_data
</code></pre>
<p>Suppose you have a list of superheroes (named <code>heroes</code>) along with each hero's height (in centimeters) and weight (in kilograms) loaded as NumPy arrays (named <code>hts</code> and <code>wts</code> respectively).</p>
<p><strong>What are the necessary steps you need to take in order to profile the <code>convert_units()</code> function acting on your superheroes data if you'd like to see line-by-line runtimes?</strong></p></div>

- [ ] Use <code>%load_ext line_profiler</code> to load the <code>line_profiler</code> within your IPython session.
- [ ] Use <code>%lprun -f convert_units convert_units(heroes, hts, wts)</code> to get line-by-line runtimes.
- [ ] Use <code>%timeit convert_units(heroes, hts, wts)</code> to gather runtimes.
- [ ] The first and second options from above are necessary.

<p class="dc-completion-pane__message dc-u-maxw-100pc">Great job! Now that you've reviewed the necessary steps for profiling a function for runtime, it's time for you to practice profiling on your own!</p>

### Using %lprun: spot bottlenecks


<div class>
<p>Profiling a function allows you to dig deeper into the function's source code and potentially spot bottlenecks. When you see certain lines of code taking up the majority of the function's runtime, it is an indication that you may want to deploy a different, more efficient technique.</p>
<p>Lets dig deeper into the <code>convert_units()</code> function. </p>
<pre><code>def convert_units(heroes, heights, weights):

    new_hts = [ht * 0.39370  for ht in heights]
    new_wts = [wt * 2.20462  for wt in weights]

    hero_data = {}

    for i,hero in enumerate(heroes):
        hero_data[hero] = (new_hts[i], new_wts[i])

    return hero_data
</code></pre>
<p>Load the <code>line_profiler</code> package into your IPython session. Then, use <code>%lprun</code> to profile the <code>convert_units()</code> function acting on your superheroes data. Remember to use the special syntax for working with <code>%lprun</code> (you'll have to provide a <code>-f</code> flag specifying the function you'd like to profile).</p>
<p>The <code>convert_units()</code> function, <code>heroes</code> list, <code>hts</code> array, and <code>wts</code> array have been loaded into your session. After you've finished coding, answer the following question:</p>
<p><strong>What percentage of time is spent on the <code>new_hts</code> list comprehension line of code relative to the total amount of time spent in the <code>convert_units()</code> function?</strong></p>
</div>

- [ ] 0% - 10%
- [x] 11% - 20%
- [ ] 21% - 50%
- [ ] 51% - 100%

<p class="">That's right! This seems like it may be a potential bottleneck in your function. Can you think of a way to make this more efficient? You'll explore a possible upgrade in the next exercise.</p>

### Using %lprun: fix the bottleneck


<div class>
<p>In the previous exercise, you profiled the <code>convert_units()</code> function and saw that the <code>new_hts</code> list comprehension could be a potential bottleneck. Did you notice that the <code>new_wts</code> list comprehension also accounted for a similar percentage of the runtime? This is an indication that you may want to create the <code>new_hts</code> and <code>new_wts</code> objects using a different technique.</p>
<p>Since the height and weight of each hero is stored in a <code>numpy</code> array, you can use array broadcasting rather than list comprehension to convert the heights and weights. This has been implemented in the below function:</p>
<pre><code>def convert_units_broadcast(heroes, heights, weights):

    # Array broadcasting instead of list comprehension
    new_hts = heights * 0.39370
    new_wts = weights * 2.20462

    hero_data = {}

    for i,hero in enumerate(heroes):
        hero_data[hero] = (new_hts[i], new_wts[i])

    return hero_data
</code></pre>
<p>Load the <code>line_profiler</code> package into your IPython session. Then, use <code>%lprun</code> to profile the <code>convert_units_broadcast()</code> function acting on your superheroes data. The <code>convert_units_broadcast()</code> function, <code>heroes</code> list, <code>hts</code> array, and <code>wts</code> array have been loaded into your session. After you've finished coding, answer the following question:</p>
<p><strong>What percentage of time is spent on the <code>new_hts</code> array broadcasting line of code relative to the total amount of time spent in the <code>convert_units_broadcast()</code> function?</strong></p>
</div>

- [x] 0% - 10%
- [ ] 11% - 20%
- [ ] 21% - 50%
- [ ] 51% - 100%

<p class="">That's correct! By profiling the <code>convert_units()</code> function, you were able to see that using list comprehension was not the most efficient solution for creating the <code>new_hts</code> and <code>new_wts</code> objects. You also saw that using array broadcasting in the <code>convert_units_broadcast()</code> function dramatically decreased the percentage of time spent executing these lines of code. You may have noticed that your function still takes a while to iterate through the for loop. Don't worry; you'll cover how to make this loop more efficient in a later chapter.</p>

## Code profiling for memory usage



### Pop quiz: steps for using %mprun

<div class=""><p>Suppose you have a list of superheroes (named <code>heroes</code>) along with each hero's height (in centimeters) and weight (in kilograms) loaded as NumPy arrays (named <code>hts</code> and <code>wts</code>, respectively). You also have a <code>convert_units()</code> function saved in a file titled <code>hero_funcs.py</code>.</p>
<p><strong>What are the necessary steps you need to take in order to profile the <code>convert_units()</code> function acting on your superheroes data if you'd like to see the line-by-line memory consumption of <code>convert_units()</code>?</strong></p></div>

- [ ] Use the command <code>from hero_funcs import convert_units</code> to load the function you'd like to profile.
- [ ] Use <code>%load_ext memory_profiler</code> to load the <code>memory_profiler</code> within your IPython session.
- [ ] Use <code>%mprun -f convert_units convert_units(heroes, hts, wts)</code> to get line-by-line memory allocations.
- [x] All of the above.

<p class="dc-completion-pane__message dc-u-maxw-100pc">Great job! Remember that using <code>%mprun</code> requires one additional step compared to using <code>%lprun</code> (i.e., you need to import the function in order to use <code>%mprun</code> on it). Now that you've reviewed these necessary steps, practice profiling for memory usage!</p>

### Using %mprun: Hero BMI


<div class>
<p>You'd like to calculate the body mass index (BMI) for a selected sample of heroes. BMI can be calculated using the below formula:</p>
<p><img src="https://assets.datacamp.com/production/repositories/3581/datasets/9d4abcd3b3d8c4911f8733bcf1b675fb1dbd023e/bmi_formula_pic.png" alt="BMI = mass(kg) / height(m)^2" width="150" height="60"></p>
<p>A random sample of 25,000 superheroes has been loaded into your session as an array called <code>sample_indices</code>. This sample is a list of <em>indices</em> that corresponds to each superhero's index selected from the <code>heroes</code> list.</p>
<p>A function named <code>calc_bmi_lists</code> has also been created and saved to a file titled <code>bmi_lists.py</code>. For convenience, it is displayed below:</p>
<pre><code>def calc_bmi_lists(sample_indices, hts, wts):

    # Gather sample heights and weights as lists
    s_hts = [hts[i] for i in sample_indices]
    s_wts = [wts[i] for i in sample_indices]

    # Convert heights from cm to m and square with list comprehension
    s_hts_m_sqr = [(ht / 100) ** 2 for ht in s_hts]

    # Calculate BMIs as a list with list comprehension
    bmis = [s_wts[i] / s_hts_m_sqr[i] for i in range(len(sample_indices))]

    return bmis
</code></pre>
<p>Notice that this function performs all necessary calculations using <strong>list comprehension</strong> (hence the name <code>calc_bmi_lists()</code>). Dig deeper into this function and analyze the memory footprint for performing your calculations using <strong>lists</strong>:</p>
<ul>
<li>Load the <code>memory_profiler</code> package into your IPython session.</li>
<li>Import <code>calc_bmi_lists</code> from <code>bmi_lists</code>.</li>
<li>Once you've completed the above steps, use <code>%mprun</code> to profile the <code>calc_bmi_lists()</code> function acting on your superheroes data.
The <code>hts</code> array and <code>wts</code> array have already been loaded into your session.</li>
</ul>
<p>After you've finished coding, answer the following question:</p>
<p><strong>How much memory do the list comprehension lines of code consume in the <code>calc_bmi_lists()</code> function? (i.e., what is the total sum of the <code>Increment</code> column for these four lines of code?)</strong></p>
</div>

- [ ] 20.0 MiB - 30.0 MiB
- [x] 0.1 MiB - 2.0 MiB
- [ ] 10.0 MiB - 15.0 MiB
- [ ] 0.0 MiB

<p class="">Correct! Using a list comprehension approach allocates anywhere from 0.1 MiB to 2 MiB of memory to calculate your BMIs.<br><br>If you run <code>%mprun</code> multiple times within your session, you may notice that the <code>Increment</code> column reports <code>0.0 MiB</code> for all lines of code. This is due to a limitation with the magic command. After running <code>%mprun</code> once, the memory allocation analyzed previously is taken into account for all consecutive runs and <code>%mprun</code> will start from the place the first run left off.<br><br>Now that we've profiled the <code>calc_bmi_lists()</code> function, let's see if you can do better with a different approach.</p>

### Using %mprun: Hero BMI 2.0


<div class>
<p>Let's see if using a different approach to calculate the BMIs can save some memory. If you remember, each hero's height and weight is stored in a <code>numpy</code> array. That means you can use NumPy's handy array indexing capabilities and broadcasting to perform your calculations. A function named <code>calc_bmi_arrays</code> has been created and saved to a file titled <code>bmi_arrays.py</code>. For convenience, it is displayed below:</p>
<pre><code>def calc_bmi_arrays(sample_indices, hts, wts):

    # Gather sample heights and weights as arrays
    s_hts = hts[sample_indices]
    s_wts = wts[sample_indices]

    # Convert heights from cm to m and square with broadcasting
    s_hts_m_sqr = (s_hts / 100) ** 2

    # Calculate BMIs as an array using broadcasting
    bmis = s_wts / s_hts_m_sqr

    return bmis
</code></pre>
<p>Notice that this function performs all necessary calculations using <strong>arrays</strong>.</p>
<p>Let's see if this updated array approach decreases your memory footprint:</p>
<ul>
<li>Load the <code>memory_profiler</code> package into your IPython session.</li>
<li>Import <code>calc_bmi_arrays</code> from <code>bmi_arrays</code>.</li>
<li>Once you've completed the above steps, use <code>%mprun</code> to profile the <code>calc_bmi_arrays()</code> function acting on your superheroes data.
The <code>sample_indices</code> array, <code>hts</code> array, and <code>wts</code> array have been loaded into your session.</li>
</ul>
<p>After you've finished coding, answer the following question:</p>
<p><strong>How much memory do the array indexing and broadcasting lines of code consume in the <code>calc_bmi_array()</code> function? (i.e., what is the total sum of the <code>Increment</code> column for these four lines of code?)</strong></p>
</div>

- [ ] 10.0 MiB - 15.0 MiB
- [ ] 0.0 MiB
- [ ] 20.0 MiB - 30.0 MiB
- [x] 0.1 MiB - 2.0 MiB

<p class="">That's right! By implementing an array approach, you were able to shave off a few MiBs. Although this isn't a colossal gain, it still decreases your code's overhead. If your input data grows over time, these small improvements could add up to some major efficiency gains.</p>

### Bringing it all together: Star Wars profiling


<div class>
<p>A list of 480 superheroes has been loaded into your session (called <code>heroes</code>) as well as a list of each hero's corresponding publisher (called <code>publishers</code>).</p>
<p>You'd like to filter the <code>heroes</code> list based on a hero's specific publisher, but are unsure which of the below functions is more efficient. </p>
<pre><code>def get_publisher_heroes(heroes, publishers, desired_publisher):

    desired_heroes = []

    for i,pub in enumerate(publishers):
        if pub == desired_publisher:
            desired_heroes.append(heroes[i])

    return desired_heroes
</code></pre>
<pre><code>def get_publisher_heroes_np(heroes, publishers, desired_publisher):

    heroes_np = np.array(heroes)
    pubs_np = np.array(publishers)

    desired_heroes = heroes_np[pubs_np == desired_publisher]

    return desired_heroes
</code></pre>
</div>

```python
# edited/added
import pandas as pd
heroes = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1531075102&single=true&output=csv", header = None).iloc[:,0].tolist()
publishers = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1911812864&single=true&output=csv", header = None).iloc[:,0].tolist()

def get_publisher_heroes(heroes, publishers, desired_publisher):

    desired_heroes = []

    for i,pub in enumerate(publishers):
        if pub == desired_publisher:
            desired_heroes.append(heroes[i])

    return desired_heroes
  
def get_publisher_heroes_np(heroes, publishers, desired_publisher):

    heroes_np = np.array(heroes)
    pubs_np = np.array(publishers)

    desired_heroes = heroes_np[pubs_np == desired_publisher]

    return desired_heroes
```
<li>Use the <code>get_publisher_heroes()</code> function and the <code>get_publisher_heroes_np()</code> function to collect heroes from the Star Wars universe. The <code>desired_publisher</code> for Star Wars is <code>'George Lucas'</code>.</li>

```python
# Use get_publisher_heroes() to gather Star Wars heroes
star_wars_heroes = get_publisher_heroes(heroes, publishers, 'George Lucas')

print(star_wars_heroes)
```

```
## ['Darth Vader', 'Han Solo', 'Luke Skywalker', 'Yoda']
```

```python
print(type(star_wars_heroes))

# Use get_publisher_heroes_np() to gather Star Wars heroes
```

```
## <class 'list'>
```

```python
star_wars_heroes_np = get_publisher_heroes_np(heroes, publishers, 'George Lucas')

print(star_wars_heroes_np)
```

```
## ['Darth Vader' 'Han Solo' 'Luke Skywalker' 'Yoda']
```

```python
print(type(star_wars_heroes_np))
```

```
## <class 'numpy.ndarray'>
```

<div class=""><ul>
<li><strong>Within your IPython console</strong>, load the <code>line_profiler</code> and use <code>%lprun</code> to profile the two functions for line-by-line runtime. When using <code>%lprun</code>, use each function to gather the Star Wars heroes as you did in the previous step. After you've finished profiling, answer the following question:</li>
</ul>
<p><strong>Which function has the fastest runtime?</strong></p></div>

- [ ] <code>get_publisher_heroes()</code> is faster.
- [x] <code>get_publisher_heroes_np()</code> is faster.
- [ ] Both functions have the same runtime.

<div class=""><ul>
<li><strong>Within your IPython console</strong>, load the <code>memory_profiler</code> and use <code>%mprun</code> to profile the two functions for line-by-line memory consumption.</li>
</ul>
<p>The <code>get_publisher_heroes()</code> function and <code>get_publisher_heroes_np()</code> function have been saved within a file titled <code>hero_funcs.py</code> (i.e., you can import both functions from <code>hero_funcs</code>). When using <code>%mprun</code>, use each function to gather the Star Wars heroes as you did in the previous step. After you've finished profiling, answer the following question:</p>
<p><strong>Which function uses the least amount of memory?</strong></p></div>

- [ ] <code>get_publisher_heroes()</code> consumes less memory.
- [ ] <code>get_publisher_heroes_np()</code> consumes less memory.
- [x] Both functions have the same memory consumption.

<div class=""><p>Based on your runtime profiling and memory allocation profiling, which function would you choose to gather Star Wars heroes?</p></div>

- [ ] I would use <code>get_publisher_heroes()</code>.
- [x] I would use <code>get_publisher_heroes_np()</code>.
- [ ] I could use either function since their runtimes, and memory usage were identical.

<p class="">The Force is strong with this one! You're timing and profiling like a true Jedi. Now that you have the tools to evaluate code efficiencies, it's time to put them to use and start writing efficient Python code.</p>

# Gaining efficiencies

<p class="">This chapter covers more complex efficiency tips and tricks. You'll learn a few useful built-in modules for writing efficient code and practice using set theory.  You'll then learn about looping patterns in Python and how to make them more efficient.</p>

## Efficiently combining, counting, and iterating



### Combining Pokémon names and types


<div class>
<p>Three lists have been loaded into your session from a dataset that contains 720 Pokémon:</p>
<ul>
<li>The <code>names</code> list contains the names of each Pokémon.</li>
<li>The <code>primary_types</code> list contains the corresponding <strong>primary</strong> type of each Pokémon.</li>
<li>The <code>secondary_types</code> list contains the corresponding <strong>secondary</strong> type of each Pokémon (<code>nan</code> if the Pokémon has only one type).</li>
</ul>
<p>We want to combine each Pokémon's name and types together so that you easily see a description of each Pokémon. Practice using <code>zip()</code> to accomplish this task.</p>
</div>
<div class="exercise--instructions__content"><p>Combine the <code>names</code> list and the <code>primary_types</code> list into a new list object (called <code>names_type1</code>).</p></div>

```python
# edited/added
names = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=728081830&single=true&output=csv", header = None).iloc[:,0].tolist()
primary_types = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1599592048&single=true&output=csv", header = None).iloc[:,0].tolist()
secondary_types = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1185014273&single=true&output=csv", header = None).iloc[:,0].tolist()

# Combine names and primary_types
names_type1 = [*zip(names, primary_types)]

print(*names_type1[:5], sep='\n')
```

```
## ('Abomasnow', 'Grass')
## ('Abra', 'Psychic')
## ('Absol', 'Dark')
## ('Accelgor', 'Bug')
## ('Aerodactyl', 'Rock')
```

<div class="exercise--instructions__content"><p>Combine <code>names</code>, <code>primary_types</code>, and <code>secondary_types</code> (in that order) using <code>zip()</code> and unpack the <em>zip object</em> into a new list.</p></div>

```python
# Combine all three lists together
names_types = [*zip(names, primary_types, secondary_types)]

print(*names_types[:5], sep='\n')
```

```
## ('Abomasnow', 'Grass', 'Ice')
## ('Abra', 'Psychic', 'Flying')
## ('Absol', 'Dark', 'Rock')
## ('Accelgor', 'Bug', 'Flying')
## ('Aerodactyl', 'Rock', 'Ice')
```

<div class="exercise--instructions__content"><p>Use <code>zip()</code> to combine the <strong>first five items</strong> from the <code>names</code> list and the <strong>first three items</strong> from the <code>primary_types</code> list.</p></div>

```python
# Combine five items from names and three items from primary_types
differing_lengths = [*zip(names[:5], primary_types[:3])]

print(*differing_lengths, sep='\n')
```

```
## ('Abomasnow', 'Grass')
## ('Abra', 'Psychic')
## ('Absol', 'Dark')
```

<p class="">Good job! You practiced using <code>zip()</code> to combine multiple objects together. This is a nice function that allows you to easily combine two or more objects. <br> <br> Did you notice that if you provide <code>zip()</code> with objects of differing lengths, it will only combine until the smallest lengthed object is exhausted?</p>

### Counting Pokémon from a sample


<div class>
<p>A sample of 500 Pokémon has been generated, and three lists from this sample have been loaded into your session:</p>
<ul>
<li>The <code>names</code> list contains the names of each Pokémon in the sample.</li>
<li>The <code>primary_types</code> list containing the corresponding <strong>primary</strong> type of each Pokémon in the sample.</li>
<li>The <code>generations</code> list contains the corresponding <strong>generation</strong> of each Pokémon in the sample.</li>
</ul>
<p>You want to quickly gather a few counts from these lists to better understand the sample that was generated. Use <code>Counter</code> from the <code>collections</code> module to explore what types of Pokémon are in your sample, what generations they come from, and how many Pokémon have a name that starts with a specific letter.</p>
<p><code>Counter</code> has already been imported into your session for convenience.</p>
</div>

```python
# edited/added
from collections import Counter
names = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1939281460&single=true&output=csv", header = None).iloc[:,0].tolist()
primary_types = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=642695943&single=true&output=csv", header = None).iloc[:,0].tolist()
generations = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1609546095&single=true&output=csv", header = None).iloc[:,0].tolist()
```
<li>Collect the count of each primary type from the sample.</li>
<li>Collect the count of each generation from the sample.</li>
<li>Use list comprehension to collect the first letter of each Pokémon in the <code>names</code> list. Save this as <code>starting_letters</code>.</li>
<li>Collect the count of starting letters from the <code>starting_letters</code> list. Save this as <code>starting_letters_count</code>.</li>

```python
# Collect the count of primary types
type_count = Counter(primary_types)
print(type_count, '\n')

# Collect the count of generations
```

```
## Counter({'Water': 66, 'Normal': 64, 'Bug': 51, 'Grass': 47, 'Psychic': 31, 'Rock': 29, 'Fire': 27, 'Electric': 25, 'Ground': 23, 'Fighting': 23, 'Poison': 22, 'Steel': 18, 'Ice': 16, 'Fairy': 16, 'Dragon': 16, 'Ghost': 13, 'Dark': 13})
```

```python
gen_count = Counter(generations)
print(gen_count, '\n')

# Use list comprehension to get each Pokémon's starting letter
```

```
## Counter({5: 122, 3: 103, 1: 99, 4: 78, 2: 51, 6: 47})
```

```python
starting_letters = [name[0] for name in names]

# Collect the count of Pokémon for each starting_letter
starting_letters_count = Counter(starting_letters)
print(starting_letters_count)
```

```
## Counter({'S': 83, 'C': 46, 'D': 33, 'M': 32, 'L': 29, 'G': 29, 'B': 28, 'P': 23, 'A': 22, 'K': 20, 'E': 19, 'W': 19, 'T': 19, 'F': 18, 'H': 15, 'R': 14, 'N': 13, 'V': 10, 'Z': 8, 'J': 7, 'I': 4, 'O': 3, 'Y': 3, 'U': 2, 'X': 1})
```

<p class="">Great job! You used <code>Counter</code> from the <code>collections</code> module to better understand the sample of 500 Pokémon that was generated. The sample's most common Pokémon type was <code>'Water'</code> and the sample's least common Pokémon types were <code>'Ghost'</code> and <code>'Dark'</code>. Did you also notice that most of the Pokémon in the sample came from generation <code>5</code> and had a starting letter of <code>'S'</code>?</p>

### Combinations of Pokémon


<div class>
<p>Ash, a Pokémon trainer, encounters a group of five Pokémon. These Pokémon have been loaded into a list within your session (called <code>pokemon</code>) and printed into the console for your convenience.</p>
<p>Ash would like to try to catch some of these Pokémon, but his Pokédex can only store <strong>two</strong> Pokémon at a time. Let's use <code>combinations</code> from the <code>itertools</code> module to see what the possible pairs of Pokémon are that Ash could catch.</p>
</div>

```python
# edited/added
pokemon = ['Geodude', 'Cubone', 'Lickitung', 'Persian', 'Diglett']
```
<li>Import <code>combinations</code> from <code>itertools</code>.</li>
<li>Create a <em>combinations object</em> called <code>combos_obj</code> that contains all possible pairs of Pokémon from the <code>pokemon</code> list. A pair has <code>2</code> Pokémon.</li>
<li>Unpack <code>combos_obj</code> into a list called <code>combos_2</code>.</li>
<li>Ash upgraded his Pokédex so that it can now store <strong>four</strong> Pokémon. Use <code>combinations</code> to collect all possible combinations of <code>4</code> different Pokémon. Save these combinations <strong>directly into a list</strong> called <code>combos_4</code> using the star character (<code>*</code>).</li>

```python
# Import combinations from itertools
from itertools import combinations

# Create a combination object with pairs of Pokémon
combos_obj = combinations(pokemon, 2)
print(type(combos_obj), '\n')

# Convert combos_obj to a list by unpacking
```

```
## <class 'itertools.combinations'>
```

```python
combos_2 = [*combos_obj]
print(combos_2, '\n')

# Collect all possible combinations of 4 Pokémon directly into a list
```

```
## [('Geodude', 'Cubone'), ('Geodude', 'Lickitung'), ('Geodude', 'Persian'), ('Geodude', 'Diglett'), ('Cubone', 'Lickitung'), ('Cubone', 'Persian'), ('Cubone', 'Diglett'), ('Lickitung', 'Persian'), ('Lickitung', 'Diglett'), ('Persian', 'Diglett')]
```

```python
combos_4 = [*combinations(pokemon, 4)]
print(combos_4)
```

```
## [('Geodude', 'Cubone', 'Lickitung', 'Persian'), ('Geodude', 'Cubone', 'Lickitung', 'Diglett'), ('Geodude', 'Cubone', 'Persian', 'Diglett'), ('Geodude', 'Lickitung', 'Persian', 'Diglett'), ('Cubone', 'Lickitung', 'Persian', 'Diglett')]
```

<p class="">Awesome! You used <code>combinations()</code> from <code>itertools</code> to collect various combination-tuples from a list. <code>combinations()</code> allows you to specify any size of combinations by passing an integer as the second argument. Ash has <code>10</code> combination options when his Pokédex can store only two Pokémon. He has <code>5</code> combination options when his Pokédex can store four Pokémon.</p>

## Set theory



### Comparing Pokédexes


<div class>
<p>Two Pokémon trainers, Ash and Misty, would like to compare their individual collections of Pokémon. Let's see what Pokémon they have in common and what Pokémon Ash has that Misty does not.</p>
<p>Both Ash and Misty's Pokédex (their collection of Pokémon) have been loaded into your session as lists called <code>ash_pokedex</code> and <code>misty_pokedex</code>. They have been printed into the console for your convenience.</p>
</div>

```python
# edited/added
ash_pokedex = ['Pikachu', 'Bulbasaur', 'Koffing', 'Spearow', 'Vulpix', 'Wigglytuff', 'Zubat', 'Rattata', 'Psyduck', 'Squirtle'] 
misty_pokedex = ['Krabby', 'Horsea', 'Slowbro', 'Tentacool', 'Vaporeon', 'Magikarp', 'Poliwag', 'Starmie', 'Psyduck', 'Squirtle']
```
<li>Convert both lists (<code>ash_pokedex</code> and <code>misty_pokedex</code>) to sets called <code>ash_set</code> and <code>misty_set</code> respectively.</li>
<li>Find the Pokémon that both Ash and Misty have in common using a set method.</li>
<li>Find the Pokémon that are within Ash's Pokédex but <strong>are not</strong> within Misty's Pokédex with a set method.</li>
<li>Use a set method to find the Pokémon that are unique to <strong>either</strong> Ash or Misty (i.e., the Pokémon that exist in <strong>exactly one</strong> of the Pokédexes but not both).</li>

```python
# Convert both lists to sets
ash_set = set(ash_pokedex)
misty_set = set(misty_pokedex)

# Find the Pokémon that exist in both sets
both = ash_set.intersection(misty_set)
print(both)

# Find the Pokémon that Ash has, and Misty does not have
```

```
## {'Squirtle', 'Psyduck'}
```

```python
ash_only = ash_set.difference(misty_set)
print(ash_only)

# Find the Pokémon that are in only one set (not both)
```

```
## {'Koffing', 'Wigglytuff', 'Spearow', 'Rattata', 'Bulbasaur', 'Vulpix', 'Zubat', 'Pikachu'}
```

```python
unique_to_set = ash_set.symmetric_difference(misty_set)
print(unique_to_set)
```

```
## {'Slowbro', 'Krabby', 'Vaporeon', 'Tentacool', 'Koffing', 'Spearow', 'Wigglytuff', 'Poliwag', 'Rattata', 'Bulbasaur', 'Vulpix', 'Magikarp', 'Starmie', 'Zubat', 'Pikachu', 'Horsea'}
```

<p class="">Great work! Using sets lets you do some cool comparisons between objects without the need to write a for loop. With a few lines of code, you were able to see that both Ash and Misty have <code>'Psyduck'</code> and <code>'Squirtle'</code> in their Pokédex. You were also able to see that Ash has <code>8</code> Pokémon that Misty does not have.</p>

### Searching for Pokémon


<div class>
<p>Two Pokémon trainers, Ash and Brock, have a collection of ten Pokémon each. Each trainer's Pokédex (their collection of Pokémon) has been loaded into your session as lists called <code>ash_pokedex</code> and <code>brock_pokedex</code> respectively.</p>
<p>You'd like to see if certain Pokémon are members of either Ash or Brock's Pokédex.</p>
<p>Let's compare using a <code>set</code> versus using a <code>list</code> when performing this membership testing.</p>
</div>

```python
# edited/added
brock_pokedex = ['Onix', 'Geodude', 'Zubat', 'Golem', 'Vulpix', 'Tauros', 'Kabutops', 'Omastar', 'Machop', 'Dugtrio']
```
<li>Convert Brock's Pokédex list (<code>brock_pokedex</code>) to a set called <code>brock_pokedex_set</code>.</li>

```python
# Convert Brock's Pokédex to a set
brock_pokedex_set = set(brock_pokedex)
print(brock_pokedex_set)
```

```
## {'Golem', 'Tauros', 'Geodude', 'Vulpix', 'Onix', 'Machop', 'Dugtrio', 'Kabutops', 'Omastar', 'Zubat'}
```
<li>Check if <code>'Psyduck'</code> is in Ash's Pokédex list (<code>ash_pokedex</code>) and if <code>'Psyduck'</code> is in Brock's Pokédex <strong>set</strong> (<code>brock_pokedex_set</code>).</li>

```python
# Convert Brock's Pokédex to a set
brock_pokedex_set = set(brock_pokedex)
print(brock_pokedex_set)

# Check if Psyduck is in Ash's list and Brock's set
```

```
## {'Golem', 'Tauros', 'Geodude', 'Vulpix', 'Onix', 'Machop', 'Dugtrio', 'Kabutops', 'Omastar', 'Zubat'}
```

```python
print('Psyduck' in ash_pokedex)
```

```
## True
```

```python
print('Psyduck' in brock_pokedex_set)
```

```
## False
```
<li>Check if <code>'Machop'</code> is in Ash's Pokédex list (<code>ash_pokedex</code>) and if <code>'Machop'</code> is in Brock's Pokédex <strong>set</strong> (<code>brock_pokedex_set</code>).</li>

```python
# Convert Brock's Pokédex to a set
brock_pokedex_set = set(brock_pokedex)
print(brock_pokedex_set)

# Check if Psyduck is in Ash's list and Brock's set
```

```
## {'Golem', 'Tauros', 'Geodude', 'Vulpix', 'Onix', 'Machop', 'Dugtrio', 'Kabutops', 'Omastar', 'Zubat'}
```

```python
print('Psyduck' in ash_pokedex)
```

```
## True
```

```python
print('Psyduck' in brock_pokedex_set)

# Check if Machop is in Ash's list and Brock's set
```

```
## False
```

```python
print('Machop' in ash_pokedex)
```

```
## False
```

```python
print('Machop' in brock_pokedex_set)
```

```
## True
```

<div class=""><p><strong>Within your IPython console</strong>, use <code>%timeit</code> to compare membership testing for <code>'Psyduck'</code> in <code>ash_pokedex</code>, <code>'Psyduck'</code> in <code>brock_pokedex_set</code>, <code>'Machop'</code> in <code>ash_pokedex</code>, and <code>'Machop'</code> in <code>brock_pokedex_set</code> (a total of <strong>four different timings</strong>).</p>
<p>Don't include the <code>print()</code> function. Only time the commands that you wrote <strong>inside</strong> the <code>print()</code> function in the previous steps. </p>
<p><strong>Which membership testing was faster?</strong></p></div>

- [ ] Using a list is faster than using a set for membership testing in all four cases.
- [ ] Member testing using a list and a set have the same runtimes for all four cases.
- [x] Member testing using a set is faster than using a list in all four cases.

<p class="">Awesome! Membership testing is much faster when you use sets. Did you notice that using a set for member testing is faster than using a list regardless if the item you are checking is in the set? Checking for 'Psyduck' (which was not in Brock's set) is still faster than checking for 'Psyduck' in Ash's list!</p>

### Gathering unique Pokémon


<div class>
<p>A sample of 500 Pokémon has been created <strong>with replacement</strong> (meaning a Pokémon could be selected more than once and duplicates exist within the sample).</p>
<p>Three lists have been loaded into your session:</p>
<ul>
<li>The <code>names</code> list contains the names of each Pokémon in the sample.</li>
<li>The <code>primary_types</code> list containing the corresponding <strong>primary</strong> type of each Pokémon in the sample.</li>
<li>The <code>generations</code> list contains the corresponding <strong>generation</strong> of each Pokémon in the sample.</li>
</ul>
<p>The below function was written to gather unique values from each list:</p>
<pre><code>def find_unique_items(data):
    uniques = []

    for item in data:
        if item not in uniques:
            uniques.append(item)

    return uniques
</code></pre>
<p>Let's compare the above function to using the <code>set</code> data type for collecting unique items.</p>
</div>

```python
# edited/added
from collections import Counter
names = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=425640626&single=true&output=csv", header = None).iloc[:,0].tolist()
primary_types = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=553528834&single=true&output=csv", header = None).iloc[:,0].tolist()
generations = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=800099022&single=true&output=csv", header = None).iloc[:,0].tolist()

def find_unique_items(data):
    uniques = []

    for item in data:
        if item not in uniques:
            uniques.append(item)

    return uniques
```
<li>Use the provided function to collect the unique Pokémon in the <code>names</code> list. Save this as <code>uniq_names_func</code>.</li>

```python
# Use the provided function to collect unique Pokémon names
uniq_names_func = find_unique_items(names)
print(len(uniq_names_func))
```

```
## 368
```
<li>Use a <code>set</code> data type to collect the unique Pokémon in the <code>names</code> list. Save this as <code>uniq_names_set</code>.</li>

```python
# Use find_unique_items() to collect unique Pokémon names
uniq_names_func = find_unique_items(names)
print(len(uniq_names_func))

# Convert the names list to a set to collect unique Pokémon names
```

```
## 368
```

```python
uniq_names_set = set(names)
print(len(uniq_names_set))

# Check that both unique collections are equivalent
```

```
## 368
```

```python
print(sorted(uniq_names_func) == sorted(uniq_names_set))
```

```
## True
```

<div class=""><p><strong>Within your IPython console</strong>, use <code>%timeit</code> to compare the <code>find_unique_items()</code> function with using a <code>set</code> data type to collect unique Pokémon character names in <code>names</code>.</p>
<p><strong>Which membership testing was faster?</strong></p></div>

- [x] Using a <code>set</code> to collect unique values is faster.
- [ ] Using the provided function that uses a loop to gather unique items is faster.
- [ ] Both approaches have the same runtime.

<li>Use the most efficient approach for gathering unique items to collect the unique Pokémon types (from the <code>primary_types</code> list) and Pokémon generations (from the <code>generations</code> list).</li>

```python
# Use find_unique_items() to collect unique Pokémon names
uniq_names_func = find_unique_items(names)
print(len(uniq_names_func))

# Convert the names list to a set to collect unique Pokémon names
```

```
## 368
```

```python
uniq_names_set = set(names)
print(len(uniq_names_set))

# Check that both unique collections are equivalent
```

```
## 368
```

```python
print(sorted(uniq_names_func) == sorted(uniq_names_set))

# Use the best approach to collect unique primary types and generations
```

```
## True
```

```python
uniq_types = set(primary_types) 
uniq_gens = set(generations)
print(uniq_types, uniq_gens, sep='\n') 
```

```
## {'Ice', 'Dark', 'Fire', 'Electric', 'Ghost', 'Poison', 'Fighting', 'Ground', 'Steel', 'Rock', 'Normal', 'Grass', 'Bug', 'Fairy', 'Water', 'Dragon', 'Psychic'}
## {1, 2, 3, 4, 5, 6}
```

<p class="">Nice work! Using a <code>set</code> data type to collect unique values is much faster than using a for loop (like in the <code>find_unique_items()</code> function). Since a set is defined as a collection of distinct elements, it is an efficient way to collect unique items from an existing object. Here you took advantage of a <code>set</code> to find the distinct Pokémon from the sample (eliminating duplicate Pokémon) and saw what unique Pokémon types and generations were included in the sample.</p>

## Eliminating loops



### Gathering Pokémon without a loop


<div class>
<p>A list containing 720 Pokémon has been loaded into your session as <code>poke_names</code>. Another list containing each Pokémon's corresponding generation has been loaded as <code>poke_gens</code>.</p>
<p>A for loop has been created to filter the Pokémon that belong to generation one or two, and collect the number of letters in each Pokémon's name:</p>
<pre><code>gen1_gen2_name_lengths_loop = []

for name,gen in zip(poke_names, poke_gens):
    if gen &lt; 3:
        name_length = len(name)
        poke_tuple = (name, name_length)
        gen1_gen2_name_lengths_loop.append(poke_tuple)
</code></pre>
</div>

```python
# edited/added
poke_names = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=728081830&single=true&output=csv", header = None).iloc[:,0].tolist()
poke_gens = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=1561338519&single=true&output=csv", header = None).iloc[:,0].tolist()
gen1_gen2_name_lengths_loop = []
```
<li>
<p>Eliminate the above for loop using list comprehension and the <code>map()</code> function:</p>
<ul>
<li>Use list comprehension to collect each Pokémon that belongs to generation 1 or generation 2. Save this as <code>gen1_gen2_pokemon</code>.</li>
<li>Use the <code>map()</code> function to collect the number of letters in each Pokémon's name within the <code>gen1_gen2_pokemon</code> list. Save this <em>map object</em> as <code>name_lengths_map</code>.</li>
<li>Combine <code>gen1_gen2_pokemon</code> and <code>name_length_map</code> into a list called <code>gen1_gen2_name_lengths</code>.</li>
</ul>
</li>

```python
# Collect Pokémon that belong to generation 1 or generation 2
gen1_gen2_pokemon = [name for name,gen in zip(poke_names, poke_gens) if gen < 3]

# Create a map object that stores the name lengths
name_lengths_map = map(len, gen1_gen2_pokemon)

# Combine gen1_gen2_pokemon and name_lengths_map into a list
gen1_gen2_name_lengths = [*zip(gen1_gen2_pokemon, name_lengths_map)]

print(gen1_gen2_name_lengths_loop[:5])
```

```
## []
```

```python
print(gen1_gen2_name_lengths[:5])
```

```
## [('Abra', 4), ('Aerodactyl', 10), ('Aipom', 5), ('Alakazam', 8), ('Ampharos', 8)]
```

<p class="">Great job! You successfully used list comprehension and the <code>map()</code> function to eliminate a for loop. If you compared runtimes between the for loop and using list comprehension with a <code>map()</code> function, you'd see that the for loop took quite a bit longer. <br> <br> If you're an experienced Pythonista, you may have noticed that you could replace the entire for loop with one list comprehension: <code>[(name, len(name)) for name,gen in zip(poke_names, poke_gens) if gen &lt; 3]</code></p>

### Pokémon totals and averages without a loop


<div class>
<p>A list of 720 Pokémon has been loaded into your session called <code>names</code>. Each Pokémon's corresponding statistics has been loaded as a NumPy array called <code>stats</code>. Each row of <code>stats</code> corresponds to a Pokémon in <code>names</code> and each column represents an individual Pokémon stat (<code>HP</code>, <code>Attack</code>, <code>Defense</code>, <code>Special Attack</code>, <code>Special Defense</code>, and <code>Speed</code> respectively.)</p>
<p>You want to gather each Pokémon's total stat value (i.e., the sum of each row in <code>stats</code>) and each Pokémon's average stat value (i.e., the mean of each row in <code>stats</code>) so that you find the strongest Pokémon.</p>
<p>The below for loop was written to collect these values:</p>
<pre><code>poke_list = []

for pokemon,row in zip(names, stats):
    total_stats = np.sum(row)
    avg_stats = np.mean(row)
    poke_list.append((pokemon, total_stats, avg_stats))
</code></pre>
</div>

```python
# edited/added
names = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=728081830&single=true&output=csv", header = None).iloc[:,0].tolist()
stats_df = pd.read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vSoeJegBxXU61LsAJQ4sPPrw99EJXBccEfiC3fhrj6TQCnhZ5Q4J8P7oCP-TtR1W6Z3d9TMcCYc32Xy/pub?gid=99951674&single=true&output=csv")
stats = stats_df.to_numpy()
poke_list = []

for pokemon,row in zip(names, stats):
    total_stats = np.sum(row)
    avg_stats = np.mean(row)
    poke_list.append((pokemon, total_stats, avg_stats))
```
<li>Replace the above for loop using NumPy:<ul>
<li>Create a total stats array (<code>total_stats_np</code>) using the <code>.sum()</code> method and specifying the correct axis.</li>
<li>Create an average stats array (<code>avg_stats_np</code>) using the <code>.mean()</code> method and specifying the correct axis.</li>
<li>Create a final output list (<code>poke_list_np</code>) by combining the <code>names</code> list, the <code>total_stats_np</code> array, and the <code>avg_stats_np</code> array.</li>
</ul>
</li>

```python
# Create a total stats array
total_stats_np = stats.sum(axis=1)

# Create an average stats array
avg_stats_np = stats.mean(axis=1)

# Combine names, total_stats_np, and avg_stats_np into a list
poke_list_np = [*zip(names, total_stats_np, avg_stats_np)]

print(poke_list_np == poke_list, '\n')
```

```
## True
```

```python
print(poke_list_np[:3])
```

```
## [('Abomasnow', 494, 82.33333333333333), ('Abra', 310, 51.666666666666664), ('Absol', 465, 77.5)]
```

```python
print(poke_list[:3], '\n')
```

```
## [('Abomasnow', 494, 82.33333333333333), ('Abra', 310, 51.666666666666664), ('Absol', 465, 77.5)]
```

```python
top_3 = sorted(poke_list_np, key=lambda x: x[1], reverse=True)[:3]
print('3 strongest Pokémon:\n{}'.format(top_3))
```

```
## 3 strongest Pokémon:
## [('GroudonPrimal Groudon', 770, 128.33333333333334), ('KyogrePrimal Kyogre', 770, 128.33333333333334), ('KyuremBlack Kyurem', 700, 116.66666666666667)]
```

<p class="">Great work! You used NumPy's <code>.sum()</code> and <code>.mean()</code> methods with a specific axis to eliminate a for loop. With this approach, you were able to quickly see that 'GroudonPrimal Groudon', 'KyogrePrimal Kyogre', and 'Arceus' were the strongest Pokémon in your list based on total stats. <br><br> If you were to gather run times, the for loop would have taken <em>milliseconds</em> to execute while the NumPy approach would have taken <em>microseconds</em> to execute. This is quite an improvement!</p>

## Writing better loops



### One-time calculation loop


<div class>
<p>A list of integers that represents each Pokémon's generation has been loaded into your session called <code>generations</code>. You'd like to gather the counts of each generation and determine what percentage each generation accounts for out of the total count of integers.</p>
<p>The below loop was written to accomplish this task:</p>
<pre><code>for gen,count in gen_counts.items():
    total_count = len(generations)
    gen_percent = round(count / total_count * 100, 2)
    print(
      'generation {}: count = {:3} percentage = {}'
      .format(gen, count, gen_percent)
    )
</code></pre>
<p>Let's make this loop more efficient by moving a one-time calculation outside the loop.</p>
</div>

```python
# edited/added
```
<li>Import <code>Counter</code> from the <code>collections</code> module.</li>
<li>Use <code>Counter()</code> to collect the count of each generation from the <code>generations</code> list. Save this as <code>gen_counts</code>.</li>
<li>Write a better for loop that places a <strong>one-time</strong> calculation outside (above) the loop. Use the exact same syntax as the original for loop (simply copy and paste the one-time calculation above the loop).</li>

```python
# Import Counter
from collections import Counter

# Collect the count of each generation
gen_counts = Counter(generations)

# Improve for loop by moving one calculation above the loop
total_count = len(generations)

for gen,count in gen_counts.items():
    gen_percent = round(count / total_count * 100, 2)
    print('generation {}: count = {:3} percentage = {}'
          .format(gen, count, gen_percent))
```

```
## generation 2: count =  69 percentage = 13.8
## generation 4: count =  84 percentage = 16.8
## generation 3: count = 107 percentage = 21.4
## generation 5: count =  95 percentage = 19.0
## generation 1: count =  96 percentage = 19.2
## generation 6: count =  49 percentage = 9.8
```

<p class="">Well done! You spotted a calculation that could be moved outside a loop to make the loop more efficient. Since the total count is now calculated just once (and not with each loop iteration), you can expect to see an efficiency gain with your new loop. When writing a loop is unavoidable, be sure to analyze the loop and move any one-time calculations outside.</p>

### Holistic conversion loop


<div class>
<p>A list of all possible Pokémon types has been loaded into your session as <code>pokemon_types</code>. It's been printed in the console for convenience.</p>
<p>You'd like to gather all the possible pairs of Pokémon types. You want to store each of these pairs in an individual list with an enumerated index as the first element of each list. This allows you to see the total number of possible pairs and provides an indexed label for each pair.</p>
<p>The below loop was written to accomplish this task:</p>
<pre><code>enumerated_pairs = []

for i,pair in enumerate(possible_pairs, 1):
    enumerated_pair_tuple = (i,) + pair
    enumerated_pair_list = list(enumerated_pair_tuple)
    enumerated_pairs.append(enumerated_pair_list)
</code></pre>
<p>Let's make this loop more efficient using a holistic conversion.</p>
</div>

```python
# edited/added
pokemon_types = ['Bug', 'Dark', 'Dragon', 'Electric', 'Fairy', 'Fighting', 'Fire', 'Flying', 'Ghost', 'Grass', 'Ground', 'Ice', 'Normal', 'Poison', 'Psychic', 'Rock', 'Steel', 'Water']
```
<li>
<code>combinations</code> from the <code>itertools</code> module has been loaded into your session. Use it to create a list called <code>possible_pairs</code> that contains all possible pairs of Pokémon types (each pair has <code>2</code> Pokémon types).</li>
<li>Create an empty list called <code>enumerated_tuples</code> above the for loop.</li>
<li>Within the for loop, append each <code>enumerated_pair_tuple</code> to the empty list you created in the above step. </li>
<li>Use a built-in function to convert each tuple in <code>enumerated_tuples</code> to a list.</li>

```python
# Collect all possible pairs using combinations()
possible_pairs = [*combinations(pokemon_types, 2)]

# Create an empty list called enumerated_tuples
enumerated_tuples = []

# Append each enumerated_pair_tuple to the empty list above
for i,pair in enumerate(possible_pairs, 1):
    enumerated_pair_tuple = (i,) + pair
    enumerated_tuples.append(enumerated_pair_tuple)

# Convert all tuples in enumerated_tuples to a list
enumerated_pairs = [*map(list, enumerated_tuples)]
print(enumerated_pairs)
```

```
## [[1, 'Bug', 'Dark'], [2, 'Bug', 'Dragon'], [3, 'Bug', 'Electric'], [4, 'Bug', 'Fairy'], [5, 'Bug', 'Fighting'], [6, 'Bug', 'Fire'], [7, 'Bug', 'Flying'], [8, 'Bug', 'Ghost'], [9, 'Bug', 'Grass'], [10, 'Bug', 'Ground'], [11, 'Bug', 'Ice'], [12, 'Bug', 'Normal'], [13, 'Bug', 'Poison'], [14, 'Bug', 'Psychic'], [15, 'Bug', 'Rock'], [16, 'Bug', 'Steel'], [17, 'Bug', 'Water'], [18, 'Dark', 'Dragon'], [19, 'Dark', 'Electric'], [20, 'Dark', 'Fairy'], [21, 'Dark', 'Fighting'], [22, 'Dark', 'Fire'], [23, 'Dark', 'Flying'], [24, 'Dark', 'Ghost'], [25, 'Dark', 'Grass'], [26, 'Dark', 'Ground'], [27, 'Dark', 'Ice'], [28, 'Dark', 'Normal'], [29, 'Dark', 'Poison'], [30, 'Dark', 'Psychic'], [31, 'Dark', 'Rock'], [32, 'Dark', 'Steel'], [33, 'Dark', 'Water'], [34, 'Dragon', 'Electric'], [35, 'Dragon', 'Fairy'], [36, 'Dragon', 'Fighting'], [37, 'Dragon', 'Fire'], [38, 'Dragon', 'Flying'], [39, 'Dragon', 'Ghost'], [40, 'Dragon', 'Grass'], [41, 'Dragon', 'Ground'], [42, 'Dragon', 'Ice'], [43, 'Dragon', 'Normal'], [44, 'Dragon', 'Poison'], [45, 'Dragon', 'Psychic'], [46, 'Dragon', 'Rock'], [47, 'Dragon', 'Steel'], [48, 'Dragon', 'Water'], [49, 'Electric', 'Fairy'], [50, 'Electric', 'Fighting'], [51, 'Electric', 'Fire'], [52, 'Electric', 'Flying'], [53, 'Electric', 'Ghost'], [54, 'Electric', 'Grass'], [55, 'Electric', 'Ground'], [56, 'Electric', 'Ice'], [57, 'Electric', 'Normal'], [58, 'Electric', 'Poison'], [59, 'Electric', 'Psychic'], [60, 'Electric', 'Rock'], [61, 'Electric', 'Steel'], [62, 'Electric', 'Water'], [63, 'Fairy', 'Fighting'], [64, 'Fairy', 'Fire'], [65, 'Fairy', 'Flying'], [66, 'Fairy', 'Ghost'], [67, 'Fairy', 'Grass'], [68, 'Fairy', 'Ground'], [69, 'Fairy', 'Ice'], [70, 'Fairy', 'Normal'], [71, 'Fairy', 'Poison'], [72, 'Fairy', 'Psychic'], [73, 'Fairy', 'Rock'], [74, 'Fairy', 'Steel'], [75, 'Fairy', 'Water'], [76, 'Fighting', 'Fire'], [77, 'Fighting', 'Flying'], [78, 'Fighting', 'Ghost'], [79, 'Fighting', 'Grass'], [80, 'Fighting', 'Ground'], [81, 'Fighting', 'Ice'], [82, 'Fighting', 'Normal'], [83, 'Fighting', 'Poison'], [84, 'Fighting', 'Psychic'], [85, 'Fighting', 'Rock'], [86, 'Fighting', 'Steel'], [87, 'Fighting', 'Water'], [88, 'Fire', 'Flying'], [89, 'Fire', 'Ghost'], [90, 'Fire', 'Grass'], [91, 'Fire', 'Ground'], [92, 'Fire', 'Ice'], [93, 'Fire', 'Normal'], [94, 'Fire', 'Poison'], [95, 'Fire', 'Psychic'], [96, 'Fire', 'Rock'], [97, 'Fire', 'Steel'], [98, 'Fire', 'Water'], [99, 'Flying', 'Ghost'], [100, 'Flying', 'Grass'], [101, 'Flying', 'Ground'], [102, 'Flying', 'Ice'], [103, 'Flying', 'Normal'], [104, 'Flying', 'Poison'], [105, 'Flying', 'Psychic'], [106, 'Flying', 'Rock'], [107, 'Flying', 'Steel'], [108, 'Flying', 'Water'], [109, 'Ghost', 'Grass'], [110, 'Ghost', 'Ground'], [111, 'Ghost', 'Ice'], [112, 'Ghost', 'Normal'], [113, 'Ghost', 'Poison'], [114, 'Ghost', 'Psychic'], [115, 'Ghost', 'Rock'], [116, 'Ghost', 'Steel'], [117, 'Ghost', 'Water'], [118, 'Grass', 'Ground'], [119, 'Grass', 'Ice'], [120, 'Grass', 'Normal'], [121, 'Grass', 'Poison'], [122, 'Grass', 'Psychic'], [123, 'Grass', 'Rock'], [124, 'Grass', 'Steel'], [125, 'Grass', 'Water'], [126, 'Ground', 'Ice'], [127, 'Ground', 'Normal'], [128, 'Ground', 'Poison'], [129, 'Ground', 'Psychic'], [130, 'Ground', 'Rock'], [131, 'Ground', 'Steel'], [132, 'Ground', 'Water'], [133, 'Ice', 'Normal'], [134, 'Ice', 'Poison'], [135, 'Ice', 'Psychic'], [136, 'Ice', 'Rock'], [137, 'Ice', 'Steel'], [138, 'Ice', 'Water'], [139, 'Normal', 'Poison'], [140, 'Normal', 'Psychic'], [141, 'Normal', 'Rock'], [142, 'Normal', 'Steel'], [143, 'Normal', 'Water'], [144, 'Poison', 'Psychic'], [145, 'Poison', 'Rock'], [146, 'Poison', 'Steel'], [147, 'Poison', 'Water'], [148, 'Psychic', 'Rock'], [149, 'Psychic', 'Steel'], [150, 'Psychic', 'Water'], [151, 'Rock', 'Steel'], [152, 'Rock', 'Water'], [153, 'Steel', 'Water']]
```

<p class="">Great job! Rather than converting each tuple to a list <em>within</em> the loop, you used the <code>map()</code> function to convert tuples to lists all at once outside of a loop. You're getting the hang of writing efficient loops! Remember, you want to avoid looping as much as possible when writing Python code. In cases where looping is unavoidable, be sure to check your loops for one-time calculations and holistic conversions to make them more efficient.</p>

### Bringing it all together: Pokémon z-scores


<div class>
<p>A list of 720 Pokémon has been loaded into your session as <code>names</code>. Each Pokémon's corresponding Health Points is stored in a NumPy array called <code>hps</code>. You want to analyze the Health Points using the <a href="https://en.wikipedia.org/wiki/Standard_score">z-score</a> to see how many standard deviations each Pokémon's HP is from the mean of all HPs.</p>
<p>The below code was written to calculate the HP z-score for each Pokémon and gather the Pokémon with the highest HPs based on their z-scores:</p>
<pre><code>poke_zscores = []

for name,hp in zip(names, hps):
    hp_avg = hps.mean()
    hp_std = hps.std()
    z_score = (hp - hp_avg)/hp_std
    poke_zscores.append((name, hp, z_score))
</code></pre>
<pre><code>highest_hp_pokemon = []

for name,hp,zscore in poke_zscores:
    if zscore &gt; 2:
        highest_hp_pokemon.append((name, hp, zscore))
</code></pre>
</div>

```python
# edited/added
hps = stats_df.HP.values
len(hps)
```

```
## 720
```
<li>Use NumPy to eliminate the for loop used to create the z-scores.</li>
<li>Then, combine the <code>names</code>, <code>hps</code>, and <code>z_scores</code> objects together into a list called <code>poke_zscores2</code>.</li>

```python
# Calculate the total HP avg and total HP standard deviation
hp_avg = hps.mean()
hp_std = hps.std()

# Use NumPy to eliminate the previous for loop
z_scores = (hps - hp_avg)/hp_std

# Combine names, hps, and z_scores
poke_zscores2 = [*zip(names, hps, z_scores)]
print(*poke_zscores2[:3], sep='\n')
```

```
## ('Abomasnow', 90, 0.8432264096861816)
## ('Abra', 25, -1.673706811393817)
## ('Absol', 65, -0.12482482919074096)
```
<li>Use list comprehension to replace the for loop used to collect Pokémon with the highest HPs based on their z-score.</li>

```python
# Calculate the total HP avg and total HP standard deviation
hp_avg = hps.mean()
hp_std = hps.std()

# Use NumPy to eliminate the previous for loop
z_scores = (hps - hp_avg)/hp_std

# Combine names, hps, and z_scores
poke_zscores2 = [*zip(names, hps, z_scores)]
print(*poke_zscores2[:3], sep='\n')

# Use list comprehension with the same logic as the highest_hp_pokemon code block
```

```
## ('Abomasnow', 90, 0.8432264096861816)
## ('Abra', 25, -1.673706811393817)
## ('Absol', 65, -0.12482482919074096)
```

```python
highest_hp_pokemon2 = [(name, hp, zscore) for name,hp,zscore in poke_zscores2 if zscore > 2]
print(*highest_hp_pokemon2, sep='\n')
```

```
## ('Alomomola', 165, 3.747380126316949)
## ('Arceus', 120, 2.0048878963384884)
## ('Aurorus', 123, 2.1210540450037194)
## ('Blissey', 255, 7.232364586273871)
## ('Chansey', 250, 7.038754338498486)
## ('Cresselia', 120, 2.0048878963384884)
## ('Drifblim', 150, 3.166549382990796)
## ('Gogoat', 123, 2.1210540450037194)
## ('Hariyama', 144, 2.9342170856603342)
## ('Kyurem', 125, 2.198498144113873)
## ('KyuremBlack Kyurem', 125, 2.198498144113873)
## ('KyuremWhite Kyurem', 125, 2.198498144113873)
## ('Lanturn', 125, 2.198498144113873)
## ('Lapras', 130, 2.3921083918892574)
## ('Munchlax', 135, 2.585718639664642)
## ('Slaking', 150, 3.166549382990796)
## ('Snorlax', 160, 3.553769878541565)
## ('Throh', 120, 2.0048878963384884)
## ('Vaporeon', 130, 2.3921083918892574)
## ('Wailmer', 130, 2.3921083918892574)
## ('Wailord', 170, 3.9409903740923338)
## ('Wigglytuff', 140, 2.7793288874400264)
## ('Wobbuffet', 190, 4.715431365193871)
## ('Xerneas', 126, 2.23722019366895)
## ('Yveltal', 126, 2.23722019366895)
```

<div class=""><p>Use <code>%%timeit</code> (<em>cell magic mode</em>) <strong>within your IPython console</strong> to compare the runtimes between the original code blocks and the new code you developed using NumPy and list comprehension.</p>
<p><strong>Don't include the <code>print()</code> statements when timing.</strong> You should include <strong>ten lines of code</strong> when timing the original code blocks and <strong>five lines of code</strong> when timing the new code you developed. You may need to press <code>SHIFT+ENTER</code> after entering <code>%%timeit</code> to get to a new line within your IPython console.</p>
<p><strong>Which approach was the faster?</strong></p></div>

- [ ] The total time for executing both of the original code blocks was faster.
- [x] The total time for executing the updated solution using NumPy and list comprehension was faster.
- [ ] Both approaches had the same execution time.

<p class="">Great job! You're Catching 'Em All (efficiencies that is). You eliminated two loops using NumPy broadcasting and list comprehension. Did you notice how much faster the approach you developed was compared to the original loops? What a great improvement! <br><br> Remember the techniques you've learned throughout this chapter as you continue writing Python code outside this course. Keep in mind the built-in functions and modules you covered to eliminate loops and remember to check your unavoidable loops for things that can be moved outside.</p>

# Basic pandas optimizations

<p class="">This chapter offers a brief introduction on how to efficiently work with pandas DataFrames. You'll learn the various options you have for iterating over a DataFrame. Then, you'll learn how to efficiently apply functions to data stored in a DataFrame.</p>

## Intro to pandas DataFrame iteration



### Iterating with .iterrows()


<div class>
<p>In the video, we discussed that <code>.iterrows()</code> returns each DataFrame row as a tuple of (index, <code>pandas</code> Series) pairs. But, what does this mean? Let's explore with a few coding exercises.</p>
<p>A <code>pandas</code> DataFrame has been loaded into your session called <code>pit_df</code>. This DataFrame contains the stats for the Major League Baseball team named the Pittsburgh Pirates (abbreviated as <code>'PIT'</code>) from the year 2008 to the year 2012. It has been printed into your console for convenience.</p>
</div>
<div class="exercise--instructions__content"><p>Use <code>.iterrows()</code> to loop over <code>pit_df</code> and print each row. Save the first item from <code>.iterrows()</code> as <code>i</code> and the second as <code>row</code>.</p></div>

```python
# edited/added
baseball_df = pd.read_csv("https://assets.datacamp.com/production/repositories/3581/datasets/779033fb8fb5021aee9ff46253980abcbc5851f3/baseball_stats.csv")
pit_df = baseball_df[baseball_df.Team == 'PIT']

# Iterate over pit_df and print each row
for i,row in pit_df.iterrows():
    print(row)
```

```
## Team              PIT
## League             NL
## Year             2012
## RS                651
## RA                674
## W                  79
## OBP             0.304
## SLG             0.395
## BA              0.243
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.314
## OSLG             0.39
## Name: 21, dtype: object
## Team              PIT
## League             NL
## Year             2011
## RS                610
## RA                712
## W                  72
## OBP             0.309
## SLG             0.368
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.338
## OSLG            0.409
## Name: 51, dtype: object
## Team              PIT
## League             NL
## Year             2010
## RS                587
## RA                866
## W                  57
## OBP             0.304
## SLG             0.373
## BA              0.242
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.348
## OSLG            0.449
## Name: 81, dtype: object
## Team              PIT
## League             NL
## Year             2009
## RS                636
## RA                768
## W                  62
## OBP             0.318
## SLG             0.387
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.346
## OSLG            0.442
## Name: 111, dtype: object
## Team              PIT
## League             NL
## Year             2008
## RS                735
## RA                884
## W                  67
## OBP              0.32
## SLG             0.403
## BA              0.258
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.362
## OSLG            0.454
## Name: 141, dtype: object
## Team              PIT
## League             NL
## Year             2007
## RS                724
## RA                846
## W                  68
## OBP             0.325
## SLG             0.411
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.352
## OSLG            0.447
## Name: 171, dtype: object
## Team              PIT
## League             NL
## Year             2006
## RS                691
## RA                797
## W                  67
## OBP             0.327
## SLG             0.397
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.357
## OSLG            0.431
## Name: 201, dtype: object
## Team              PIT
## League             NL
## Year             2005
## RS                680
## RA                769
## W                  67
## OBP             0.322
## SLG               0.4
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.424
## Name: 231, dtype: object
## Team              PIT
## League             NL
## Year             2004
## RS                680
## RA                744
## W                  72
## OBP             0.321
## SLG             0.401
## BA               0.26
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.416
## Name: 262, dtype: object
## Team              PIT
## League             NL
## Year             2003
## RS                753
## RA                801
## W                  75
## OBP             0.338
## SLG              0.42
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.336
## OSLG            0.431
## Name: 292, dtype: object
## Team              PIT
## League             NL
## Year             2002
## RS                641
## RA                730
## W                  72
## OBP             0.319
## SLG             0.381
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.423
## Name: 322, dtype: object
## Team              PIT
## League             NL
## Year             2001
## RS                657
## RA                858
## W                  62
## OBP             0.313
## SLG             0.393
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.433
## Name: 352, dtype: object
## Team              PIT
## League             NL
## Year             2000
## RS                793
## RA                888
## W                  69
## OBP             0.339
## SLG             0.424
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.361
## OSLG            0.432
## Name: 382, dtype: object
## Team              PIT
## League             NL
## Year             1999
## RS                775
## RA                782
## W                  78
## OBP             0.334
## SLG             0.419
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.343
## OSLG             0.42
## Name: 412, dtype: object
## Team              PIT
## League             NL
## Year             1998
## RS                650
## RA                718
## W                  69
## OBP             0.311
## SLG             0.374
## BA              0.254
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 442, dtype: object
## Team              PIT
## League             NL
## Year             1997
## RS                725
## RA                760
## W                  79
## OBP             0.329
## SLG             0.404
## BA              0.262
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 471, dtype: object
## Team              PIT
## League             NL
## Year             1996
## RS                776
## RA                833
## W                  73
## OBP             0.329
## SLG             0.407
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 499, dtype: object
## Team              PIT
## League             NL
## Year             1993
## RS                707
## RA                806
## W                  75
## OBP             0.335
## SLG             0.393
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 527, dtype: object
## Team              PIT
## League             NL
## Year             1992
## RS                693
## RA                595
## W                  96
## OBP             0.324
## SLG             0.381
## BA              0.255
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 553, dtype: object
## Team              PIT
## League             NL
## Year             1991
## RS                768
## RA                632
## W                  98
## OBP             0.338
## SLG             0.398
## BA              0.263
## Playoffs            1
## RankSeason        1.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 579, dtype: object
## Team              PIT
## League             NL
## Year             1990
## RS                733
## RA                619
## W                  95
## OBP              0.33
## SLG             0.405
## BA              0.259
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 605, dtype: object
## Team              PIT
## League             NL
## Year             1989
## RS                637
## RA                680
## W                  74
## OBP             0.311
## SLG             0.359
## BA              0.241
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 164
## OOBP              NaN
## OSLG              NaN
## Name: 631, dtype: object
## Team              PIT
## League             NL
## Year             1988
## RS                651
## RA                616
## W                  85
## OBP             0.317
## SLG             0.369
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 160
## OOBP              NaN
## OSLG              NaN
## Name: 657, dtype: object
## Team              PIT
## League             NL
## Year             1987
## RS                723
## RA                744
## W                  80
## OBP              0.33
## SLG             0.403
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 683, dtype: object
## Team              PIT
## League             NL
## Year             1986
## RS                663
## RA                700
## W                  64
## OBP             0.321
## SLG             0.374
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 709, dtype: object
## Team              PIT
## League             NL
## Year             1985
## RS                568
## RA                708
## W                  57
## OBP             0.311
## SLG             0.347
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 735, dtype: object
## Team              PIT
## League             NL
## Year             1984
## RS                615
## RA                567
## W                  75
## OBP              0.31
## SLG             0.363
## BA              0.255
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 761, dtype: object
## Team              PIT
## League             NL
## Year             1983
## RS                659
## RA                648
## W                  84
## OBP             0.325
## SLG             0.383
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 787, dtype: object
## Team              PIT
## League             NL
## Year             1982
## RS                724
## RA                696
## W                  84
## OBP             0.327
## SLG             0.408
## BA              0.273
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 813, dtype: object
## Team              PIT
## League             NL
## Year             1980
## RS                666
## RA                646
## W                  83
## OBP             0.322
## SLG             0.388
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 839, dtype: object
## Team              PIT
## League             NL
## Year             1979
## RS                775
## RA                643
## W                  98
## OBP              0.33
## SLG             0.416
## BA              0.272
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 865, dtype: object
## Team              PIT
## League             NL
## Year             1978
## RS                684
## RA                637
## W                  88
## OBP              0.32
## SLG             0.385
## BA              0.257
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 891, dtype: object
## Team              PIT
## League             NL
## Year             1977
## RS                734
## RA                665
## W                  96
## OBP             0.331
## SLG             0.413
## BA              0.274
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 917, dtype: object
## Team              PIT
## League             NL
## Year             1976
## RS                708
## RA                630
## W                  92
## OBP             0.321
## SLG             0.391
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 943, dtype: object
## Team              PIT
## League             NL
## Year             1975
## RS                712
## RA                565
## W                  92
## OBP             0.323
## SLG             0.402
## BA              0.263
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 967, dtype: object
## Team              PIT
## League             NL
## Year             1974
## RS                751
## RA                657
## W                  88
## OBP             0.335
## SLG             0.391
## BA              0.274
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 991, dtype: object
## Team              PIT
## League             NL
## Year             1973
## RS                704
## RA                693
## W                  80
## OBP             0.315
## SLG             0.405
## BA              0.261
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1015, dtype: object
## Team              PIT
## League             NL
## Year             1971
## RS                788
## RA                599
## W                  97
## OBP              0.33
## SLG             0.416
## BA              0.274
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1039, dtype: object
## Team              PIT
## League             NL
## Year             1970
## RS                729
## RA                664
## W                  89
## OBP             0.325
## SLG             0.406
## BA               0.27
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1063, dtype: object
## Team              PIT
## League             NL
## Year             1969
## RS                725
## RA                652
## W                  88
## OBP             0.334
## SLG             0.398
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1086, dtype: object
## Team              PIT
## League             NL
## Year             1968
## RS                583
## RA                532
## W                  80
## OBP             0.306
## SLG             0.343
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1108, dtype: object
## Team              PIT
## League             NL
## Year             1967
## RS                679
## RA                693
## W                  81
## OBP             0.324
## SLG              0.38
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1128, dtype: object
## Team              PIT
## League             NL
## Year             1966
## RS                759
## RA                641
## W                  92
## OBP             0.329
## SLG             0.428
## BA              0.279
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1148, dtype: object
## Team              PIT
## League             NL
## Year             1965
## RS                675
## RA                580
## W                  90
## OBP             0.317
## SLG             0.382
## BA              0.265
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1168, dtype: object
## Team              PIT
## League             NL
## Year             1964
## RS                663
## RA                636
## W                  80
## OBP             0.315
## SLG             0.389
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1188, dtype: object
## Team              PIT
## League             NL
## Year             1963
## RS                567
## RA                595
## W                  74
## OBP             0.309
## SLG             0.359
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1208, dtype: object
## Team              PIT
## League             NL
## Year             1962
## RS                706
## RA                626
## W                  93
## OBP             0.321
## SLG             0.394
## BA              0.268
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 1228, dtype: object
```

<div class="exercise--instructions__content"><p>Add <strong>two</strong> lines to the loop: one <em>before</em> <code>print(row)</code> to print each index variable and one <em>after</em> to print each row's type.</p></div>

```python
# Iterate over pit_df and print each index variable, row, and row type
for i,row in pit_df.iterrows():
    print(i)
    print(row)
    print(type(row))
```

```
## 21
## Team              PIT
## League             NL
## Year             2012
## RS                651
## RA                674
## W                  79
## OBP             0.304
## SLG             0.395
## BA              0.243
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.314
## OSLG             0.39
## Name: 21, dtype: object
## <class 'pandas.core.series.Series'>
## 51
## Team              PIT
## League             NL
## Year             2011
## RS                610
## RA                712
## W                  72
## OBP             0.309
## SLG             0.368
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.338
## OSLG            0.409
## Name: 51, dtype: object
## <class 'pandas.core.series.Series'>
## 81
## Team              PIT
## League             NL
## Year             2010
## RS                587
## RA                866
## W                  57
## OBP             0.304
## SLG             0.373
## BA              0.242
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.348
## OSLG            0.449
## Name: 81, dtype: object
## <class 'pandas.core.series.Series'>
## 111
## Team              PIT
## League             NL
## Year             2009
## RS                636
## RA                768
## W                  62
## OBP             0.318
## SLG             0.387
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.346
## OSLG            0.442
## Name: 111, dtype: object
## <class 'pandas.core.series.Series'>
## 141
## Team              PIT
## League             NL
## Year             2008
## RS                735
## RA                884
## W                  67
## OBP              0.32
## SLG             0.403
## BA              0.258
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.362
## OSLG            0.454
## Name: 141, dtype: object
## <class 'pandas.core.series.Series'>
## 171
## Team              PIT
## League             NL
## Year             2007
## RS                724
## RA                846
## W                  68
## OBP             0.325
## SLG             0.411
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.352
## OSLG            0.447
## Name: 171, dtype: object
## <class 'pandas.core.series.Series'>
## 201
## Team              PIT
## League             NL
## Year             2006
## RS                691
## RA                797
## W                  67
## OBP             0.327
## SLG             0.397
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.357
## OSLG            0.431
## Name: 201, dtype: object
## <class 'pandas.core.series.Series'>
## 231
## Team              PIT
## League             NL
## Year             2005
## RS                680
## RA                769
## W                  67
## OBP             0.322
## SLG               0.4
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.424
## Name: 231, dtype: object
## <class 'pandas.core.series.Series'>
## 262
## Team              PIT
## League             NL
## Year             2004
## RS                680
## RA                744
## W                  72
## OBP             0.321
## SLG             0.401
## BA               0.26
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.416
## Name: 262, dtype: object
## <class 'pandas.core.series.Series'>
## 292
## Team              PIT
## League             NL
## Year             2003
## RS                753
## RA                801
## W                  75
## OBP             0.338
## SLG              0.42
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.336
## OSLG            0.431
## Name: 292, dtype: object
## <class 'pandas.core.series.Series'>
## 322
## Team              PIT
## League             NL
## Year             2002
## RS                641
## RA                730
## W                  72
## OBP             0.319
## SLG             0.381
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.423
## Name: 322, dtype: object
## <class 'pandas.core.series.Series'>
## 352
## Team              PIT
## League             NL
## Year             2001
## RS                657
## RA                858
## W                  62
## OBP             0.313
## SLG             0.393
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.433
## Name: 352, dtype: object
## <class 'pandas.core.series.Series'>
## 382
## Team              PIT
## League             NL
## Year             2000
## RS                793
## RA                888
## W                  69
## OBP             0.339
## SLG             0.424
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.361
## OSLG            0.432
## Name: 382, dtype: object
## <class 'pandas.core.series.Series'>
## 412
## Team              PIT
## League             NL
## Year             1999
## RS                775
## RA                782
## W                  78
## OBP             0.334
## SLG             0.419
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.343
## OSLG             0.42
## Name: 412, dtype: object
## <class 'pandas.core.series.Series'>
## 442
## Team              PIT
## League             NL
## Year             1998
## RS                650
## RA                718
## W                  69
## OBP             0.311
## SLG             0.374
## BA              0.254
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 442, dtype: object
## <class 'pandas.core.series.Series'>
## 471
## Team              PIT
## League             NL
## Year             1997
## RS                725
## RA                760
## W                  79
## OBP             0.329
## SLG             0.404
## BA              0.262
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 471, dtype: object
## <class 'pandas.core.series.Series'>
## 499
## Team              PIT
## League             NL
## Year             1996
## RS                776
## RA                833
## W                  73
## OBP             0.329
## SLG             0.407
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 499, dtype: object
## <class 'pandas.core.series.Series'>
## 527
## Team              PIT
## League             NL
## Year             1993
## RS                707
## RA                806
## W                  75
## OBP             0.335
## SLG             0.393
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 527, dtype: object
## <class 'pandas.core.series.Series'>
## 553
## Team              PIT
## League             NL
## Year             1992
## RS                693
## RA                595
## W                  96
## OBP             0.324
## SLG             0.381
## BA              0.255
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 553, dtype: object
## <class 'pandas.core.series.Series'>
## 579
## Team              PIT
## League             NL
## Year             1991
## RS                768
## RA                632
## W                  98
## OBP             0.338
## SLG             0.398
## BA              0.263
## Playoffs            1
## RankSeason        1.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 579, dtype: object
## <class 'pandas.core.series.Series'>
## 605
## Team              PIT
## League             NL
## Year             1990
## RS                733
## RA                619
## W                  95
## OBP              0.33
## SLG             0.405
## BA              0.259
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 605, dtype: object
## <class 'pandas.core.series.Series'>
## 631
## Team              PIT
## League             NL
## Year             1989
## RS                637
## RA                680
## W                  74
## OBP             0.311
## SLG             0.359
## BA              0.241
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 164
## OOBP              NaN
## OSLG              NaN
## Name: 631, dtype: object
## <class 'pandas.core.series.Series'>
## 657
## Team              PIT
## League             NL
## Year             1988
## RS                651
## RA                616
## W                  85
## OBP             0.317
## SLG             0.369
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 160
## OOBP              NaN
## OSLG              NaN
## Name: 657, dtype: object
## <class 'pandas.core.series.Series'>
## 683
## Team              PIT
## League             NL
## Year             1987
## RS                723
## RA                744
## W                  80
## OBP              0.33
## SLG             0.403
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 683, dtype: object
## <class 'pandas.core.series.Series'>
## 709
## Team              PIT
## League             NL
## Year             1986
## RS                663
## RA                700
## W                  64
## OBP             0.321
## SLG             0.374
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 709, dtype: object
## <class 'pandas.core.series.Series'>
## 735
## Team              PIT
## League             NL
## Year             1985
## RS                568
## RA                708
## W                  57
## OBP             0.311
## SLG             0.347
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 735, dtype: object
## <class 'pandas.core.series.Series'>
## 761
## Team              PIT
## League             NL
## Year             1984
## RS                615
## RA                567
## W                  75
## OBP              0.31
## SLG             0.363
## BA              0.255
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 761, dtype: object
## <class 'pandas.core.series.Series'>
## 787
## Team              PIT
## League             NL
## Year             1983
## RS                659
## RA                648
## W                  84
## OBP             0.325
## SLG             0.383
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 787, dtype: object
## <class 'pandas.core.series.Series'>
## 813
## Team              PIT
## League             NL
## Year             1982
## RS                724
## RA                696
## W                  84
## OBP             0.327
## SLG             0.408
## BA              0.273
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 813, dtype: object
## <class 'pandas.core.series.Series'>
## 839
## Team              PIT
## League             NL
## Year             1980
## RS                666
## RA                646
## W                  83
## OBP             0.322
## SLG             0.388
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 839, dtype: object
## <class 'pandas.core.series.Series'>
## 865
## Team              PIT
## League             NL
## Year             1979
## RS                775
## RA                643
## W                  98
## OBP              0.33
## SLG             0.416
## BA              0.272
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 865, dtype: object
## <class 'pandas.core.series.Series'>
## 891
## Team              PIT
## League             NL
## Year             1978
## RS                684
## RA                637
## W                  88
## OBP              0.32
## SLG             0.385
## BA              0.257
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 891, dtype: object
## <class 'pandas.core.series.Series'>
## 917
## Team              PIT
## League             NL
## Year             1977
## RS                734
## RA                665
## W                  96
## OBP             0.331
## SLG             0.413
## BA              0.274
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 917, dtype: object
## <class 'pandas.core.series.Series'>
## 943
## Team              PIT
## League             NL
## Year             1976
## RS                708
## RA                630
## W                  92
## OBP             0.321
## SLG             0.391
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 943, dtype: object
## <class 'pandas.core.series.Series'>
## 967
## Team              PIT
## League             NL
## Year             1975
## RS                712
## RA                565
## W                  92
## OBP             0.323
## SLG             0.402
## BA              0.263
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 967, dtype: object
## <class 'pandas.core.series.Series'>
## 991
## Team              PIT
## League             NL
## Year             1974
## RS                751
## RA                657
## W                  88
## OBP             0.335
## SLG             0.391
## BA              0.274
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 991, dtype: object
## <class 'pandas.core.series.Series'>
## 1015
## Team              PIT
## League             NL
## Year             1973
## RS                704
## RA                693
## W                  80
## OBP             0.315
## SLG             0.405
## BA              0.261
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1015, dtype: object
## <class 'pandas.core.series.Series'>
## 1039
## Team              PIT
## League             NL
## Year             1971
## RS                788
## RA                599
## W                  97
## OBP              0.33
## SLG             0.416
## BA              0.274
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1039, dtype: object
## <class 'pandas.core.series.Series'>
## 1063
## Team              PIT
## League             NL
## Year             1970
## RS                729
## RA                664
## W                  89
## OBP             0.325
## SLG             0.406
## BA               0.27
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1063, dtype: object
## <class 'pandas.core.series.Series'>
## 1086
## Team              PIT
## League             NL
## Year             1969
## RS                725
## RA                652
## W                  88
## OBP             0.334
## SLG             0.398
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1086, dtype: object
## <class 'pandas.core.series.Series'>
## 1108
## Team              PIT
## League             NL
## Year             1968
## RS                583
## RA                532
## W                  80
## OBP             0.306
## SLG             0.343
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1108, dtype: object
## <class 'pandas.core.series.Series'>
## 1128
## Team              PIT
## League             NL
## Year             1967
## RS                679
## RA                693
## W                  81
## OBP             0.324
## SLG              0.38
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1128, dtype: object
## <class 'pandas.core.series.Series'>
## 1148
## Team              PIT
## League             NL
## Year             1966
## RS                759
## RA                641
## W                  92
## OBP             0.329
## SLG             0.428
## BA              0.279
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1148, dtype: object
## <class 'pandas.core.series.Series'>
## 1168
## Team              PIT
## League             NL
## Year             1965
## RS                675
## RA                580
## W                  90
## OBP             0.317
## SLG             0.382
## BA              0.265
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1168, dtype: object
## <class 'pandas.core.series.Series'>
## 1188
## Team              PIT
## League             NL
## Year             1964
## RS                663
## RA                636
## W                  80
## OBP             0.315
## SLG             0.389
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1188, dtype: object
## <class 'pandas.core.series.Series'>
## 1208
## Team              PIT
## League             NL
## Year             1963
## RS                567
## RA                595
## W                  74
## OBP             0.309
## SLG             0.359
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1208, dtype: object
## <class 'pandas.core.series.Series'>
## 1228
## Team              PIT
## League             NL
## Year             1962
## RS                706
## RA                626
## W                  93
## OBP             0.321
## SLG             0.394
## BA              0.268
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 1228, dtype: object
## <class 'pandas.core.series.Series'>
```

<div class="exercise--instructions__content"><p>Instead of using <code>i</code> and <code>row</code> in the for statement to store the output of <code>.iterrows()</code>, use <strong>one</strong> variable named <code>row_tuple</code>.</p></div>

```python
# Use one variable instead of two to store the result of .iterrows()
for row_tuple in pit_df.iterrows():
    print(row_tuple)
```

```
## (21, Team              PIT
## League             NL
## Year             2012
## RS                651
## RA                674
## W                  79
## OBP             0.304
## SLG             0.395
## BA              0.243
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.314
## OSLG             0.39
## Name: 21, dtype: object)
## (51, Team              PIT
## League             NL
## Year             2011
## RS                610
## RA                712
## W                  72
## OBP             0.309
## SLG             0.368
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.338
## OSLG            0.409
## Name: 51, dtype: object)
## (81, Team              PIT
## League             NL
## Year             2010
## RS                587
## RA                866
## W                  57
## OBP             0.304
## SLG             0.373
## BA              0.242
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.348
## OSLG            0.449
## Name: 81, dtype: object)
## (111, Team              PIT
## League             NL
## Year             2009
## RS                636
## RA                768
## W                  62
## OBP             0.318
## SLG             0.387
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.346
## OSLG            0.442
## Name: 111, dtype: object)
## (141, Team              PIT
## League             NL
## Year             2008
## RS                735
## RA                884
## W                  67
## OBP              0.32
## SLG             0.403
## BA              0.258
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.362
## OSLG            0.454
## Name: 141, dtype: object)
## (171, Team              PIT
## League             NL
## Year             2007
## RS                724
## RA                846
## W                  68
## OBP             0.325
## SLG             0.411
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.352
## OSLG            0.447
## Name: 171, dtype: object)
## (201, Team              PIT
## League             NL
## Year             2006
## RS                691
## RA                797
## W                  67
## OBP             0.327
## SLG             0.397
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.357
## OSLG            0.431
## Name: 201, dtype: object)
## (231, Team              PIT
## League             NL
## Year             2005
## RS                680
## RA                769
## W                  67
## OBP             0.322
## SLG               0.4
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.424
## Name: 231, dtype: object)
## (262, Team              PIT
## League             NL
## Year             2004
## RS                680
## RA                744
## W                  72
## OBP             0.321
## SLG             0.401
## BA               0.26
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.416
## Name: 262, dtype: object)
## (292, Team              PIT
## League             NL
## Year             2003
## RS                753
## RA                801
## W                  75
## OBP             0.338
## SLG              0.42
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.336
## OSLG            0.431
## Name: 292, dtype: object)
## (322, Team              PIT
## League             NL
## Year             2002
## RS                641
## RA                730
## W                  72
## OBP             0.319
## SLG             0.381
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.423
## Name: 322, dtype: object)
## (352, Team              PIT
## League             NL
## Year             2001
## RS                657
## RA                858
## W                  62
## OBP             0.313
## SLG             0.393
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.433
## Name: 352, dtype: object)
## (382, Team              PIT
## League             NL
## Year             2000
## RS                793
## RA                888
## W                  69
## OBP             0.339
## SLG             0.424
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.361
## OSLG            0.432
## Name: 382, dtype: object)
## (412, Team              PIT
## League             NL
## Year             1999
## RS                775
## RA                782
## W                  78
## OBP             0.334
## SLG             0.419
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.343
## OSLG             0.42
## Name: 412, dtype: object)
## (442, Team              PIT
## League             NL
## Year             1998
## RS                650
## RA                718
## W                  69
## OBP             0.311
## SLG             0.374
## BA              0.254
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 442, dtype: object)
## (471, Team              PIT
## League             NL
## Year             1997
## RS                725
## RA                760
## W                  79
## OBP             0.329
## SLG             0.404
## BA              0.262
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 471, dtype: object)
## (499, Team              PIT
## League             NL
## Year             1996
## RS                776
## RA                833
## W                  73
## OBP             0.329
## SLG             0.407
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 499, dtype: object)
## (527, Team              PIT
## League             NL
## Year             1993
## RS                707
## RA                806
## W                  75
## OBP             0.335
## SLG             0.393
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 527, dtype: object)
## (553, Team              PIT
## League             NL
## Year             1992
## RS                693
## RA                595
## W                  96
## OBP             0.324
## SLG             0.381
## BA              0.255
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 553, dtype: object)
## (579, Team              PIT
## League             NL
## Year             1991
## RS                768
## RA                632
## W                  98
## OBP             0.338
## SLG             0.398
## BA              0.263
## Playoffs            1
## RankSeason        1.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 579, dtype: object)
## (605, Team              PIT
## League             NL
## Year             1990
## RS                733
## RA                619
## W                  95
## OBP              0.33
## SLG             0.405
## BA              0.259
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 605, dtype: object)
## (631, Team              PIT
## League             NL
## Year             1989
## RS                637
## RA                680
## W                  74
## OBP             0.311
## SLG             0.359
## BA              0.241
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 164
## OOBP              NaN
## OSLG              NaN
## Name: 631, dtype: object)
## (657, Team              PIT
## League             NL
## Year             1988
## RS                651
## RA                616
## W                  85
## OBP             0.317
## SLG             0.369
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 160
## OOBP              NaN
## OSLG              NaN
## Name: 657, dtype: object)
## (683, Team              PIT
## League             NL
## Year             1987
## RS                723
## RA                744
## W                  80
## OBP              0.33
## SLG             0.403
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 683, dtype: object)
## (709, Team              PIT
## League             NL
## Year             1986
## RS                663
## RA                700
## W                  64
## OBP             0.321
## SLG             0.374
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 709, dtype: object)
## (735, Team              PIT
## League             NL
## Year             1985
## RS                568
## RA                708
## W                  57
## OBP             0.311
## SLG             0.347
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 735, dtype: object)
## (761, Team              PIT
## League             NL
## Year             1984
## RS                615
## RA                567
## W                  75
## OBP              0.31
## SLG             0.363
## BA              0.255
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 761, dtype: object)
## (787, Team              PIT
## League             NL
## Year             1983
## RS                659
## RA                648
## W                  84
## OBP             0.325
## SLG             0.383
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 787, dtype: object)
## (813, Team              PIT
## League             NL
## Year             1982
## RS                724
## RA                696
## W                  84
## OBP             0.327
## SLG             0.408
## BA              0.273
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 813, dtype: object)
## (839, Team              PIT
## League             NL
## Year             1980
## RS                666
## RA                646
## W                  83
## OBP             0.322
## SLG             0.388
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 839, dtype: object)
## (865, Team              PIT
## League             NL
## Year             1979
## RS                775
## RA                643
## W                  98
## OBP              0.33
## SLG             0.416
## BA              0.272
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 865, dtype: object)
## (891, Team              PIT
## League             NL
## Year             1978
## RS                684
## RA                637
## W                  88
## OBP              0.32
## SLG             0.385
## BA              0.257
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 891, dtype: object)
## (917, Team              PIT
## League             NL
## Year             1977
## RS                734
## RA                665
## W                  96
## OBP             0.331
## SLG             0.413
## BA              0.274
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 917, dtype: object)
## (943, Team              PIT
## League             NL
## Year             1976
## RS                708
## RA                630
## W                  92
## OBP             0.321
## SLG             0.391
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 943, dtype: object)
## (967, Team              PIT
## League             NL
## Year             1975
## RS                712
## RA                565
## W                  92
## OBP             0.323
## SLG             0.402
## BA              0.263
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 967, dtype: object)
## (991, Team              PIT
## League             NL
## Year             1974
## RS                751
## RA                657
## W                  88
## OBP             0.335
## SLG             0.391
## BA              0.274
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 991, dtype: object)
## (1015, Team              PIT
## League             NL
## Year             1973
## RS                704
## RA                693
## W                  80
## OBP             0.315
## SLG             0.405
## BA              0.261
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1015, dtype: object)
## (1039, Team              PIT
## League             NL
## Year             1971
## RS                788
## RA                599
## W                  97
## OBP              0.33
## SLG             0.416
## BA              0.274
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1039, dtype: object)
## (1063, Team              PIT
## League             NL
## Year             1970
## RS                729
## RA                664
## W                  89
## OBP             0.325
## SLG             0.406
## BA               0.27
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1063, dtype: object)
## (1086, Team              PIT
## League             NL
## Year             1969
## RS                725
## RA                652
## W                  88
## OBP             0.334
## SLG             0.398
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1086, dtype: object)
## (1108, Team              PIT
## League             NL
## Year             1968
## RS                583
## RA                532
## W                  80
## OBP             0.306
## SLG             0.343
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1108, dtype: object)
## (1128, Team              PIT
## League             NL
## Year             1967
## RS                679
## RA                693
## W                  81
## OBP             0.324
## SLG              0.38
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1128, dtype: object)
## (1148, Team              PIT
## League             NL
## Year             1966
## RS                759
## RA                641
## W                  92
## OBP             0.329
## SLG             0.428
## BA              0.279
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1148, dtype: object)
## (1168, Team              PIT
## League             NL
## Year             1965
## RS                675
## RA                580
## W                  90
## OBP             0.317
## SLG             0.382
## BA              0.265
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1168, dtype: object)
## (1188, Team              PIT
## League             NL
## Year             1964
## RS                663
## RA                636
## W                  80
## OBP             0.315
## SLG             0.389
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1188, dtype: object)
## (1208, Team              PIT
## League             NL
## Year             1963
## RS                567
## RA                595
## W                  74
## OBP             0.309
## SLG             0.359
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1208, dtype: object)
## (1228, Team              PIT
## League             NL
## Year             1962
## RS                706
## RA                626
## W                  93
## OBP             0.321
## SLG             0.394
## BA              0.268
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 1228, dtype: object)
```

<div class="exercise--instructions__content"><p>Add a line in the for loop to print the type of each <code>row_tuple</code>.</p></div>

```python
# Print the row and type of each row
for row_tuple in pit_df.iterrows():
    print(row_tuple)
    print(type(row_tuple))
```

```
## (21, Team              PIT
## League             NL
## Year             2012
## RS                651
## RA                674
## W                  79
## OBP             0.304
## SLG             0.395
## BA              0.243
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.314
## OSLG             0.39
## Name: 21, dtype: object)
## <class 'tuple'>
## (51, Team              PIT
## League             NL
## Year             2011
## RS                610
## RA                712
## W                  72
## OBP             0.309
## SLG             0.368
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.338
## OSLG            0.409
## Name: 51, dtype: object)
## <class 'tuple'>
## (81, Team              PIT
## League             NL
## Year             2010
## RS                587
## RA                866
## W                  57
## OBP             0.304
## SLG             0.373
## BA              0.242
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.348
## OSLG            0.449
## Name: 81, dtype: object)
## <class 'tuple'>
## (111, Team              PIT
## League             NL
## Year             2009
## RS                636
## RA                768
## W                  62
## OBP             0.318
## SLG             0.387
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.346
## OSLG            0.442
## Name: 111, dtype: object)
## <class 'tuple'>
## (141, Team              PIT
## League             NL
## Year             2008
## RS                735
## RA                884
## W                  67
## OBP              0.32
## SLG             0.403
## BA              0.258
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.362
## OSLG            0.454
## Name: 141, dtype: object)
## <class 'tuple'>
## (171, Team              PIT
## League             NL
## Year             2007
## RS                724
## RA                846
## W                  68
## OBP             0.325
## SLG             0.411
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.352
## OSLG            0.447
## Name: 171, dtype: object)
## <class 'tuple'>
## (201, Team              PIT
## League             NL
## Year             2006
## RS                691
## RA                797
## W                  67
## OBP             0.327
## SLG             0.397
## BA              0.263
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.357
## OSLG            0.431
## Name: 201, dtype: object)
## <class 'tuple'>
## (231, Team              PIT
## League             NL
## Year             2005
## RS                680
## RA                769
## W                  67
## OBP             0.322
## SLG               0.4
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.424
## Name: 231, dtype: object)
## <class 'tuple'>
## (262, Team              PIT
## League             NL
## Year             2004
## RS                680
## RA                744
## W                  72
## OBP             0.321
## SLG             0.401
## BA               0.26
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.416
## Name: 262, dtype: object)
## <class 'tuple'>
## (292, Team              PIT
## League             NL
## Year             2003
## RS                753
## RA                801
## W                  75
## OBP             0.338
## SLG              0.42
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.336
## OSLG            0.431
## Name: 292, dtype: object)
## <class 'tuple'>
## (322, Team              PIT
## League             NL
## Year             2002
## RS                641
## RA                730
## W                  72
## OBP             0.319
## SLG             0.381
## BA              0.244
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.342
## OSLG            0.423
## Name: 322, dtype: object)
## <class 'tuple'>
## (352, Team              PIT
## League             NL
## Year             2001
## RS                657
## RA                858
## W                  62
## OBP             0.313
## SLG             0.393
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.344
## OSLG            0.433
## Name: 352, dtype: object)
## <class 'tuple'>
## (382, Team              PIT
## League             NL
## Year             2000
## RS                793
## RA                888
## W                  69
## OBP             0.339
## SLG             0.424
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP            0.361
## OSLG            0.432
## Name: 382, dtype: object)
## <class 'tuple'>
## (412, Team              PIT
## League             NL
## Year             1999
## RS                775
## RA                782
## W                  78
## OBP             0.334
## SLG             0.419
## BA              0.259
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP            0.343
## OSLG             0.42
## Name: 412, dtype: object)
## <class 'tuple'>
## (442, Team              PIT
## League             NL
## Year             1998
## RS                650
## RA                718
## W                  69
## OBP             0.311
## SLG             0.374
## BA              0.254
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 442, dtype: object)
## <class 'tuple'>
## (471, Team              PIT
## League             NL
## Year             1997
## RS                725
## RA                760
## W                  79
## OBP             0.329
## SLG             0.404
## BA              0.262
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 471, dtype: object)
## <class 'tuple'>
## (499, Team              PIT
## League             NL
## Year             1996
## RS                776
## RA                833
## W                  73
## OBP             0.329
## SLG             0.407
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 499, dtype: object)
## <class 'tuple'>
## (527, Team              PIT
## League             NL
## Year             1993
## RS                707
## RA                806
## W                  75
## OBP             0.335
## SLG             0.393
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 527, dtype: object)
## <class 'tuple'>
## (553, Team              PIT
## League             NL
## Year             1992
## RS                693
## RA                595
## W                  96
## OBP             0.324
## SLG             0.381
## BA              0.255
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 553, dtype: object)
## <class 'tuple'>
## (579, Team              PIT
## League             NL
## Year             1991
## RS                768
## RA                632
## W                  98
## OBP             0.338
## SLG             0.398
## BA              0.263
## Playoffs            1
## RankSeason        1.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 579, dtype: object)
## <class 'tuple'>
## (605, Team              PIT
## League             NL
## Year             1990
## RS                733
## RA                619
## W                  95
## OBP              0.33
## SLG             0.405
## BA              0.259
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 605, dtype: object)
## <class 'tuple'>
## (631, Team              PIT
## League             NL
## Year             1989
## RS                637
## RA                680
## W                  74
## OBP             0.311
## SLG             0.359
## BA              0.241
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 164
## OOBP              NaN
## OSLG              NaN
## Name: 631, dtype: object)
## <class 'tuple'>
## (657, Team              PIT
## League             NL
## Year             1988
## RS                651
## RA                616
## W                  85
## OBP             0.317
## SLG             0.369
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 160
## OOBP              NaN
## OSLG              NaN
## Name: 657, dtype: object)
## <class 'tuple'>
## (683, Team              PIT
## League             NL
## Year             1987
## RS                723
## RA                744
## W                  80
## OBP              0.33
## SLG             0.403
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 683, dtype: object)
## <class 'tuple'>
## (709, Team              PIT
## League             NL
## Year             1986
## RS                663
## RA                700
## W                  64
## OBP             0.321
## SLG             0.374
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 709, dtype: object)
## <class 'tuple'>
## (735, Team              PIT
## League             NL
## Year             1985
## RS                568
## RA                708
## W                  57
## OBP             0.311
## SLG             0.347
## BA              0.247
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 735, dtype: object)
## <class 'tuple'>
## (761, Team              PIT
## League             NL
## Year             1984
## RS                615
## RA                567
## W                  75
## OBP              0.31
## SLG             0.363
## BA              0.255
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 761, dtype: object)
## <class 'tuple'>
## (787, Team              PIT
## League             NL
## Year             1983
## RS                659
## RA                648
## W                  84
## OBP             0.325
## SLG             0.383
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 787, dtype: object)
## <class 'tuple'>
## (813, Team              PIT
## League             NL
## Year             1982
## RS                724
## RA                696
## W                  84
## OBP             0.327
## SLG             0.408
## BA              0.273
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 813, dtype: object)
## <class 'tuple'>
## (839, Team              PIT
## League             NL
## Year             1980
## RS                666
## RA                646
## W                  83
## OBP             0.322
## SLG             0.388
## BA              0.266
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 839, dtype: object)
## <class 'tuple'>
## (865, Team              PIT
## League             NL
## Year             1979
## RS                775
## RA                643
## W                  98
## OBP              0.33
## SLG             0.416
## BA              0.272
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 865, dtype: object)
## <class 'tuple'>
## (891, Team              PIT
## League             NL
## Year             1978
## RS                684
## RA                637
## W                  88
## OBP              0.32
## SLG             0.385
## BA              0.257
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 891, dtype: object)
## <class 'tuple'>
## (917, Team              PIT
## League             NL
## Year             1977
## RS                734
## RA                665
## W                  96
## OBP             0.331
## SLG             0.413
## BA              0.274
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 917, dtype: object)
## <class 'tuple'>
## (943, Team              PIT
## League             NL
## Year             1976
## RS                708
## RA                630
## W                  92
## OBP             0.321
## SLG             0.391
## BA              0.267
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 943, dtype: object)
## <class 'tuple'>
## (967, Team              PIT
## League             NL
## Year             1975
## RS                712
## RA                565
## W                  92
## OBP             0.323
## SLG             0.402
## BA              0.263
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 967, dtype: object)
## <class 'tuple'>
## (991, Team              PIT
## League             NL
## Year             1974
## RS                751
## RA                657
## W                  88
## OBP             0.335
## SLG             0.391
## BA              0.274
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 991, dtype: object)
## <class 'tuple'>
## (1015, Team              PIT
## League             NL
## Year             1973
## RS                704
## RA                693
## W                  80
## OBP             0.315
## SLG             0.405
## BA              0.261
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1015, dtype: object)
## <class 'tuple'>
## (1039, Team              PIT
## League             NL
## Year             1971
## RS                788
## RA                599
## W                  97
## OBP              0.33
## SLG             0.416
## BA              0.274
## Playoffs            1
## RankSeason        2.0
## RankPlayoffs      1.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1039, dtype: object)
## <class 'tuple'>
## (1063, Team              PIT
## League             NL
## Year             1970
## RS                729
## RA                664
## W                  89
## OBP             0.325
## SLG             0.406
## BA               0.27
## Playoffs            1
## RankSeason        4.0
## RankPlayoffs      3.0
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1063, dtype: object)
## <class 'tuple'>
## (1086, Team              PIT
## League             NL
## Year             1969
## RS                725
## RA                652
## W                  88
## OBP             0.334
## SLG             0.398
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1086, dtype: object)
## <class 'tuple'>
## (1108, Team              PIT
## League             NL
## Year             1968
## RS                583
## RA                532
## W                  80
## OBP             0.306
## SLG             0.343
## BA              0.252
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1108, dtype: object)
## <class 'tuple'>
## (1128, Team              PIT
## League             NL
## Year             1967
## RS                679
## RA                693
## W                  81
## OBP             0.324
## SLG              0.38
## BA              0.277
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1128, dtype: object)
## <class 'tuple'>
## (1148, Team              PIT
## League             NL
## Year             1966
## RS                759
## RA                641
## W                  92
## OBP             0.329
## SLG             0.428
## BA              0.279
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1148, dtype: object)
## <class 'tuple'>
## (1168, Team              PIT
## League             NL
## Year             1965
## RS                675
## RA                580
## W                  90
## OBP             0.317
## SLG             0.382
## BA              0.265
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 163
## OOBP              NaN
## OSLG              NaN
## Name: 1168, dtype: object)
## <class 'tuple'>
## (1188, Team              PIT
## League             NL
## Year             1964
## RS                663
## RA                636
## W                  80
## OBP             0.315
## SLG             0.389
## BA              0.264
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1188, dtype: object)
## <class 'tuple'>
## (1208, Team              PIT
## League             NL
## Year             1963
## RS                567
## RA                595
## W                  74
## OBP             0.309
## SLG             0.359
## BA               0.25
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 162
## OOBP              NaN
## OSLG              NaN
## Name: 1208, dtype: object)
## <class 'tuple'>
## (1228, Team              PIT
## League             NL
## Year             1962
## RS                706
## RA                626
## W                  93
## OBP             0.321
## SLG             0.394
## BA              0.268
## Playoffs            0
## RankSeason        NaN
## RankPlayoffs      NaN
## G                 161
## OOBP              NaN
## OSLG              NaN
## Name: 1228, dtype: object)
## <class 'tuple'>
```

<p class="">Nice work! Since <code>.iterrows()</code> returns each DataFrame row as a tuple of (index, <code>pandas</code> Series) pairs, you can either split this tuple and use the index and row-values separately (as you did with <code>for i,row in pit_df.iterrows()</code>), or you can keep the result of <code>.iterrows()</code> in the tuple form (as you did with <code>for row_tuple in pit_df.iterrows()</code>).<br><br>If using <code>i,row</code>, you can access things from the row using square brackets (i.e., <code>row['Team']</code>). If using <code>row_tuple</code>, you would have to specify which element of the tuple you'd like to access before grabbing the team name (i.e., <code>row_tuple[1]['Team']</code>). <br><br> With either approach, using <code>.iterrows()</code> will still be substantially faster than using <code>.iloc</code> as you saw in the video.</p>

### Run differentials with .iterrows()


<div class>
<p>You've been hired by the San Francisco Giants as an analyst—congrats! The team's owner wants you to calculate a metric called the <em>run differential</em> for each season from the year 2008 to 2012. This metric is calculated by subtracting the total number of runs a team allowed in a season from the team's total number of runs scored in a season. <code>'RS'</code> means runs scored and <code>'RA'</code> means runs allowed.</p>
<p>The below function calculates this metric:</p>
<pre><code>def calc_run_diff(runs_scored, runs_allowed):

    run_diff = runs_scored - runs_allowed

    return run_diff
</code></pre>
<p>A DataFrame has been loaded into your session as <code>giants_df</code> and printed into the console. Let's practice using <code>.iterrows()</code> to add a <em>run differential</em> column to this DataFrame.</p>
</div>

```python
# edited/added
giants_df = baseball_df[(baseball_df.Team == 'SFG') & (baseball_df.Year.between(2008,2012))][['Team', 'League', 'Year', 'RS', 'RA', 'W', 'G', 'Playoffs']]

def calc_run_diff(runs_scored, runs_allowed):

    run_diff = runs_scored - runs_allowed

    return run_diff
```
<li>Create an empty list called <code>run_diffs</code> that will be used to store the <em>run differentials</em> you will calculate.</li>

```python
# Create an empty list to store run differentials
run_diffs = []
```
<li>Write a for loop that uses <code>.iterrows()</code> to loop over <code>giants_df</code> and collects each row's runs scored and runs allowed.</li>

```python
# Create an empty list to store run differentials
run_diffs = []

# Write a for loop and collect runs allowed and runs scored for each row
for i,row in giants_df.iterrows():
    runs_scored = row['RS']
    runs_allowed = row['RA']
```
<li>Add a line to the for loop that uses the provided function to calculate each row's <em>run differential</em>.</li>

```python
# Create an empty list to store run differentials
run_diffs = []

# Write a for loop and collect runs allowed and runs scored for each row
for i,row in giants_df.iterrows():
    runs_scored = row['RS']
    runs_allowed = row['RA']
    
    # Use the provided function to calculate run_diff for each row
    run_diff = calc_run_diff(runs_scored, runs_allowed)
```
<li>Add a line to the loop that appends each row's <em>run differential</em> to the <code>run_diffs</code> list.</li>

```python
# Create an empty list to store run differentials
run_diffs = []

# Write a for loop and collect runs allowed and runs scored for each row
for i,row in giants_df.iterrows():
    runs_scored = row['RS']
    runs_allowed = row['RA']
    
    # Use the provided function to calculate run_diff for each row
    run_diff = calc_run_diff(runs_scored, runs_allowed)
    
    # Append each run differential to the output list
    run_diffs.append(run_diff)

giants_df['RD'] = run_diffs
print(giants_df)
```

```
##     Team League  Year   RS   RA   W    G  Playoffs   RD
## 24   SFG     NL  2012  718  649  94  162         1   69
## 54   SFG     NL  2011  570  578  86  162         0   -8
## 84   SFG     NL  2010  697  583  92  162         1  114
## 114  SFG     NL  2009  657  611  88  162         0   46
## 144  SFG     NL  2008  640  759  72  162         0 -119
```

<p class="">Great job! Take a look at the <code>giants_df</code> DataFrame with the new run differential column (<code>'RD'</code>) you created (it has been printed in the console).<br><br>The <code>'Playoffs'</code> column tells you if a team made the playoffs for a given season. A <code>1</code> means that the team made the playoffs in that season and a <code>0</code> means the team did not make the playoffs in that season.<br><br>Did you notice that in the seasons with the highest run differentials the Giants made the playoffs? In fact, in both of these seasons (2010 and 2012), the San Francisco Giants not only made the playoffs but also won the World Series! Cool!</p>

## Another iterator method: .itertuples()



### Iterating with .itertuples()


<div class>
<p>Remember, <code>.itertuples()</code> returns each DataFrame row as a special data type called a <strong>namedtuple</strong>. You can look up an attribute within a namedtuple with a special syntax. Let's practice working with namedtuples.</p>
<p>A <code>pandas</code> DataFrame has been loaded into your session called <code>rangers_df</code>. This DataFrame contains the stats (<code>'Team'</code>, <code>'League'</code>, <code>'Year'</code>, <code>'RS'</code>, <code>'RA'</code>, '<code>W'</code>, <code>'G'</code>, and <code>'Playoffs'</code>) for the Major League baseball team named the Texas Rangers (abbreviated as <code>'TEX'</code>).</p>
</div>
<div class="exercise--instructions__content"><p>Use <code>.itertuples()</code> to loop over <code>rangers_df</code> and print each row.</p></div>

```python
# edited/added
rangers_df = baseball_df[(baseball_df.Team == 'TEX') & (baseball_df.Year.between(1973,2012))][['Team', 'League', 'Year', 'RS', 'RA', 'W', 'G', 'Playoffs']]

# Loop over the DataFrame and print each row
for row in rangers_df.itertuples():
  print(row)
```

```
## Pandas(Index=27, Team='TEX', League='AL', Year=2012, RS=808, RA=707, W=93, G=162, Playoffs=1)
## Pandas(Index=57, Team='TEX', League='AL', Year=2011, RS=855, RA=677, W=96, G=162, Playoffs=1)
## Pandas(Index=87, Team='TEX', League='AL', Year=2010, RS=787, RA=687, W=90, G=162, Playoffs=1)
## Pandas(Index=117, Team='TEX', League='AL', Year=2009, RS=784, RA=740, W=87, G=162, Playoffs=0)
## Pandas(Index=147, Team='TEX', League='AL', Year=2008, RS=901, RA=967, W=79, G=162, Playoffs=0)
## Pandas(Index=177, Team='TEX', League='AL', Year=2007, RS=816, RA=844, W=75, G=162, Playoffs=0)
## Pandas(Index=207, Team='TEX', League='AL', Year=2006, RS=835, RA=784, W=80, G=162, Playoffs=0)
## Pandas(Index=237, Team='TEX', League='AL', Year=2005, RS=865, RA=858, W=79, G=162, Playoffs=0)
## Pandas(Index=268, Team='TEX', League='AL', Year=2004, RS=860, RA=794, W=89, G=162, Playoffs=0)
## Pandas(Index=298, Team='TEX', League='AL', Year=2003, RS=826, RA=969, W=71, G=162, Playoffs=0)
## Pandas(Index=328, Team='TEX', League='AL', Year=2002, RS=843, RA=882, W=72, G=162, Playoffs=0)
## Pandas(Index=358, Team='TEX', League='AL', Year=2001, RS=890, RA=968, W=73, G=162, Playoffs=0)
## Pandas(Index=388, Team='TEX', League='AL', Year=2000, RS=848, RA=974, W=71, G=162, Playoffs=0)
## Pandas(Index=418, Team='TEX', League='AL', Year=1999, RS=945, RA=859, W=95, G=162, Playoffs=1)
## Pandas(Index=448, Team='TEX', League='AL', Year=1998, RS=940, RA=871, W=88, G=162, Playoffs=1)
## Pandas(Index=476, Team='TEX', League='AL', Year=1997, RS=807, RA=823, W=77, G=162, Playoffs=0)
## Pandas(Index=504, Team='TEX', League='AL', Year=1996, RS=928, RA=799, W=90, G=163, Playoffs=1)
## Pandas(Index=532, Team='TEX', League='AL', Year=1993, RS=835, RA=751, W=86, G=162, Playoffs=0)
## Pandas(Index=558, Team='TEX', League='AL', Year=1992, RS=682, RA=753, W=77, G=162, Playoffs=0)
## Pandas(Index=584, Team='TEX', League='AL', Year=1991, RS=829, RA=814, W=85, G=162, Playoffs=0)
## Pandas(Index=610, Team='TEX', League='AL', Year=1990, RS=676, RA=696, W=83, G=162, Playoffs=0)
## Pandas(Index=636, Team='TEX', League='AL', Year=1989, RS=695, RA=714, W=83, G=162, Playoffs=0)
## Pandas(Index=662, Team='TEX', League='AL', Year=1988, RS=637, RA=735, W=70, G=161, Playoffs=0)
## Pandas(Index=688, Team='TEX', League='AL', Year=1987, RS=823, RA=849, W=75, G=162, Playoffs=0)
## Pandas(Index=714, Team='TEX', League='AL', Year=1986, RS=771, RA=743, W=87, G=162, Playoffs=0)
## Pandas(Index=740, Team='TEX', League='AL', Year=1985, RS=617, RA=785, W=62, G=161, Playoffs=0)
## Pandas(Index=766, Team='TEX', League='AL', Year=1984, RS=656, RA=714, W=69, G=161, Playoffs=0)
## Pandas(Index=792, Team='TEX', League='AL', Year=1983, RS=639, RA=609, W=77, G=163, Playoffs=0)
## Pandas(Index=818, Team='TEX', League='AL', Year=1982, RS=590, RA=749, W=64, G=162, Playoffs=0)
## Pandas(Index=844, Team='TEX', League='AL', Year=1980, RS=756, RA=752, W=76, G=163, Playoffs=0)
## Pandas(Index=870, Team='TEX', League='AL', Year=1979, RS=750, RA=698, W=83, G=162, Playoffs=0)
## Pandas(Index=896, Team='TEX', League='AL', Year=1978, RS=692, RA=632, W=87, G=162, Playoffs=0)
## Pandas(Index=922, Team='TEX', League='AL', Year=1977, RS=767, RA=657, W=94, G=162, Playoffs=0)
## Pandas(Index=947, Team='TEX', League='AL', Year=1976, RS=616, RA=652, W=76, G=162, Playoffs=0)
## Pandas(Index=971, Team='TEX', League='AL', Year=1975, RS=714, RA=733, W=79, G=162, Playoffs=0)
## Pandas(Index=995, Team='TEX', League='AL', Year=1974, RS=690, RA=698, W=83, G=161, Playoffs=0)
## Pandas(Index=1019, Team='TEX', League='AL', Year=1973, RS=619, RA=844, W=57, G=162, Playoffs=0)
```

<div class="exercise--instructions__content"><p>Loop over <code>rangers_df</code> with <code>.itertuples()</code> and save each row's <code>Index</code>, <code>Year</code>, and Wins (<code>W</code>) attribute as <code>i</code>, <code>year</code>, and <code>wins</code>.</p></div>

```python
# Loop over the DataFrame and print each row's Index, Year and Wins (W)
for row in rangers_df.itertuples():
  i = row.Index
  year = row.Year
  wins = row.W
  print(i, year, wins)
```

```
## 27 2012 93
## 57 2011 96
## 87 2010 90
## 117 2009 87
## 147 2008 79
## 177 2007 75
## 207 2006 80
## 237 2005 79
## 268 2004 89
## 298 2003 71
## 328 2002 72
## 358 2001 73
## 388 2000 71
## 418 1999 95
## 448 1998 88
## 476 1997 77
## 504 1996 90
## 532 1993 86
## 558 1992 77
## 584 1991 85
## 610 1990 83
## 636 1989 83
## 662 1988 70
## 688 1987 75
## 714 1986 87
## 740 1985 62
## 766 1984 69
## 792 1983 77
## 818 1982 64
## 844 1980 76
## 870 1979 83
## 896 1978 87
## 922 1977 94
## 947 1976 76
## 971 1975 79
## 995 1974 83
## 1019 1973 57
```

<div class="exercise--instructions__content"><p>Now, loop over <code>rangers_df</code> and print these values <strong>only for those rows</strong> where the Rangers made the playoffs.</p></div>

```python
# Loop over the DataFrame and print each row's Index, Year and Wins (W)
for row in rangers_df.itertuples():
  i = row.Index
  year = row.Year
  wins = row.W
  
  # Check if rangers made Playoffs (1 means yes; 0 means no)
  if row.Playoffs == 1:
    print(i, year, wins)
```

```
## 27 2012 93
## 57 2011 96
## 87 2010 90
## 418 1999 95
## 448 1998 88
## 504 1996 90
```

<p class="">Awesome! You're getting the hang of using <code>.itertuples()</code>. Remember, you need to use the <em>dot</em> syntax for referencing an attribute in a <strong>namedtuple</strong>.<br><br> You can create a new variable using a row's dot reference (as you did when storing <code>row.Index</code> as the variable <code>i</code>). Or you can use the row's dot reference directly to perform calculations and checks. Notice that you did not have to save <code>row.Playoffs</code> to a new variable in your check statement (you were able to use <code>row.Playoffs</code> directly in your check).<br><br> Did you notice the pattern in the Texas Rangers playoff appearances? Only six appearances and two distinct sets of groupings (one from 2010 - 2012 and one from 1996 - 1999).</p>

### Run differentials with .itertuples()


<div class>
<p>The New York Yankees have made a trade with the San Francisco Giants for your analyst contract— you're a hot commodity! Your new boss has seen your work with the Giants and now wants you to do something similar with the Yankees data. He'd like you to calculate <em>run differentials</em> for the Yankees from the year 1962 to the year 2012 and find which season they had the best <em>run differential</em>.</p>
<p>You've remembered the function you used when working with the Giants and quickly write it down:</p>
<pre><code>def calc_run_diff(runs_scored, runs_allowed):

    run_diff = runs_scored - runs_allowed

    return run_diff
</code></pre>
<p>Let's use <code>.itertuples()</code> to loop over the <code>yankees_df</code> DataFrame (which has been loaded into your session) and calculate <em>run differentials</em>.</p>
</div>

```python
# edited/added
yankees_df = baseball_df[(baseball_df.Team == 'NYY') & (baseball_df.Year.between(1962,2012))][['Team', 'League', 'Year', 'RS', 'RA', 'W', 'G', 'Playoffs']]
```
<li>Use <code>.itertuples()</code> to loop over <code>yankees_df</code> and grab each row's runs scored and runs allowed values.</li>

```python
run_diffs = []

# Loop over the DataFrame and calculate each row's run differential
for row in yankees_df.itertuples():
    
    runs_scored = row.RS
    runs_allowed = row.RA
```
<li>Now, calculate each row's <em>run differential</em> using <code>calc_run_diff()</code>. Be sure to append each row's <em>run differential</em> to <code>run_diffs</code>.</li>

```python
run_diffs = []

# Loop over the DataFrame and calculate each row's run differential
for row in yankees_df.itertuples():
    
    runs_scored = row.RS
    runs_allowed = row.RA

    run_diff = calc_run_diff(runs_scored, runs_allowed)
    
    run_diffs.append(run_diff)
```
<li>Append a new column called <code>'RD'</code> to the <code>yankees_df</code> DataFrame that contains the <em>run differentials</em> you calculated.</li>

```python
run_diffs = []

# Loop over the DataFrame and calculate each row's run differential
for row in yankees_df.itertuples():
    
    runs_scored = row.RS
    runs_allowed = row.RA

    run_diff = calc_run_diff(runs_scored, runs_allowed)
    
    run_diffs.append(run_diff)

# Append new column
yankees_df['RD'] = run_diffs
print(yankees_df)
```

```
##      Team League  Year   RS   RA    W    G  Playoffs   RD
## 18    NYY     AL  2012  804  668   95  162         1  136
## 48    NYY     AL  2011  867  657   97  162         1  210
## 78    NYY     AL  2010  859  693   95  162         1  166
## 108   NYY     AL  2009  915  753  103  162         1  162
## 138   NYY     AL  2008  789  727   89  162         0   62
## 168   NYY     AL  2007  968  777   94  162         1  191
## 198   NYY     AL  2006  930  767   97  162         1  163
## 228   NYY     AL  2005  886  789   95  162         1   97
## 259   NYY     AL  2004  897  808  101  162         1   89
## 289   NYY     AL  2003  877  716  101  163         1  161
## 319   NYY     AL  2002  897  697  103  161         1  200
## 349   NYY     AL  2001  804  713   95  161         1   91
## 379   NYY     AL  2000  871  814   87  161         1   57
## 409   NYY     AL  1999  900  731   98  162         1  169
## 439   NYY     AL  1998  965  656  114  162         1  309
## 468   NYY     AL  1997  891  688   96  162         1  203
## 496   NYY     AL  1996  871  787   92  162         1   84
## 524   NYY     AL  1993  821  761   88  162         0   60
## 550   NYY     AL  1992  733  746   76  162         0  -13
## 576   NYY     AL  1991  674  777   71  162         0 -103
## 602   NYY     AL  1990  603  749   67  162         0 -146
## 628   NYY     AL  1989  698  792   74  161         0  -94
## 654   NYY     AL  1988  772  748   85  161         0   24
## 680   NYY     AL  1987  788  758   89  162         0   30
## 706   NYY     AL  1986  797  738   90  162         0   59
## 732   NYY     AL  1985  839  660   97  161         0  179
## 758   NYY     AL  1984  758  679   87  162         0   79
## 784   NYY     AL  1983  770  703   91  162         0   67
## 810   NYY     AL  1982  709  716   79  162         0   -7
## 836   NYY     AL  1980  820  662  103  162         1  158
## 862   NYY     AL  1979  734  672   89  160         0   62
## 888   NYY     AL  1978  735  582  100  163         1  153
## 914   NYY     AL  1977  831  651  100  162         1  180
## 940   NYY     AL  1976  730  575   97  159         1  155
## 964   NYY     AL  1975  681  588   83  160         0   93
## 988   NYY     AL  1974  671  623   89  162         0   48
## 1012  NYY     AL  1973  641  610   80  162         0   31
## 1036  NYY     AL  1971  648  641   81  162         0    7
## 1060  NYY     AL  1970  680  612   93  163         0   68
## 1083  NYY     AL  1969  562  587   80  162         0  -25
## 1105  NYY     AL  1968  536  531   83  164         0    5
## 1126  NYY     AL  1967  522  621   72  163         0  -99
## 1146  NYY     AL  1966  611  612   70  160         0   -1
## 1166  NYY     AL  1965  611  604   77  162         0    7
## 1186  NYY     AL  1964  730  577   99  164         1  153
## 1206  NYY     AL  1963  714  547  104  161         1  167
## 1226  NYY     AL  1962  817  680   96  162         1  137
```

<div class=""><ul>
<li>In what year within your DataFrame did the New York Yankees have the highest <em>run differential</em>?</li>
</ul>
<p><strong>You'll need to rerun the code that creates the <code>'RD'</code> column if you'd like to analyze the DataFrame with code rather than looking at the console output.</strong></p></div>

- [ ] In <strong>2011</strong> (with a <em>Run Differential</em> of <strong>210</strong>)
- [x] In <strong>1998</strong> (with a <em>Run Differential</em> of <strong>309</strong>)
- [ ] In <strong>1962</strong> (with a <em>Run Differential</em> of <strong>503</strong>)
- [ ] In <strong>1985</strong> (with a <em>Run Differential</em> of <strong>315</strong>)

<p class="">Great job! You used <code>.itertuples()</code> to help the Yankees calculate <em>run differentials</em>. Remember, using <code>.itertuples()</code> is just like using <code>.iterrows()</code> except it tends to be faster. You also have to use a <em>dot</em> reference when looking up attributes with <code>.itertuples()</code>.<br><br> You found that the Yankees' highest <em>run differential</em> was in 1998. Did you know they actually hold the record for the highest <em>run differential</em> in an MLB season (411 in the year 1939 where they scored 967 runs and allowed 556)? Wow!</p>

## pandas alternative to looping



### Analyzing baseball stats with .apply()


<div class>
<p>The Tampa Bay Rays want you to analyze their data.</p>
<p>They'd like the following metrics:</p>
<ul>
<li>The sum of each column in the data</li>
<li>The total amount of runs scored in a year (<code>'RS'</code> + <code>'RA'</code> for each year)</li>
<li>The <code>'Playoffs'</code> column in text format rather than using <code>1</code>'s and <code>0</code>'s</li>
</ul>
<p>The below function can be used to convert the <code>'Playoffs'</code> column to text:</p>
<pre><code>def text_playoffs(num_playoffs): 
    if num_playoffs == 1:
        return 'Yes'
    else:
        return 'No' 
</code></pre>
<p>Use <code>.apply()</code> to get these metrics. A DataFrame (<code>rays_df</code>) has been loaded and printed to the console. This DataFrame is indexed on the <code>'Year'</code> column.</p>
</div>
<div class="exercise--instructions__content"><p>Apply <code>sum()</code> to each <strong>column</strong> of <code>rays_df</code> to collect the sum of each column. Be sure to specify the correct <code>axis</code>.</p></div>

```python
# edited/added
def text_playoffs(num_playoffs): 
    if num_playoffs == 1:
        return 'Yes'
    else:
        return 'No' 

rays_df = baseball_df[baseball_df.Team == 'TBR'][['Year', 'RS', 'RA', 'W', 'Playoffs']].set_index('Year')
rays_df.index.names = [None]

# Gather sum of all columns
stat_totals = rays_df.apply(sum, axis=0)
print(stat_totals)
```

```
## RS          3783
## RA          3265
## W            458
## Playoffs       3
## dtype: int64
```

<div class="exercise--instructions__content"><p>Apply <code>sum()</code> to each <strong>row</strong> of <code>rays_df</code>, only looking at the <code>'RS'</code> and <code>'RA'</code> columns, and specify the correct <code>axis</code>.</p></div>

```python
# Gather total runs scored in all games per year
total_runs_scored = rays_df[['RS', 'RA']].apply(sum, axis=1)
print(total_runs_scored)
```

```
## 2012    1274
## 2011    1321
## 2010    1451
## 2009    1557
## 2008    1445
## dtype: int64
```

<div class="exercise--instructions__content"><p>Use <code>.apply()</code> and a <code>lambda</code> function to apply <code>text_playoffs()</code> to each <strong>row</strong>'s <code>'Playoffs'</code> value of the <code>rays_df</code> DataFrame.</p></div>

```python
# Convert numeric playoffs to text by applying text_playoffs()
textual_playoffs = rays_df.apply(lambda row: text_playoffs(row['Playoffs']), axis=1)
print(textual_playoffs)
```

```
## 2012     No
## 2011    Yes
## 2010    Yes
## 2009     No
## 2008    Yes
## dtype: object
```

<p class="">Great work! The <code>.apply()</code> method let's you apply functions to all rows or columns of a DataFrame by specifying an axis.<br><br>If you've been using <code>pandas</code> for some time, you may have noticed that a better way to find these stats would use the <code>pandas</code> built-in <code>.sum()</code> method.<br><br> You could have used <code>rays_df.sum(axis=0)</code> to get columnar sums and <code>rays_df[['RS', 'RA']].sum(axis=1)</code> to get row sums.<br><br> You could have also used <code>.apply()</code> <strong>directly</strong> on a Series (or column) of the DataFrame. For example, you could use <code>rays_df['Playoffs'].apply(text_playoffs)</code> to convert the <code>'Playoffs'</code> column to text.</p>

### Settle a debate with .apply()


<div class>
<p>Word has gotten to the Arizona Diamondbacks about your awesome analytics skills. They'd like for you to help settle a debate amongst the managers. One manager claims that the team has made the playoffs every year they have had a win percentage of <code>0.50</code> or greater. Another manager says this is not true.</p>
<p>Let's use the below function and the <code>.apply()</code> method to see which manager is correct.</p>
<pre><code>def calc_win_perc(wins, games_played):
    win_perc = wins / games_played
    return np.round(win_perc,2)
</code></pre>
<p>A DataFrame named <code>dbacks_df</code> has been loaded into your session.</p>
</div>

```python
# edited/added
def calc_win_perc(wins, games_played):
    win_perc = wins / games_played
    return np.round(win_perc,2)
  
dbacks_df = baseball_df[(baseball_df.Team == 'ARI') & (baseball_df.Year.between(1998,2012))][['Team', 'League', 'Year', 'RS', 'RA', 'W', 'G', 'Playoffs']]
```
<li>Print the first five rows of the <code>dbacks_df</code> DataFrame to see what the data looks like.</li>

```python
# Display the first five rows of the DataFrame
print(dbacks_df.head())
```

```
##     Team League  Year   RS   RA   W    G  Playoffs
## 0    ARI     NL  2012  734  688  81  162         0
## 30   ARI     NL  2011  731  662  94  162         1
## 60   ARI     NL  2010  713  836  65  162         0
## 90   ARI     NL  2009  720  782  70  162         0
## 120  ARI     NL  2008  720  706  82  162         0
```
<li>Create a <code>pandas</code> Series called <code>win_percs</code> by <em>applying</em> the <code>calc_win_perc()</code> function to each <strong>row</strong> of the DataFrame with a <code>lambda</code> function.</li>

```python
# Display the first five rows of the DataFrame
print(dbacks_df.head())

# Create a win percentage Series 
```

```
##     Team League  Year   RS   RA   W    G  Playoffs
## 0    ARI     NL  2012  734  688  81  162         0
## 30   ARI     NL  2011  731  662  94  162         1
## 60   ARI     NL  2010  713  836  65  162         0
## 90   ARI     NL  2009  720  782  70  162         0
## 120  ARI     NL  2008  720  706  82  162         0
```

```python
win_percs = dbacks_df.apply(lambda row: calc_win_perc(row['W'], row['G']), axis=1)
print(win_percs, '\n')
```

```
## 0      0.50
## 30     0.58
## 60     0.40
## 90     0.43
## 120    0.51
## 150    0.56
## 180    0.47
## 210    0.48
## 241    0.31
## 271    0.52
## 301    0.60
## 331    0.57
## 361    0.52
## 391    0.62
## 421    0.40
## dtype: float64
```
<li>Create a new column in <code>dbacks_df</code> called <code>WP</code> that contains the win percentages you calculated in the above step.</li>

```python
# Display the first five rows of the DataFrame
print(dbacks_df.head())

# Create a win percentage Series 
```

```
##     Team League  Year   RS   RA   W    G  Playoffs
## 0    ARI     NL  2012  734  688  81  162         0
## 30   ARI     NL  2011  731  662  94  162         1
## 60   ARI     NL  2010  713  836  65  162         0
## 90   ARI     NL  2009  720  782  70  162         0
## 120  ARI     NL  2008  720  706  82  162         0
```

```python
win_percs = dbacks_df.apply(lambda row: calc_win_perc(row['W'], row['G']), axis=1)
print(win_percs, '\n')

# Append a new column to dbacks_df
```

```
## 0      0.50
## 30     0.58
## 60     0.40
## 90     0.43
## 120    0.51
## 150    0.56
## 180    0.47
## 210    0.48
## 241    0.31
## 271    0.52
## 301    0.60
## 331    0.57
## 361    0.52
## 391    0.62
## 421    0.40
## dtype: float64
```

```python
dbacks_df['WP'] = win_percs
print(dbacks_df, '\n')

# Display dbacks_df where WP is greater than 0.50
```

```
##     Team League  Year   RS   RA    W    G  Playoffs    WP
## 0    ARI     NL  2012  734  688   81  162         0  0.50
## 30   ARI     NL  2011  731  662   94  162         1  0.58
## 60   ARI     NL  2010  713  836   65  162         0  0.40
## 90   ARI     NL  2009  720  782   70  162         0  0.43
## 120  ARI     NL  2008  720  706   82  162         0  0.51
## 150  ARI     NL  2007  712  732   90  162         1  0.56
## 180  ARI     NL  2006  773  788   76  162         0  0.47
## 210  ARI     NL  2005  696  856   77  162         0  0.48
## 241  ARI     NL  2004  615  899   51  162         0  0.31
## 271  ARI     NL  2003  717  685   84  162         0  0.52
## 301  ARI     NL  2002  819  674   98  162         1  0.60
## 331  ARI     NL  2001  818  677   92  162         1  0.57
## 361  ARI     NL  2000  792  754   85  162         0  0.52
## 391  ARI     NL  1999  908  676  100  162         1  0.62
## 421  ARI     NL  1998  665  812   65  162         0  0.40
```

```python
print(dbacks_df[dbacks_df['WP'] >= 0.50])
```

```
##     Team League  Year   RS   RA    W    G  Playoffs    WP
## 0    ARI     NL  2012  734  688   81  162         0  0.50
## 30   ARI     NL  2011  731  662   94  162         1  0.58
## 120  ARI     NL  2008  720  706   82  162         0  0.51
## 150  ARI     NL  2007  712  732   90  162         1  0.56
## 271  ARI     NL  2003  717  685   84  162         0  0.52
## 301  ARI     NL  2002  819  674   98  162         1  0.60
## 331  ARI     NL  2001  818  677   92  162         1  0.57
## 361  ARI     NL  2000  792  754   85  162         0  0.52
## 391  ARI     NL  1999  908  676  100  162         1  0.62
```

<div class=""><ul>
<li>Which manager was correct in their claim?</li>
</ul></div>

- [ ] 
- [x] 
- [ ] 

<p class="">Nicely done! Using the <code>.apply()</code> method with a <code>lambda</code> function allows you to apply a function to a DataFrame without the need to write a for loop.<br><br>Sadly, the second manager was correct. In the year 2012, 2008, 2003, and 2000 the Arizona Diamondbacks had a win percentage greater than or equal to 0.50, but still <strong>did not</strong> make the playoffs.</p>

## Optimal pandas iterating



### Replacing .iloc with underlying arrays


<div class>
<p>Now that you have a better grasp on a DataFrame's internals let's update one of your previous analyses to leverage a DataFrame's underlying arrays. You'll revisit the win percentage calculations you performed row by row with the <code>.iloc</code> method:</p>
<pre><code>def calc_win_perc(wins, games_played):
    win_perc = wins / games_played
    return np.round(win_perc,2)

win_percs_list = []

for i in range(len(baseball_df)):
    row = baseball_df.iloc[i]

    wins = row['W']
    games_played = row['G']

    win_perc = calc_win_perc(wins, games_played)

    win_percs_list.append(win_perc)

baseball_df['WP'] = win_percs_list
</code></pre>
<p>Let's update this analysis to use arrays instead of the <code>.iloc</code> method. A DataFrame (<code>baseball_df</code>) has been loaded into your session.</p>
</div>

```python
# edited/added
```
<li>Use <em>the right method</em> to collect the underlying <code>'W'</code> and <code>'G'</code> arrays of <code>baseball_df</code> and pass them <strong>directly into</strong> the <code>calc_win_perc()</code> function. Store the result as a variable called <code>win_percs_np</code>.</li>

```python
# Use the W array and G array to calculate win percentages
win_percs_np = calc_win_perc(baseball_df['W'].values, baseball_df['G'].values)
```
<li>Create a new column in <code>baseball_df</code> called <code>'WP'</code> that contains the win percentages you just calculated.</li>

```python
# Use the W array and G array to calculate win percentages
win_percs_np = calc_win_perc(baseball_df['W'].values, baseball_df['G'].values)

# Append a new column to baseball_df that stores all win percentages
baseball_df['WP'] = win_percs_np

print(baseball_df.head())
```

```
##   Team League  Year   RS   RA  ...  RankPlayoffs    G   OOBP   OSLG    WP
## 0  ARI     NL  2012  734  688  ...           NaN  162  0.317  0.415  0.50
## 1  ATL     NL  2012  700  600  ...           5.0  162  0.306  0.378  0.58
## 2  BAL     AL  2012  712  705  ...           4.0  162  0.315  0.403  0.57
## 3  BOS     AL  2012  734  806  ...           NaN  162  0.331  0.428  0.43
## 4  CHC     NL  2012  613  759  ...           NaN  162  0.335  0.424  0.38
## 
## [5 rows x 16 columns]
```

<div class=""><p>Use <code>timeit</code> in <em>cell magic mode</em> <strong>within your IPython console</strong> to compare the runtimes between the old code block using <code>.iloc</code> and the new code you developed using NumPy arrays.</p>
<p><strong>Don't include the code that defines the <code>calc_win_perc()</code> function or the <code>print()</code> statements or when timing</strong>.</p>
<p>You should include <strong>eight lines of code</strong> when timing the old code block and <strong>two lines of code</strong> when timing the new code you developed. You may need to press <code>SHIFT+ENTER</code> when using <code>timeit</code> in <em>cell magic mode</em> to get to a new line within your IPython console.</p>
<p><strong>Which approach was the faster?</strong></p></div>

- [ ] <div class="dc-input-radio__text">The original code with <code>.iloc</code> is much faster than using NumPy arrays</div>
- [ ] <div class="dc-input-radio__text">The old code block with <code>.iloc</code> and the new code with NumPy arrays have similar runtimes.</div>
- [x] <div class="dc-input-radio__text">The NumPy array approach is faster than the <code>.iloc</code> approach.</div>

<p class="">Great job! You're knocking it out of the park! Using a DataFrame's underlying arrays to perform calculations can really speed up your code and yields some significant efficiency gains. Did you notice that the NumPy array approach was not just faster, but that it also used fewer lines of code and was easier to read?</p>

### Bringing it all together: Predict win percentage


<div class>
<p>A <code>pandas</code> DataFrame (<code>baseball_df</code>) has been loaded into your session. For convenience, a dictionary describing each column within <code>baseball_df</code> has been printed into your console. You can reference these descriptions throughout the exercise.</p>
<p>You'd like to attempt to <em>predict</em> a team's win percentage for a given season by using the team's total runs scored in a season (<code>'RS'</code>) and total runs allowed in a season (<code>'RA'</code>) with the following function:</p>
<pre><code>def predict_win_perc(RS, RA):
    prediction = RS ** 2 / (RS ** 2 + RA ** 2)
    return np.round(prediction, 2)
</code></pre>
<p>Let's compare the approaches you've learned to calculate a <em>predicted win percentage</em> for each season (or row) in your DataFrame.</p>
</div>

```python
# edited/added
def predict_win_perc(RS, RA):
    prediction = RS ** 2 / (RS ** 2 + RA ** 2)
    return np.round(prediction, 2)
```
<li>Use a for loop and <code>.itertuples()</code> to predict the win percentage for each row of <code>baseball_df</code> with the <code>predict_win_perc()</code> function. Save each row's predicted win percentage as <code>win_perc_pred</code> and append each to the <code>win_perc_preds_loop</code> list.</li>

```python
win_perc_preds_loop = []

# Use a loop and .itertuples() to collect each row's predicted win percentage
for row in baseball_df.itertuples():
    runs_scored = row.RS
    runs_allowed = row.RA
    win_perc_pred = predict_win_perc(runs_scored, runs_allowed)
    win_perc_preds_loop.append(win_perc_pred)
```
<li>Apply <code>predict_win_perc()</code> to each row of the <code>baseball_df</code> DataFrame using a <code>lambda</code> function. Save the predicted win percentage as <code>win_perc_preds_apply</code>.</li>

```python
win_perc_preds_loop = []

# Use a loop and .itertuples() to collect each row's predicted win percentage
for row in baseball_df.itertuples():
    runs_scored = row.RS
    runs_allowed = row.RA
    win_perc_pred = predict_win_perc(runs_scored, runs_allowed)
    win_perc_preds_loop.append(win_perc_pred)

# Apply predict_win_perc to each row of the DataFrame
win_perc_preds_apply = baseball_df.apply(lambda row: predict_win_perc(row['RS'], row['RA']), axis=1)
```
<li>Calculate the predicted win percentages by passing the underlying <code>'RS'</code> and <code>'RA'</code> <strong>arrays</strong> from <code>baseball_df</code> into <code>predict_win_perc()</code>. Save these predictions as <code>win_perc_preds_np</code>.</li>

```python
win_perc_preds_loop = []

# Use a loop and .itertuples() to collect each row's predicted win percentage
for row in baseball_df.itertuples():
    runs_scored = row.RS
    runs_allowed = row.RA
    win_perc_pred = predict_win_perc(runs_scored, runs_allowed)
    win_perc_preds_loop.append(win_perc_pred)

# Apply predict_win_perc to each row of the DataFrame
win_perc_preds_apply = baseball_df.apply(lambda row: predict_win_perc(row['RS'], row['RA']), axis=1)

# Calculate the win percentage predictions using NumPy arrays
win_perc_preds_np = predict_win_perc(baseball_df['RS'].values, baseball_df['RA'].values)
baseball_df['WP_preds'] = win_perc_preds_np
print(baseball_df.head())
```

```
##   Team League  Year   RS   RA  ...    G   OOBP   OSLG    WP  WP_preds
## 0  ARI     NL  2012  734  688  ...  162  0.317  0.415  0.50      0.53
## 1  ATL     NL  2012  700  600  ...  162  0.306  0.378  0.58      0.58
## 2  BAL     AL  2012  712  705  ...  162  0.315  0.403  0.57      0.50
## 3  BOS     AL  2012  734  806  ...  162  0.331  0.428  0.43      0.45
## 4  CHC     NL  2012  613  759  ...  162  0.335  0.424  0.38      0.39
## 
## [5 rows x 17 columns]
```

<div class=""><p>Compare runtimes <strong>within your IPython console</strong> between <strong>all three</strong> approaches used to calculate the predicted win percentages.</p>
<p>Use <strong><code>%%timeit</code></strong> (<em>cell magic mode</em>) to time the <strong>six lines of code</strong> (not including comment lines) for the <code>.itertuples()</code> approach. You may need to press <code>SHIFT+ENTER</code> after entering <code>%%timeit</code> to get to a new line within your IPython console.</p>
<p>Use <strong><code>%timeit</code></strong> (<em>line magic mode</em>) to time the <code>.apply()</code> approach and the NumPy array approach separately. Each has only <strong>one line of code</strong> (not including comment lines). </p>
<p><strong>What is the order of approaches from fastest to slowest?</strong></p></div>

- [ ] <div class="dc-input-radio__text">The <code>.apply()</code> with a <code>lambda</code> function was the <strong>fastest</strong>, followed by the <code>.itertuples()</code> approach, and the array approach was <strong>slowest</strong>.</div>
- [x] <div class="dc-input-radio__text">Using NumPy arrays was the <strong>fastest</strong> approach, followed by the <code>.itertuples()</code> approach, and the <code>.apply()</code> approach was <strong>slowest</strong>.</div>
- [ ] <div class="dc-input-radio__text">The <code>.itertuples()</code> approach was <strong>fastest</strong>, followed by the array approach, and the <code>.apply()</code> approach was <strong>slowest</strong>.</div>
- [ ] <div class="dc-input-radio__text">All three approaches had comparable runtimes.</div>

<p class="">Great job! That's a home run! You practiced using three different approaches to iterate over a <code>pandas</code> DataFrame and perform calculations. Did you notice that the <code>.itertuples()</code> approach beat the <code>.apply()</code> approach? Even though both these implementations can be useful, you should default to using a DataFrame's underlying arrays to perform calculations.<br><br>Take a look at your win percentage predictions (column <code>'WP_preds'</code>) and compare them to the actual win percentages (column <code>'WP'</code>). Not bad!<br><br>You've done a great job throughout the course! Now, you are well on your way to writing efficient Python and <code>pandas</code> code!</p>

## Congratulations!

### Congratulations!

Congratulations on completing the course! Now, you have the necessary tools to start writing efficient Python code!

### What you have learned

Over the four chapters of this course, you have learned what writing efficient code truly means, and that writing Pythonic code often yields efficient code. You've explored Python's Standard Library and practiced using built-in functions like range, enumerate, and map. You know the power of NumPy arrays and can use them for fast, efficient calculations. You're a whiz at using magic commands like %timeit and know how to profile your code with the line_profiler and memory_profiler packages. You've also applied more advanced techniques to gain efficiencies by using built-in functions like zip, built-in modules like itertools and collections, and a branch of mathematics called set theory. Finally, you explored looping patterns in Python and why they are not always the most efficient approach to solving problems. You successfully eliminated loops in your code and even learned how to efficiently iterate over pandas DataFrames.

### Well done!

Well done! It has been an absolute pleasure working with you! Thank you for taking the course, and I hope to see you again in the future!
