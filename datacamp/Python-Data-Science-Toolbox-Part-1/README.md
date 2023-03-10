<h3><a href="https://github.com/mclix85/datacamp" target="_blank">View Source Code</a></h3>

<h3>Course Description</h3>

<p class="course__description">It's time to push forward and develop your Python chops even further. There are tons of fantastic functions in Python and its library ecosystem. However, as a data scientist, you'll constantly need to write your own functions to solve problems that are dictated by your data. You will learn the art of function writing in this first Python Data Science Toolbox course. You'll come out of this course being able to write your very own custom functions, complete with multiple parameters and multiple return values, along with default arguments and variable-length arguments. You'll gain insight into scoping in Python and be able to write lambda functions and handle errors in your function writing practice. And you'll wrap up each chapter by using your new skills to write functions that analyze Twitter DataFrames.</p>


  </p>

# Writing your own functions

<p class="chapter__description">
    In this chapter, you'll learn how to write simple functions, as well as functions that accept multiple arguments and return multiple values. You'll also have the opportunity to apply these new skills to questions commonly encountered by data scientists.
  </p>
  
## User-defined functions



### Strings in Python


<div class>
<p>In the video, you learned of another standard Python datatype, <strong>strings</strong>. Recall that these represent textual data. To assign the string <code>'DataCamp'</code> to a variable <code>company</code>, you execute:</p>
<pre><code>company = 'DataCamp'
</code></pre>
<p>You've also learned to use the operations <code>+</code> and <code>\*</code> with strings. Unlike with numeric types such as ints and floats, the <code>+</code> operator <em>concatenates</em> strings together, while the <code>\*</code> concatenates multiple copies of a string together. In this exercise, you will use the <code>+</code> and <code>\*</code> operations on strings to answer the question below. Execute the following code in the shell: </p>
<pre><code>object1 = "data" + "analysis" + "visualization"
object2 = 1 * 3
object3 = "1" * 3
</code></pre>
<p>What are the values in <code>object1</code>, <code>object2</code>, and <code>object3</code>, respectively?</p>
</div>

- [ ] <code>object1</code> contains <code>"data + analysis + visualization"</code>, <code>object2</code> contains <code>"1*3"</code>, <code>object3</code> contains <code>13</code>.
- [ ] <code>object1</code> contains <code>"data+analysis+visualization"</code>, <code>object2</code> contains <code>3</code>, <code>object3</code> contains <code>"13"</code>.
- [x] <code>object1</code> contains <code>"dataanalysisvisualization"</code>, <code>object2</code> contains <code>3</code>, <code>object3</code> contains <code>"111"</code>.

<p class="">Correct!</p>

### Recapping built-in functions


<div class>
<p>In the video, Hugo briefly examined the return behavior of the built-in functions <code>print()</code> and <code>str()</code>. Here, you will use both functions and examine their return values. A variable <code>x</code> has been preloaded for this exercise. Run the code below in the console. Pay close attention to the results to answer the question that follows.</p>
<ul>
<li>Assign <code>str(x)</code> to a variable <code>y1</code>: <code>y1 = str(x)</code>
</li>
<li>Assign <code>print(x)</code> to a variable <code>y2</code>: <code>y2 = print(x)</code>
</li>
<li>Check the types of the variables <code>x</code>, <code>y1</code>, and <code>y2</code>.</li>
</ul>
<p>What are the types of <code>x</code>, <code>y1</code>, and <code>y2</code>?</p>
</div>
<div>

```python
# edited/added
x = 4.89
y1 = str(x)
y2 = print(x)
```

```
## 4.89
```

```python
type(x),type(y1),type(y2)
```

```
## (<class 'float'>, <class 'str'>, <class 'NoneType'>)
```
</div>

- [ ] They are all <code>str</code> types.
- [ ] <code>x</code> is a <code>float</code>, <code>y1</code> is an <code>float</code>, and <code>y2</code> is a <code>str</code>.</li>
- [x] <code>x</code> is a <code>float</code>, <code>y1</code> is a <code>str</code>, and <code>y2</code> is a <code>NoneType</code>.</li>
- [ ] They are all <code>NoneType</code> types.</li>

<p class="">Correct! It is important to remember that assigning a variable <code>y2</code> to a function that prints a value but does not return a value will result in that variable <code>y2</code> being of <code>type</code> <code>NoneType</code>.</p>

### Write a simple function


<div class>
<p>In the last video, Hugo described the basics of how to define a function. You will now write your own function!</p>
<p>Define a function, <code>shout()</code>, which simply prints out a string with three exclamation marks <code>'!!!'</code> at the end. The code for the <code>square()</code> function that we wrote earlier is found below. You can use it as a pattern to define <code>shout()</code>.</p>
<pre><code>def square():
    new_value = 4 ** 2
    return new_value
</code></pre>
<p>Note that the function body is indented 4 spaces already for you. Function bodies need to be indented by a consistent number of spaces and the choice of 4 is common.</p>
<p><em>This course touches on a lot of concepts you may have forgotten, so if you ever need a quick refresher, download the <a href="https://datacamp-community-prod.s3.amazonaws.com/0eff0330-e87d-4c34-88d5-73e80cb955f2">Python for Data Science Cheat Sheet</a> and keep it handy!</em></p>
</div>

<li>Complete the function header by adding the appropriate function name, <code>shout</code>.</li>
<li>In the function body, <strong>concatenate</strong> the string, <code>'congratulations'</code> with another string, <code>'!!!'</code>. Assign the result to <code>shout_word</code>.</li>
<li>Print the value of <code>shout_word</code>.</li>

<li>Call the <code>shout</code> function.</li>
<div>

```python
# Define the function shout
def shout():
    """Print a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = 'congratulations' + '!!!'

    # Print shout_word
    print(shout_word)

# Call shout
shout()
```

```
## congratulations!!!
```
</div>

<p class="">Great work!</p>

### Single-parameter functions


<div class>
<p>Congratulations! You have successfully defined <em>and</em> called your own function! That's pretty cool.</p>
<p>In the previous exercise, you defined and called the function <code>shout()</code>, which printed out a string concatenated with <code>'!!!'</code>.
You will now update <code>shout()</code> by adding a <em>parameter</em> so that it can accept and process any string <em>argument</em> passed to it. Also note that <code>shout(word)</code>, the part of the <em>header</em> that specifies the function name and parameter(s), is known as the <em>signature</em> of the function. You may encounter this term in the wild!</p>
</div>

<li>Complete the function header by adding the parameter name, <code>word</code>.</li>
<li>Assign the result of concatenating <code>word</code> with <code>'!!!'</code> to <code>shout_word</code>.</li>
<li>Print the value of <code>shout_word</code>.</li>

<li>Call the <code>shout()</code> function, passing to it the string, <code>'congratulations'</code>.</li>
<div>

```python
# Define shout with the parameter, word
def shout(word):
    """Print a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!'

    # Print shout_word
    print(shout_word)
    
# Call shout with the string 'congratulations'
shout('congratulations')
```

```
## congratulations!!!
```
</div>

<p class="">Great work!</p>

### Functions that return single values


<div class><p>You're getting very good at this! Try your hand at another modification to the <code>shout()</code> function so that it now <em>returns</em> a single value instead of printing within the function. Recall that the <code>return</code> keyword lets you return values from functions. Parts of the function <code>shout()</code>, which you wrote earlier, are shown. Returning values is generally more desirable than printing them out because, as you saw earlier, a <code>print()</code> call assigned to a variable has type <code>NoneType</code>.</p></div>

<li>In the function body, concatenate the string in <code>word</code> with <code>'!!!'</code> and assign to <code>shout_word</code>.</li>
<li>Replace the <code>print()</code> statement with the appropriate <code>return</code> statement.</li>

<li>Call the <code>shout()</code> function, passing to it the string, <code>'congratulations'</code>, and assigning the call to the variable, <code>yell</code>.</li>

<li>To check if <code>yell</code> contains the value returned by <code>shout()</code>, print the value of <code>yell</code>.</li>
<div>

```python
# Define shout with the parameter, word
def shout(word):
    """Return a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!'

    # Replace print with return
    return shout_word
  
# Pass 'congratulations' to shout: yell
yell = shout('congratulations')

# Print yell
print(yell)
```

```
## congratulations!!!
```
</div>

<p class="">Great work! Here it made sense to assign the output of <code>shout('congratulations')</code> to a variable <code>yell</code> because the function <code>shout</code> actually returns a value, it does not merely print one.</p>

## Multiple parameters and return values



### Functions with multiple parameters


<div class><p>Hugo discussed the use of multiple parameters in defining functions in the last lecture. You are now going to use what you've learned to modify the <code>shout()</code> function further. Here, you will modify <code>shout()</code> to accept two arguments. Parts of the function <code>shout()</code>, which you wrote earlier, are shown.</p></div>

<li>Modify the function header such that it accepts two parameters, <code>word1</code> and <code>word2</code>, in that order.</li>
<li>Concatenate each of <code>word1</code> and <code>word2</code> with <code>'!!!'</code> and assign to <code>shout1</code> and <code>shout2</code>, respectively.</li>
<li>Concatenate <code>shout1</code> and <code>shout2</code> together, in that order, and assign to <code>new_shout</code>.</li>

<li>Pass the strings <code>'congratulations'</code> and <code>'you'</code>, in that order, to a call to <code>shout()</code>. Assign the return value to <code>yell</code>.</li>
<div>

```python
# Define shout with parameters word1 and word2
def shout(word1, word2):
    """Concatenate strings with three exclamation marks"""
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 + '!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 + '!!!'
    
    # Concatenate shout1 with shout2: new_shout
    new_shout = shout1 + shout2

    # Return new_shout
    return new_shout
  
# Pass 'congratulations' and 'you' to shout: yell
yell = shout('congratulations', 'you')

# Print yell
print(yell)
```

```
## congratulations!!!you!!!
```
</div>

<p class="">Great work!</p>

### A brief introduction to tuples


<div class>
<p>Alongside learning about functions, you've also learned about tuples! Here, you will practice what you've learned about tuples: how to construct, unpack, and access tuple elements. Recall how Hugo unpacked the tuple <code>even_nums</code> in the video:</p>
<p><code>a, b, c = even_nums</code></p>
<p>A three-element tuple named <code>nums</code> has been preloaded for this exercise. Before completing the script, perform the following:</p>
<ul>
<li>Print out the value of <code>nums</code> in the IPython shell. Note the elements in the tuple.</li>
<li>In the IPython shell, try to change the first element of <code>nums</code> to the value <em>2</em> by doing an assignment: <code>nums[0] = 2</code>. What happens?</li>
</ul>
</div>


<li>Unpack <code>nums</code> to the variables <code>num1</code>, <code>num2</code>, and <code>num3</code>.</li>

<li>Construct a new tuple, <code>even_nums</code> composed of the same elements in <code>nums</code>, but with the 1st element replaced with the value, <em>2</em>.</li>
<div>

```python
# edited/added
nums = (3,4,6)

# Unpack nums into num1, num2, and num3
num1, num2, num3 = nums

# Construct even_nums
even_nums = (2, num2, num3)
```
</div>

<p class="">Great work!</p>

### Functions that return multiple values


<div class>
<p>In the previous exercise, you constructed tuples, assigned tuples to variables, and unpacked tuples. Here you will return multiple values from a function using tuples. Let's now update our <code>shout()</code> function to return multiple values. Instead of returning just one string, we will return two strings with the string <code>!!!</code> concatenated to each. </p>
<p>Note that the return statement <code>return x, y</code> has the same result as <code>return (x, y)</code>: the former actually packs <code>x</code> and <code>y</code> into a tuple under the hood!</p>
</div>

<li>Modify the function header such that the function name is now <code>shout_all</code>, and it accepts two parameters, <code>word1</code> and <code>word2</code>, in that order.</li>
<li>Concatenate the string <code>'!!!'</code> to each of <code>word1</code> and <code>word2</code> and assign to <code>shout1</code> and <code>shout2</code>, respectively.</li>
<li>Construct a tuple <code>shout_words</code>, composed of <code>shout1</code> and <code>shout2</code>.</li>

<li>Call <code>shout_all()</code> with the strings <code>'congratulations'</code> and <code>'you'</code> and assign the result to <code>yell1</code> and <code>yell2</code> (remember, <code>shout_all()</code> returns 2 variables!).</li>
<div>

```python
# Define shout_all with parameters word1 and word2
def shout_all(word1, word2):
    """Return a tuple of strings"""
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 + '!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 + '!!!'
    
    # Construct a tuple with shout1 and shout2: shout_words
    shout_words = (shout1, shout2)

    # Return shout_words
    return shout_words
  
# Pass 'congratulations' and 'you' to shout_all(): yell1, yell2
yell1, yell2 = shout_all('congratulations', 'you')

# Print yell1 and yell2
print(yell1)
```

```
## congratulations!!!
```

```python
print(yell2)
```

```
## you!!!
```
</div>

<p class="">Great work!</p>

## Bringing it all together



### Bringing it all together (1)


<div class>
<p>You've got your first taste of writing your own functions in the previous exercises. You've learned how to add parameters to your own function definitions, return a value or multiple values with tuples, and how to call the functions you've defined.</p>
<p>In this and the following exercise, you will bring together all these concepts and apply them to a simple data science problem. You will load a dataset and develop functionalities to extract simple insights from the data. </p>
<p>For this exercise, your goal is to recall how to load a dataset into a DataFrame. The dataset contains Twitter data and you will iterate over entries in a column to build a dictionary in which the keys are the names of languages and the values are the number of tweets in the given language. The file <code>tweets.csv</code> is available in your current directory.</p>
<p><em>Be aware that this is real data from Twitter and as such there is always a risk that it may contain profanity or other offensive content (in this exercise, and any following exercises that also use real Twitter data).</em></p>
</div>

<li>Import the pandas package with the alias <code>pd</code>.</li>

<li>Import the file <code>'tweets.csv'</code> using the pandas function <code>read_csv()</code>. Assign the resulting DataFrame to <code>df</code>.</li>

<li>Complete the <code>for</code> loop by iterating over <code>col</code>, the <code>'lang'</code> column in the DataFrame <code>df</code>.</li>
<li>Complete the bodies of the <code>if-else</code> statements in the for loop:  <strong>if</strong> the key is in the dictionary <code>langs_count</code>, add <code>1</code> to the value corresponding to this key in the dictionary, <strong>else</strong> add the key to <code>langs_count</code> and set the corresponding value to <code>1</code>. Use the loop variable <code>entry</code> in your code.</li>
<div>

```python
# Import pandas
import pandas as pd

# Import Twitter data as DataFrame: df
df = pd.read_csv('datasets/Python-Data-Science-Toolbox-Part-1/tweets.csv') # edited/added

# Initialize an empty dictionary: langs_count
langs_count = {}

# Extract column from DataFrame: col
col = df['lang']

# Iterate over lang column in DataFrame
for entry in col:

    # If the language is in langs_count, add 1
    if entry in langs_count.keys():
        langs_count[entry] += 1
    # Else add the language to langs_count, set the value to 1
    else:
        langs_count[entry] = 1

# Print the populated dictionary
print(langs_count)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```
</div>

<p class="">Great work!</p>

### Bringing it all together (2)


<div class>
<p>Great job! You've now defined the functionality for iterating over entries in a column and building a dictionary with keys the names of languages and values the number of tweets in the given language. </p>
<p>In this exercise, you will define a function with the functionality you developed in the previous exercise, return the resulting dictionary from within the function, and call the function with the appropriate arguments. </p>
<p>For your convenience, the pandas package has been imported as <code>pd</code> and the <code>'tweets.csv'</code> file has been imported into the <code>tweets_df</code> variable.</p>
</div>

<li>Define the function <code>count_entries()</code>, which has two parameters. The first parameter is <code>df</code> for the DataFrame and the second is <code>col_name</code> for the column name.</li>
<li>Complete the bodies of the <code>if-else</code> statements in the <code>for</code> loop: <strong>if</strong> the key is in the dictionary <code>langs_count</code>, add <code>1</code> to its current value, <strong>else</strong> add the key to <code>langs_count</code> and set its value to <code>1</code>. Use the loop variable <code>entry</code> in your code.</li>
<li>Return the <code>langs_count</code> dictionary from inside the <code>count_entries()</code> function.</li>

<li>Call the <code>count_entries()</code> function by passing to it <code>tweets_df</code> and the name of the column, <code>'lang'</code>. Assign the result of the call to the variable <code>result</code>.</li>
<div>

```python
# Define count_entries()
def count_entries(df, col_name):
    """Return a dictionary with counts of 
    occurrences as value for each key."""

    # Initialize an empty dictionary: langs_count
    langs_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]

    # Iterate over lang column in DataFrame
    for entry in col:

        # If the language is in langs_count, add 1
        if entry in langs_count.keys():
            langs_count[entry] += 1
        # Else add the language to langs_count, set the value to 1
        else:
            langs_count[entry] = 1

    # Return the langs_count dictionary
    return langs_count
  
# edited/added
tweets_df = pd.read_csv('datasets/Python-Data-Science-Toolbox-Part-1/tweets.csv')

# Call count_entries(): result
result = count_entries(tweets_df, 'lang')

# Print the result
print(result)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```
</div>

<p class="">Great work!</p>

# Default arguments, variable-length arguments and scope

<p class="chapter__description">
    In this chapter, you'll learn to write functions with default arguments so that the user doesn't always need to specify them, and variable-length arguments so they can pass an arbitrary number of arguments on to your functions. You'll also learn about the essential concept of scope.
  </p>
  
## Scope and user-defined functions




### Pop quiz on understanding scope


<div class>
<p>In this exercise, you will practice what you've learned about scope in functions. The variable <code>num</code> has been predefined as <code>5</code>, alongside the following function definitions:</p>
<pre><code>def func1():
    num = 3
    print(num)

def func2():
    global num
    double_num = num * 2
    num = 6
    print(double_num)
</code></pre>
<p>Try calling <code>func1()</code> and <code>func2()</code> in the shell, then answer the following questions:</p>
<ul>
<li>What are the values printed out when you call <code>func1()</code> and <code>func2()</code>? </li>
<li>What is the value of <code>num</code> in the global scope after calling <code>func1()</code> and <code>func2()</code>?</li>
</ul>
</div>

- [ ] <code>func1()</code> prints out <code>3</code>, <code>func2()</code> prints out <code>6</code>, and the value of <code>num</code> in the global scope is <code>3</code>.
- [ ] <code>func1()</code> prints out <code>3</code>, <code>func2()</code> prints out <code>3</code>, and the value of <code>num</code> in the global scope is <code>3</code>.
- [ ] <code>func1()</code> prints out <code>3</code>, <code>func2()</code> prints out <code>10</code>, and the value of <code>num</code> in the global scope is <code>10</code>.
- [x] <code>func1()</code> prints out <code>3</code>, <code>func2()</code> prints out <code>10</code>, and the value of <code>num</code> in the global scope is <code>6</code>.

<p class="">Correct!</p>

### The keyword global


<div class><p>Let's work more on your mastery of scope. In this exercise, you will use the keyword <code>global</code> within a function to alter the value of a variable defined in the global scope.</p></div>

<li>Use the keyword <code>global</code> to alter the object <code>team</code> in the global scope.</li>
<li>Change the value of <code>team</code> in the global scope to the string <code>"justice league"</code>. Assign the result to <code>team</code>.</li>

<li>Hit the Submit button to see how executing your newly defined function <code>change_team()</code> changes the value of the name <code>team</code>!</li>
<div>

```python
# Create a string: team
team = "teen titans"

# Define change_team()
def change_team():
    """Change the value of the global variable team."""

    # Use team in global scope
    global team

    # Change the value of team in global: team
    team = "justice league"
    
# Print team
print(team)
```

```
## teen titans
```
</div>

<div>

```python
# Call change_team()
change_team()

# Print team
print(team)
```

```
## justice league
```
</div>

<p class="">Great work!</p>

### Python's built-in scope


<div class><p>Here you're going to check out Python's built-in scope, which is really just a built-in module called <code>builtins</code>. However, to query <code>builtins</code>, you'll need to <code>import builtins</code> 'because the name builtins is not itself built in???No, I???m serious!' (<a href="http://shop.oreilly.com/product/0636920028154.do"><em>Learning Python</em>, 5th edition</a>, Mark Lutz).
After executing <code>import builtins</code> in the IPython Shell, execute <code>dir(builtins)</code> to print a list of all the names in the module <code>builtins</code>. Have a look and you'll see a bunch of names that you'll recognize! Which of the following names is NOT in the module builtins?</p></div>

- [ ] 'sum'
- [ ] 'range'
- [x] 'array'
- [ ] 'tuple'

<p class="">You got it!</p>

## Nested functions



### Nested Functions I


<div class>
<p>You've learned in the last video about nesting functions within functions. One reason why you'd like to do this is to avoid writing out the same computations within functions repeatedly. There's nothing new about defining nested functions: you simply define it as you would a regular function with <code>def</code> and embed it inside another function!</p>
<p>In this exercise, inside a function <code>three_shouts()</code>, you will define a nested function <code>inner()</code> that concatenates a string object with <code>!!!</code>. <code>three_shouts()</code> then returns a tuple of three elements, each a string concatenated with <code>!!!</code> using <code>inner()</code>. Go for it!</p>
</div>

<li>Complete the function header of the nested function with the function name <code>inner()</code> and a single parameter <code>word</code>.</li>
<li>Complete the return value: each element of the tuple should be a call to <code>inner()</code>, passing in the parameters from <code>three_shouts()</code> as arguments to each call.</li>
<div>

```python
# Define three_shouts
def three_shouts(word1, word2, word3):
    """Returns a tuple of strings
    concatenated with '!!!'."""

    # Define inner
    def inner(word):
        """Returns a string concatenated with '!!!'."""
        return word + '!!!'

    # Return a tuple of strings
    return (inner(word1), inner(word2), inner(word3))

# Call three_shouts() and print
print(three_shouts('a', 'b', 'c'))
```

```
## ('a!!!', 'b!!!', 'c!!!')
```
</div>

<p class="">Great work!</p>

### Nested Functions II


<div class>
<p>Great job, you've just nested a function within another function. One other pretty cool reason for nesting functions is the idea of a <strong>closure</strong>. This means that the nested or inner function remembers the state of its enclosing scope when called. Thus, anything defined locally in the enclosing scope is available to the inner function even when the outer function has finished execution.</p>
<p>Let's move forward then! In this exercise, you will complete the definition of the inner function <code>inner_echo()</code> and then call <code>echo()</code> a couple of times, each with a different argument. Complete the exercise and see what the output will be!</p>
</div>

<li>Complete the function header of the inner function with the function name <code>inner_echo()</code> and a single parameter <code>word1</code>.</li>
<li>Complete the function <code>echo()</code> so that it returns <code>inner_echo</code>.</li>

<li>We have called <code>echo()</code>, passing 2 as an argument, and assigned the resulting function to <code>twice</code>. Your job is to call <code>echo()</code>, passing 3 as an argument. Assign the resulting function to <code>thrice</code>.</li>

<li>Hit Submit to call <code>twice()</code> and <code>thrice()</code> and print the results.</li>
<div>

```python
# Define echo
def echo(n):
    """Return the inner_echo function."""

    # Define inner_echo
    def inner_echo(word1):
        """Concatenate n copies of word1."""
        echo_word = word1 * n
        return echo_word

    # Return inner_echo
    return inner_echo
  
# Call echo: twice
twice = echo(2)

# Call echo: thrice
thrice = echo(3)

# Call twice() and thrice() then print
print(twice('hello'), thrice('hello'))
```

```
## hellohello hellohellohello
```
</div>

<p class="">Great work!</p>

### The keyword nonlocal and nested functions


<div class><p>Let's once again work further on your mastery of scope! In this exercise, you will use the keyword <code>nonlocal</code> within a nested function to alter the value of a variable defined in the enclosing scope.</p></div>

<li>Assign to <code>echo_word</code> the string <code>word</code>, concatenated with itself.</li>
<li>Use the keyword <code>nonlocal</code> to alter the value of <code>echo_word</code> in the enclosing scope.</li>
<li>Alter <code>echo_word</code> to <code>echo_word</code> concatenated with '!!!'.</li>

<li>Call the function <code>echo_shout()</code>,  passing it a single argument 'hello'.</li>
<div>

```python
# Define echo_shout()
def echo_shout(word):
    """Change the value of a nonlocal variable"""
    
    # Concatenate word with itself: echo_word
    echo_word = word*2
    
    # Print echo_word
    print(echo_word)
    
    # Define inner function shout()
    def shout():
        """Alter a variable in the enclosing scope"""
        
        # Use echo_word in nonlocal scope
        nonlocal echo_word
        
        # Change echo_word to echo_word concatenated with '!!!'
        echo_word = echo_word + '!!!'
    
    # Call function shout()
    shout()
    
    # Print echo_word
    print(echo_word)
    
# Call function echo_shout() with argument 'hello'
echo_shout('hello')
```

```
## hellohello
## hellohello!!!
```
</div>

<p class="">Quite something, that <code>nonlocal</code> keyword!</p>

## Default and flexible arguments



### Functions with one default argument


<div class><p>In the previous chapter, you've learned to define functions with more than one parameter and then calling those functions by passing the required number of arguments. In the last video, Hugo built on this idea by showing you how to define functions with default arguments. You will practice that skill in this exercise by writing a function that uses a default argument and then calling the function a couple of times.</p></div>

<li>Complete the function header with the function name <code>shout_echo</code>. It accepts an argument <code>word1</code> and a default argument <code>echo</code> with default value <code>1</code>, in that order.</li>
<li>Use the <code>*</code> operator to concatenate <code>echo</code> copies of <code>word1</code>. Assign the result to <code>echo_word</code>.</li>

<li>Call <code>shout_echo()</code> with just the string, <code>"Hey"</code>. Assign the result to <code>no_echo</code>.</li>

<li>Call <code>shout_echo()</code> with the string <code>"Hey"</code> and the value <code>5</code> for the default argument, <code>echo</code>. Assign the result to <code>with_echo</code>.</li>
<div>

```python
# Define shout_echo
def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
     exclamation marks at the end of the string."""

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'

    # Return shout_word
    return shout_word
  
# Call shout_echo() with "Hey": no_echo
no_echo = shout_echo("Hey")

# Call shout_echo() with "Hey" and echo=5: with_echo
with_echo = shout_echo("Hey", echo=5)

# Print no_echo and with_echo
print(no_echo)
```

```
## Hey!!!
```

```python
print(with_echo)
```

```
## HeyHeyHeyHeyHey!!!
```
</div>

<p class="">Great work!</p>

### Functions with multiple default arguments


<div class>
<p>You've now defined a function that uses a default argument - don't stop there just yet! You will now try your hand at defining a function with more than one default argument and then calling this function in various ways. </p>
<p>After defining the function, you will call it by supplying values to <em>all</em> the default arguments of the function. Additionally, you will call the function by not passing a value to one of the default arguments - see how that changes the output of your function!</p>
</div>

<li>Complete the function header with the function name <code>shout_echo</code>. It accepts an argument <code>word1</code>, a default argument <code>echo</code> with default value <code>1</code> and a default argument <code>intense</code> with default value <code>False</code>, in that order.</li>
<li>In the body of the <code>if</code> statement, make the string object <code>echo_word</code> upper case by applying the method <code>.upper()</code> on it.</li>

<li>Call <code>shout_echo()</code> with the string, <code>"Hey"</code>, the value <code>5</code> for <code>echo</code> and the value <code>True</code> for <code>intense</code>. Assign the result to <code>with_big_echo</code>.</li>

<li>Call <code>shout_echo()</code> with the string <code>"Hey"</code> and the value <code>True</code> for <code>intense</code>. Assign the result to <code>big_no_echo</code>.</li>
<div>

```python
# Define shout_echo
def shout_echo(word1, echo=1, intense=False):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Make echo_word uppercase if intense is True
    if intense is True:
        # Make uppercase and concatenate '!!!': echo_word_new
        echo_word_new = echo_word.upper() + '!!!'
    else:
        # Concatenate '!!!' to echo_word: echo_word_new
        echo_word_new = echo_word + '!!!'

    # Return echo_word_new
    return echo_word_new
  
# Call shout_echo() with "Hey", echo=5 and intense=True: with_big_echo
with_big_echo = shout_echo("Hey", echo=5, intense=True)

# Call shout_echo() with "Hey" and intense=True: big_no_echo
big_no_echo = shout_echo("Hey", intense=True)

# Print with_big_echo and big_no_echo
print(with_big_echo)
```

```
## HEYHEYHEYHEYHEY!!!
```

```python
print(big_no_echo)
```

```
## HEY!!!
```
</div>

<p class="">Great work!</p>

### Functions with variable-length arguments (\*args)


<div class>
<p>Flexible arguments enable you to pass a variable number of arguments to a function. In this exercise, you will practice defining a function that accepts a variable number of string arguments.</p>
<p>The function you will define is <code>gibberish()</code> which can accept a variable number of string values. Its return value is a single string composed of all the string arguments concatenated together in the order they were passed to the function call. You will call the function with a single string argument and see how the output changes with another call using more than one string argument. Recall from the previous video that, within the function definition, <code>args</code> is a tuple.</p>
</div>

<li>Complete the function header with the function name <code>gibberish</code>. It accepts a single flexible argument <code>\*args</code>.</li>
<li>Initialize a variable <code>hodgepodge</code> to an empty string.</li>
<li>Return the variable <code>hodgepodge</code> at the end of the function body.</li>

<li>Call <code>gibberish()</code> with the single string, <code>"luke"</code>. Assign the result to <code>one_word</code>.</li>

<li>Hit the Submit button to call <code>gibberish()</code> with multiple arguments and to print the value to the Shell.</li>
<div>

```python
# Define gibberish
def gibberish(*args):
    """Concatenate strings in *args together."""

    # Initialize an empty string: hodgepodge
    hodgepodge = ''

    # Concatenate the strings in args
    for word in args:
        hodgepodge += word

    # Return hodgepodge
    return hodgepodge
  
# Call gibberish() with one string: one_word
one_word = gibberish("luke")

# Call gibberish() with five strings: many_words
many_words = gibberish("luke", "leia", "han", "obi", "darth")

# Print one_word and many_words
print(one_word)
```

```
## luke
```

```python
print(many_words)
```

```
## lukeleiahanobidarth
```
</div>

<p class="">Great work!</p>

### Functions with variable-length keyword arguments (\*\*kwargs)


<div class>
<p>Let's push further on what you've learned about flexible arguments - you've used <code>\*args</code>, you're now going to use <code>\*\*kwargs</code>! What makes <code>**kwargs</code> different is that it allows you to pass a variable number of <em>keyword arguments</em> to functions. Recall from the previous video that, within the function definition, <code>kwargs</code> is a dictionary.</p>
<p>To understand this idea better, you're going to use <code>\*\*kwargs</code> in this exercise to define a function that accepts a variable number of keyword arguments. The function simulates a simple status report system that prints out the status of a character in a movie.</p>
</div>

<li>Complete the function header with the function name <code>report_status</code>. It accepts a single flexible argument <code>\*\*kwargs</code>.</li>
<li>Iterate over the key-value pairs of <code>kwargs</code> to print out the keys and values, separated by a colon ':'.</li>

<li>In the first call to <code>report_status()</code>, pass the following keyword-value pairs: <code>name="luke"</code>, <code>affiliation="jedi"</code> and <code>status="missing"</code>.</li>

<li>In the second call to <code>report_status()</code>, pass the following keyword-value pairs: <code>name="anakin"</code>, <code>affiliation="sith lord"</code> and <code>status="deceased"</code>.</li>
<div>

```python
# Define report_status
def report_status(**kwargs):
    """Print out the status of a movie character."""

    print("\nBEGIN: REPORT\n")

    # Iterate over the key-value pairs of kwargs
    for key, value in kwargs.items():
        # Print out the keys and values, separated by a colon ':'
        print(key + ": " + value)

    print("\nEND REPORT")
    
# First call to report_status()
report_status(name="luke", affiliation="jedi", status="missing")
```

```
## 
## BEGIN: REPORT
## 
## name: luke
## affiliation: jedi
## status: missing
## 
## END REPORT
```
</div>
<div>

```python
# Second call to report_status()
report_status(name="anakin", affiliation="sith lord", status="deceased")
```

```
## 
## BEGIN: REPORT
## 
## name: anakin
## affiliation: sith lord
## status: deceased
## 
## END REPORT
```
</div>

<div class="dc-completed__message"><p class="">Great work!</p></div>

## Bringing it all together



### Bringing it all together (1)


<div class>
<p>Recall the <em>Bringing it all together</em> exercise in the previous chapter where you did a simple Twitter analysis by developing a function that counts how many tweets are in certain languages. The output of your function was a dictionary that had the language as the <em>keys</em> and the counts of tweets in that language as the <em>value</em>.</p>
<p>In this exercise, we will generalize the Twitter language analysis that you did in the previous chapter. You will do that by including a <strong>default argument</strong> that takes a column name. </p>
<p>For your convenience, <code>pandas</code> has been imported as <code>pd</code> and the <code>'tweets.csv'</code> file has been imported into the DataFrame <code>tweets_df</code>. Parts of the code from your previous work are also provided.</p>
</div>

<li>Complete the function header by supplying the parameter for a DataFrame <code>df</code> and the parameter <code>col_name</code> with a default value of <code>'lang'</code> for the DataFrame column name.</li>

<li>Call <code>count_entries()</code> by passing the <code>tweets_df</code> DataFrame and the column name <code>'lang'</code>. Assign the result to <code>result1</code>. Note that since <code>'lang'</code> is the default value of the <code>col_name</code> parameter, you don't have to specify it here.</li>

<li>Call <code>count_entries()</code> by passing the <code>tweets_df</code> DataFrame and the column name <code>'source'</code>. Assign the result to <code>result2</code>.</li>
<div>

```python
# Define count_entries()
def count_entries(df, col_name='lang'):
    """Return a dictionary with counts of
    occurrences as value for each key."""

    # Initialize an empty dictionary: cols_count
    cols_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]

    # Iterate over the column in DataFrame
    for entry in col:

        # If entry is in cols_count, add 1
        if entry in cols_count.keys():
            cols_count[entry] += 1

        # Else add the entry to cols_count, set the value to 1
        else:
            cols_count[entry] = 1

    # Return the cols_count dictionary
    return cols_count
  
# Call count_entries(): result1
result1 = count_entries(tweets_df, col_name='lang')

# Call count_entries(): result2
result2 = count_entries(tweets_df, col_name='source')

# Print result1 and result2
print(result1)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```

```python
print(result2)
```

```
## {'<a href="http://twitter.com" rel="nofollow">Twitter Web Client</a>': 24, '<a href="http://www.facebook.com/twitter" rel="nofollow">Facebook</a>': 1, '<a href="http://twitter.com/download/android" rel="nofollow">Twitter for Android</a>': 26, '<a href="http://twitter.com/download/iphone" rel="nofollow">Twitter for iPhone</a>': 33, '<a href="http://www.twitter.com" rel="nofollow">Twitter for BlackBerry</a>': 2, '<a href="http://www.google.com/" rel="nofollow">Google</a>': 2, '<a href="http://twitter.com/#!/download/ipad" rel="nofollow">Twitter for iPad</a>': 6, '<a href="http://linkis.com" rel="nofollow">Linkis.com</a>': 2, '<a href="http://rutracker.org/forum/viewforum.php?f=93" rel="nofollow">newzlasz</a>': 2, '<a href="http://ifttt.com" rel="nofollow">IFTTT</a>': 1, '<a href="http://www.myplume.com/" rel="nofollow">Plume\xa0for\xa0Android</a>': 1}
```
</div>

<p class="">Great work!</p>

### Bringing it all together (2)


<div class>
<p>Wow, you've just generalized your Twitter language analysis that you did in the previous chapter to include a default argument for the column name. You're now going to generalize this function one step further by allowing the user to pass it a flexible argument, that is, in this case, as many column names as the user would like!</p>
<p>Once again, for your convenience, <code>pandas</code> has been imported as <code>pd</code> and the <code>'tweets.csv'</code> file has been imported into the DataFrame <code>tweets_df</code>. Parts of the code from your previous work are also provided.</p>
</div>

<li>Complete the function header by supplying the parameter for the DataFrame <code>df</code> and the flexible argument <code>*args</code>.</li>
<li>Complete the <code>for</code> loop within the function definition so that the loop occurs over the tuple <code>args</code>.</li>

<li>Call <code>count_entries()</code> by passing the <code>tweets_df</code> DataFrame and the column name <code>'lang'</code>. Assign the result to <code>result1</code>.</li>

<li>Call <code>count_entries()</code> by passing the <code>tweets_df</code> DataFrame and the column names <code>'lang'</code> and <code>'source'</code>. Assign the result to <code>result2</code>.</li>
<div>

```python
# Define count_entries()
def count_entries(df, *args):
    """Return a dictionary with counts of
    occurrences as value for each key."""
    
    #Initialize an empty dictionary: cols_count
    cols_count = {}
    
    # Iterate over column names in args
    for col_name in args:
    
        # Extract column from DataFrame: col
        col = df[col_name]
    
        # Iterate over the column in DataFrame
        for entry in col:
    
            # If entry is in cols_count, add 1
            if entry in cols_count.keys():
                cols_count[entry] += 1
    
            # Else add the entry to cols_count, set the value to 1
            else:
                cols_count[entry] = 1

    # Return the cols_count dictionary
    return cols_count
  
# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang')

# Call count_entries(): result2
result2 = count_entries(tweets_df, 'lang', 'source')

# Print result1 and result2
print(result1)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```

```python
print(result2)
```

```
## {'en': 97, 'et': 1, 'und': 2, '<a href="http://twitter.com" rel="nofollow">Twitter Web Client</a>': 24, '<a href="http://www.facebook.com/twitter" rel="nofollow">Facebook</a>': 1, '<a href="http://twitter.com/download/android" rel="nofollow">Twitter for Android</a>': 26, '<a href="http://twitter.com/download/iphone" rel="nofollow">Twitter for iPhone</a>': 33, '<a href="http://www.twitter.com" rel="nofollow">Twitter for BlackBerry</a>': 2, '<a href="http://www.google.com/" rel="nofollow">Google</a>': 2, '<a href="http://twitter.com/#!/download/ipad" rel="nofollow">Twitter for iPad</a>': 6, '<a href="http://linkis.com" rel="nofollow">Linkis.com</a>': 2, '<a href="http://rutracker.org/forum/viewforum.php?f=93" rel="nofollow">newzlasz</a>': 2, '<a href="http://ifttt.com" rel="nofollow">IFTTT</a>': 1, '<a href="http://www.myplume.com/" rel="nofollow">Plume\xa0for\xa0Android</a>': 1}
```
</div>

<p class="">Great work!</p>

# Lambda functions and error-handling

<p class="chapter__description">
    Learn about lambda functions, which allow you to write functions quickly and on the fly. You'll also practice handling errors in your functions, which is an essential skill. Then, apply your new skills to answer data science questions.
  </p>
  
## Lambda functions



### Pop quiz on lambda functions


<div class>
<p>In this exercise, you will practice writing a simple lambda function and calling this function. Recall what you know about lambda functions and answer the following questions:</p>
<ul>
<li>How would you write a lambda function <code>add_bangs</code> that adds three exclamation points <code>'!!!'</code> to the end of a string <code>a</code>? </li>
<li>How would you call <code>add_bangs</code> with the argument <code>'hello'</code>?</li>
</ul>
<p>You may use the IPython shell to test your code.</p>
</div>

- [ ] The lambda function definition is: <code>add_bangs = (a + '!!!')</code>, and the function call is: <code>add_bangs('hello')</code>.
- [x] The lambda function definition is: <code>add_bangs = (lambda a: a + '!!!')</code>, and the function call is: <code>add_bangs('hello')</code>.
- [ ] The lambda function definition is: <code>(lambda a: a + '!!!') = add_bangs</code>, and the function call is: <code>add_bangs('hello')</code>.

<p class="">Correct!</p>

### Writing a lambda function you already know


<div class>
<p>Some function definitions are simple enough that they can be converted to a lambda function. By doing this, you write less lines of code, which is pretty awesome and will come in handy, especially when you're writing and maintaining big programs. In this exercise, you will use what you know about lambda functions to convert a function that does a simple task into a lambda function. Take a look at this function definition:</p>
<pre><code>def echo_word(word1, echo):
    """Concatenate echo copies of word1."""
    words = word1 * echo
    return words
</code></pre>
<p>The function <code>echo_word</code> takes 2 parameters: a string value, <code>word1</code> and an integer value, <code>echo</code>. It returns a string that is a concatenation of <code>echo</code> copies of <code>word1</code>. Your task is to convert this simple function into a lambda function.</p>
</div>

<li>Define the lambda function <code>echo_word</code> using the variables <code>word1</code> and <code>echo</code>. Replicate what the original function definition for <code>echo_word()</code> does above.</li>

<li>Call <code>echo_word()</code> with the string argument <code>'hey'</code> and the value <code>5</code>, in that order. Assign the call to <code>result</code>.</li>
<div>

```python
# Define echo_word as a lambda function: echo_word
echo_word = (lambda word1, echo: word1 * echo)

# Call echo_word: result
result = echo_word('hey', 5)

# Print result
print(result)
```

```
## heyheyheyheyhey
```
</div>

<p class="">Great work!</p>

### Map() and lambda functions


<div class>
<p>So far, you've used lambda functions to write short, simple functions as well as to redefine functions with simple functionality. The best use case for lambda functions, however, are for when you want these simple functionalities to be anonymously embedded within larger expressions. What that means is that the functionality is not stored in the environment, unlike a function defined with <code>def</code>. To understand this idea better, you will use a lambda function in the context of the <code>map()</code> function.</p>
<p>Recall from the video that <code>map()</code> applies a function over an object, such as a list. Here, you can use lambda functions to define the function that <code>map()</code> will use to process the object. For example:</p>
<pre><code>nums = [2, 4, 6, 8, 10]

result = map(lambda a: a ** 2, nums)
</code></pre>
<p>You can see here that a lambda function, which raises a value <code>a</code> to the power of 2, is passed to <code>map()</code> alongside a list of numbers, <code>nums</code>. The <em>map object</em> that results from the call to <code>map()</code> is stored in <code>result</code>. You will now practice the use of lambda functions with <code>map()</code>. For this exercise, you will map the functionality of the <code>add_bangs()</code> function you defined in previous exercises over a list of strings.</p>
</div>

<li>In the <code>map()</code> call, pass a lambda function that concatenates the string <code>'!!!'</code> to a string <code>item</code>; also pass the list of strings, <code>spells</code>. Assign the resulting map object to <code>shout_spells</code>.</li>

<li>Convert <code>shout_spells</code> to a list and print out the list.</li>
<div>

```python
# Create a list of strings: spells
spells = ['protego', 'accio', 'expecto patronum', 'legilimens']

# Use map() to apply a lambda function over spells: shout_spells
shout_spells = map(lambda item: item + '!!!', spells)

# Convert shout_spells to a list: shout_spells_list
shout_spells_list = list(shout_spells)

# Print the result
print(shout_spells_list)
```

```
## ['protego!!!', 'accio!!!', 'expecto patronum!!!', 'legilimens!!!']
```
</div>

<p class="">Great work!</p>

### Filter() and lambda functions


<div class>
<p>In the previous exercise, you used lambda functions to anonymously embed an operation within <code>map()</code>. You will practice this again in this exercise by using a lambda function with <code>filter()</code>, which may be new to you! The function <code>filter()</code> offers a way to filter out elements from a list that don't satisfy certain criteria.</p>
<p>Your goal in this exercise is to use <code>filter()</code> to create, from an input list of strings, a new list that contains only strings that have more than 6 characters.</p>
</div>

<li>In the <code>filter()</code> call, pass a lambda function and the list of strings, <code>fellowship</code>. The lambda function should check if the number of characters in a string <code>member</code> is greater than 6; use the <code>len()</code> function to do this. Assign the resulting filter object to <code>result</code>.</li>

<li>Convert <code>result</code> to a list and print out the list.</li>
<div>

```python
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'pippin', 'aragorn', 'boromir', 'legolas', 'gimli', 'gandalf']

# Use filter() to apply a lambda function over fellowship: result
result = filter(lambda member: len(member) > 6, fellowship)

# Convert result to a list: result_list
result_list = list(result)

# Print result_list
print(result_list)
```

```
## ['samwise', 'aragorn', 'boromir', 'legolas', 'gandalf']
```
</div>

<p class="">Great work!</p>

### Reduce() and lambda functions


<div class>
<p>You're getting very good at using lambda functions! Here's one more function to add to your repertoire of skills. The <code>reduce()</code> function is useful for performing some computation on a list and, unlike <code>map()</code> and <code>filter()</code>, returns a single value as a result. To use <code>reduce()</code>, you must import it from the <code>functools</code> module.</p>
<p>Remember <code>gibberish()</code> from a few exercises back?</p>
<pre><code># Define gibberish
def gibberish(*args):
    """Concatenate strings in *args together."""
    hodgepodge = ''
    for word in args:
        hodgepodge += word
    return hodgepodge
</code></pre>
<p><code>gibberish()</code> simply takes a list of strings as an argument and returns, as a single-value result, the concatenation of all of these strings. In this exercise, you will replicate this functionality by using <code>reduce()</code> and a lambda function that concatenates strings together.</p>
</div>

<li>Import the <code>reduce</code> function from the <code>functools</code> module.</li>

<li>In the <code>reduce()</code> call, pass a lambda function that takes two string arguments <code>item1</code> and <code>item2</code> and concatenates them; also pass the list of strings, <code>stark</code>. Assign the result to <code>result</code>. The first argument to <code>reduce()</code> should be the lambda function and the second argument is the list <code>stark</code>.</li>
<div>

```python
# Import reduce from functools
from functools import reduce

# Create a list of strings: stark
stark = ['robb', 'sansa', 'arya', 'brandon', 'rickon']

# Use reduce() to apply a lambda function over stark: result
result = reduce(lambda item1, item2: item1 + item2, stark)

# Print the result
print(result)
```

```
## robbsansaaryabrandonrickon
```
</div>

<p class="">Great work!</p>

## Introduction to error handling



### Pop quiz about errors


<div class>
<p>In the video, Hugo talked about how errors happen when functions are supplied arguments that they are unable to work with. In this exercise, you will identify which function call raises an error and what type of error is raised.</p>
<p>Take a look at the following function calls to <code>len()</code>:</p>
<pre><code>len('There is a beast in every man and it stirs when you put a sword in his hand.')

len(['robb', 'sansa', 'arya', 'eddard', 'jon'])

len(525600)

len(('jaime', 'cersei', 'tywin', 'tyrion', 'joffrey'))
</code></pre>
<p>Which of the function calls raises an error and what type of error is raised?</p>
</div>

- [ ] The call <code>len('There is a beast in every man and it stirs when you put a sword in his hand.')</code> raises a <code>TypeError</code>.
- [ ] The call <code>len(['robb', 'sansa', 'arya', 'eddard', 'jon'])</code> raises an <code>IndexError</code>.
- [x] The call <code>len(525600)</code> raises a <code>TypeError</code>.
- [ ] The call <code>len(('jaime', 'cersei', 'tywin', 'tyrion', 'joffrey'))</code> raises a <code>NameError</code>.

<p class="">Correct!</p>

### Error handling with try-except


<div class>
<p>A good practice in writing your own functions is also anticipating the ways in which other people (or yourself, if you accidentally misuse your own function) might use the function you defined. </p>
<p>As in the previous exercise, you saw that the <code>len()</code> function is able to handle input arguments such as strings, lists, and tuples, but not int type ones and raises an appropriate error and error message when it encounters invalid input arguments. One way of doing this is through exception handling with the <code>try-except</code> block. </p>
<p>In this exercise, you will define a function as well as use a <code>try-except</code> block for handling cases when incorrect input arguments are passed to the function.</p>
<p>Recall the <code>shout_echo()</code> function you defined in previous exercises; parts of the function definition are provided in the sample code. Your goal is to complete the exception handling code in the function definition and provide an appropriate error message when raising an error.</p>
</div>

<li>Initialize the variables <code>echo_word</code> and <code>shout_words</code> to empty strings.</li>
<li>Add the keywords <code>try</code> and <code>except</code> in the appropriate locations for the exception handling block.</li>
<li>Use the <code>*</code> operator to concatenate <code>echo</code> copies of <code>word1</code>. Assign the result to <code>echo_word</code>.</li>
<li>Concatenate the string <code>'!!!'</code> to <code>echo_word</code>. Assign the result to <code>shout_words</code>.</li>
<div>

```python
# Define shout_echo
def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Initialize empty strings: echo_word, shout_words
    echo_word = ''
    shout_words = ''

    # Add exception handling with try-except
    try:
        # Concatenate echo copies of word1 using *: echo_word
        echo_word = word1 * echo

        # Concatenate '!!!' to echo_word: shout_words
        shout_words = echo_word + '!!!'
    except:
        # Print error message
        print("word1 must be a string and echo must be an integer.")

    # Return shout_words
    return shout_words

# Call shout_echo
shout_echo("particle", echo="accelerator")
```

```
## word1 must be a string and echo must be an integer.
## ''
```
</div>

<p class="">Great work!</p>

### Error handling by raising an error


<div class>
<p>Another way to raise an error is by using <code>raise</code>. In this exercise, you will add a <code>raise</code> statement to the <code>shout_echo()</code> function you defined before to raise an error message when the value supplied by the user to the <code>echo</code> argument is less than 0.</p>
<p>The call to <code>shout_echo()</code> uses valid argument values. To test and see how the <code>raise</code> statement works, simply change the value for the <code>echo</code> argument to a <em>negative</em> value. Don't forget to change it back to valid values to move on to the next exercise!</p>
</div>

<li>Complete the <code>if</code> statement by checking if the value of <code>echo</code> is <em>less than</em> 0.</li>
<li>In the body of the <code>if</code> statement, add a <code>raise</code> statement that raises a <code>ValueError</code> with message <code>'echo must be greater than or equal to 0'</code> when the value supplied by the user to <code>echo</code> is less than 0.</li>
<div>

```python
# Define shout_echo
def shout_echo(word1, echo=1):
    """Concatenate echo copies of word1 and three
    exclamation marks at the end of the string."""

    # Raise an error with raise
    if echo < 0:
        raise ValueError('echo must be greater than or equal to 0')

    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo

    # Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'

    # Return shout_word
    return shout_word

# Call shout_echo
shout_echo("particle", echo=5)
```

```
## 'particleparticleparticleparticleparticle!!!'
```
</div>

<p class="">Great work!</p>

## Bringing it all together



### Bringing it all together (1)


<div class>
<p>This is awesome! You have now learned how to write anonymous functions using <code>lambda</code>, how to pass lambda functions as arguments to other functions such as <code>map()</code>, <code>filter()</code>, and <code>reduce()</code>, as well as how to write errors and output custom error messages within your functions. You will now put together these learnings to good use by working with a Twitter dataset. Before practicing your new error handling skills; in this exercise, you will write a lambda function and use <code>filter()</code> to select retweets, that is, tweets that begin with the string <code>'RT'</code>.</p>
<p>To help you accomplish this, the Twitter data has been imported into the DataFrame, <code>tweets_df</code>. Go for it!</p>
</div>

<li>In the <code>filter()</code> call, pass a lambda function and the sequence of tweets as strings, <code>tweets_df['text']</code>. The lambda function should check if the first 2 characters in a tweet <code>x</code> are 'RT'. Assign the resulting filter object to <code>result</code>.  To get the first 2 characters in a tweet <code>x</code>, use <code>x[0:2]</code>. To check equality, use a Boolean filter with <code>==</code>.</li>

<li>Convert <code>result</code> to a list and print out the list.</li>
<div>

```python
# Select retweets from the Twitter DataFrame: result
result = filter(lambda x: x[0:2] == 'RT', tweets_df['text'])

# Create list from filter object result: res_list
res_list = list(result)

# Print all retweets in res_list
for tweet in res_list:
    print(tweet)
```

```
## RT @bpolitics: .@krollbondrating's Christopher Whalen says Clinton is the weakest Dem candidate in 50 years https://t.co/pLk7rvoRSn https:/???
## RT @HeidiAlpine: @dmartosko Cruz video found.....racing from the scene.... #cruzsexscandal https://t.co/zuAPZfQDk3
## RT @AlanLohner: The anti-American D.C. elites despise Trump for his America-first foreign policy. Trump threatens their gravy train. https:???
## RT @BIackPplTweets: Young Donald trump meets his neighbor  https://t.co/RFlu17Z1eE
## RT @trumpresearch: @WaitingInBagdad @thehill Trump supporters have selective amnisia.
## RT @HouseCracka: 29,000+ PEOPLE WATCHING TRUMP LIVE ON ONE STREAM!!!
## 
## https://t.co/7QCFz9ehNe
## RT @urfavandtrump: RT for Brendon Urie
## Fav for Donald Trump https://t.co/PZ5vS94lOg
## RT @trapgrampa: This is how I see #Trump every time he speaks. https://t.co/fYSiHNS0nT
## RT @trumpresearch: @WaitingInBagdad @thehill Trump supporters have selective amnisia.
## RT @Pjw20161951: NO KIDDING: #SleazyDonald just attacked Scott Walker for NOT RAISING TAXES in WI! #LyinTrump
## #NeverTrump  #CruzCrew  https???
## RT @urfavandtrump: RT for Brendon Urie
## Fav for Donald Trump https://t.co/PZ5vS94lOg
## RT @ggreenwald: The media spent all day claiming @SusanSarandon said she might vote for Trump. A total fabrication, but whatever... https:/???
## RT @Pjw20161951: NO KIDDING: #SleazyDonald just attacked Scott Walker for NOT RAISING TAXES in WI! #LyinTrump
## #NeverTrump  #CruzCrew  https???
## RT @trapgrampa: This is how I see #Trump every time he speaks. https://t.co/fYSiHNS0nT
## RT @mitchellvii: So let me get this straight.  Any reporter can assault Mr Trump at any time and Corey can do nothing?  Michelle is clearly???
## RT @paulbenedict7: How #Trump Sacks RINO Strongholds by Hitting Positions Held by Dems and GOP https://t.co/D7ulnAJhis   #tcot #PJNET https???
## RT @DRUDGE_REPORT: VIDEO:  Trump emotional moment with Former Miss Wisconsin who has terminal illness... https://t.co/qt06aG9inT
## RT @ggreenwald: The media spent all day claiming @SusanSarandon said she might vote for Trump. A total fabrication, but whatever... https:/???
## RT @DennisApgar: Thank God I seen Trump at first stop in Wisconsin media doesn't know how great he is, advice watch live streaming https://???
## RT @paulbenedict7: How #Trump Sacks RINO Strongholds by Hitting Positions Held by Dems and GOP https://t.co/D7ulnAJhis   #tcot #PJNET https???
## RT @DRUDGE_REPORT: VIDEO:  Trump emotional moment with Former Miss Wisconsin who has terminal illness... https://t.co/qt06aG9inT
## RT @DennisApgar: Thank God I seen Trump at first stop in Wisconsin media doesn't know how great he is, advice watch live streaming https://???
## RT @mitchellvii: So let me get this straight.  Any reporter can assault Mr Trump at any time and Corey can do nothing?  Michelle is clearly???
## RT @sciam: Trump's idiosyncratic patterns of speech are why people tend either to love or hate him https://t.co/QXwquVgs3c https://t.co/P9N???
## RT @Norsu2: Nightmare WI poll for Ted Cruz has Kasich surging: Trump 29, Kasich 27, Cruz 25. https://t.co/lJsgbLYY1P #NeverTrump
## RT @thehill: WATCH: Protester pepper-sprayed point blank at Trump rally https://t.co/B5f65Al9ld https://t.co/skAfByXuQc
## RT @sciam: Trump's idiosyncratic patterns of speech are why people tend either to love or hate him https://t.co/QXwquVgs3c https://t.co/P9N???
## RT @ggreenwald: The media spent all day claiming @SusanSarandon said she might vote for Trump. A total fabrication, but whatever... https:/???
## RT @DebbieStout5: Wow! Last I checked it was just 12 points &amp; that wasn't more than a day ago. Oh boy Trump ppl might want to rethink???? http???
## RT @tyleroakley: i'm a messy bitch, but at least i'm not voting for trump
## RT @vandives: Trump supporters r tired of justice NOT being served. There's no justice anymore. Hardworking Americans get screwed. That's n???
## RT @AP: BREAKING: Trump vows to stand by campaign manager charged with battery, says he does not discard people.
## RT @AP: BREAKING: Trump vows to stand by campaign manager charged with battery, says he does not discard people.
## RT @urfavandtrump: RT for Jerrie (Little Mix)
## Fav for Donald Trump https://t.co/nEVxElW6iG
## RT @urfavandtrump: RT for Jerrie (Little Mix)
## Fav for Donald Trump https://t.co/nEVxElW6iG
## RT @NoahCRothman: When Walker was fighting for reforms, Trump was defending unions and collective bargaining privileges https://t.co/e1UWNN???
## RT @RedheadAndRight: Report: Secret Service Says Michelle Fields Touched Trump https://t.co/c5c2sD8VO2
## 
## This is the only article you will n???
## RT @AIIAmericanGirI: VIDEO=&gt; Anti-Trump Protester SLUGS Elderly Trump Supporter in the Face
## https://t.co/GeEryMDuDY
## RT @NoahCRothman: When Walker was fighting for reforms, Trump was defending unions and collective bargaining privileges https://t.co/e1UWNN???
## RT @JusticeRanger1: @realDonaldTrump @Pudingtane @DanScavino @GOP @infowars @EricTrump 
## URGENT PUBLIC TRUMP ALERT:
## COVERT KILL MEANS https:???
## RT @AIIAmericanGirI: VIDEO=&gt; Anti-Trump Protester SLUGS Elderly Trump Supporter in the Face
## https://t.co/GeEryMDuDY
## RT @RedheadAndRight: Report: Secret Service Says Michelle Fields Touched Trump https://t.co/c5c2sD8VO2
## 
## This is the only article you will n???
## RT @JusticeRanger1: @realDonaldTrump @Pudingtane @DanScavino @GOP @infowars @EricTrump 
## URGENT PUBLIC TRUMP ALERT:
## COVERT KILL MEANS https:???
## RT @Schneider_CM: Trump says nobody had ever heard of executive orders before Obama started signing them. Never heard of the Emancipation P???
## RT @RonBasler1: @DavidWhitDennis @realDonaldTrump @tedcruz 
## 
## CRUZ SCREWS HOOKERS
## 
## CRUZ / CLINTON
## RT @DonaldsAngel: Former Ms. WI just said that she is terminally ill but because of Trump pageant, her 7 yr. old son has his college educat???
## RT @Schneider_CM: Trump says nobody had ever heard of executive orders before Obama started signing them. Never heard of the Emancipation P???
## RT @DonaldsAngel: Former Ms. WI just said that she is terminally ill but because of Trump pageant, her 7 yr. old son has his college educat???
## RT @Dodarey: @DR8801 @SykesCharlie Charlie, let's see you get a straight "yes" or "no" answer from Cruz a/b being unfaithful to his wife @T???
## RT @RonBasler1: @DavidWhitDennis @realDonaldTrump @tedcruz 
## 
## CRUZ SCREWS HOOKERS
## 
## CRUZ / CLINTON
## RT @RockCliffOne: Remember when the idea of a diabolical moron holding the world hostage was an idea for a funny movie? #Trump #GOP https:/???
## RT @HillaryClinton: "Every day, another Republican bemoans the rise of Donald Trump... but [he] didn???t come out of nowhere." ???Hillary
## https???
## RT @Dodarey: @DR8801 @SykesCharlie Charlie, let's see you get a straight "yes" or "no" answer from Cruz a/b being unfaithful to his wife @T???
## RT @HillaryClinton: "Every day, another Republican bemoans the rise of Donald Trump... but [he] didn???t come out of nowhere." ???Hillary
## https???
## RT @RockCliffOne: Remember when the idea of a diabolical moron holding the world hostage was an idea for a funny movie? #Trump #GOP https:/???
## RT @immigrant4trump: @immigrant4trump msm, cable news attacking trump all day, from 8am to 10pm today, then the reruns come on, repeating t???
## RT @immigrant4trump: @immigrant4trump msm, cable news attacking trump all day, from 8am to 10pm today, then the reruns come on, repeating t???
## RT @GlendaJazzey: Donald Trump???s Campaign Financing Dodge, @rrotunda https://t.co/L8flI4lswG via @VerdictJustia
## RT @TUSK81: LOUDER FOR THE PEOPLE IN THE BACK https://t.co/hlPVyNLXzx
## RT @loopzoop: Well...put it back https://t.co/8Yb7BDT5VM
## RT @claytoncubitt: Stop asking Bernie supporters if they???ll vote for Hillary against Trump. We got a plan to beat Trump already. Called Ber???
## RT @akaMaude13: Seriously can't make this up. What a joke. #NeverTrump  https://t.co/JkTx6mdRgC
```
</div>

<p class="">Great work!</p>

### Bringing it all together (2)


<div class>
<p>Sometimes, we make mistakes when calling functions - even ones <em>you</em> made yourself. But don't fret! In this exercise, you will improve on your previous work with the <code>count_entries()</code> function in the last chapter by adding a <code>try-except</code> block to it. This will allow your function to provide a helpful message when the user calls your <code>count_entries()</code> function but provides a column name that isn't in the DataFrame.</p>
<p>Once again, for your convenience, <code>pandas</code> has been imported as <code>pd</code> and the <code>'tweets.csv'</code> file has been imported into the DataFrame <code>tweets_df</code>. Parts of the code from your previous work are also provided.</p>
</div>

<li>Add a <code>try</code> block so that when the function is called with the correct arguments, it processes the DataFrame and returns a dictionary of results.</li>
<li>Add an <code>except</code> block so that when the function is called incorrectly, it displays the following error message: <code>'The DataFrame does not have a ' + col_name + ' column.'</code>.</li>
<div>

```python
# Define count_entries()
def count_entries(df, col_name='lang'):
    """Return a dictionary with counts of
    occurrences as value for each key."""

    # Initialize an empty dictionary: cols_count
    cols_count = {}

    # Add try block
    try: 
        # Extract column from DataFrame: col
        col = df[col_name]
        
        # Iterate over the column in DataFrame
        for entry in col:
    
            # If entry is in cols_count, add 1
            if entry in cols_count.keys():
                cols_count[entry] += 1
            # Else add the entry to cols_count, set the value to 1
            else:
                cols_count[entry] = 1
    
        # Return the cols_count dictionary
        return cols_count

    # Add except block
    except:
        print('The DataFrame does not have a ' + col_name + ' column.')

# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang')

# Print result1
print(result1)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```
</div>

<p class="">Great work!</p>

### Bringing it all together (3)


<div class>
<p>In the previous exercise, you built on your function <code>count_entries()</code> to add a <code>try-except</code> block. This was so that users would get helpful messages when calling your <code>count_entries()</code> function and providing a column name that isn't in the DataFrame. In this exercise, you'll instead raise a <code>ValueError</code> in the case that the user provides a column name that isn't in the DataFrame.</p>
<p>Once again, for your convenience, <code>pandas</code> has been imported as <code>pd</code> and the <code>'tweets.csv'</code> file has been imported into the DataFrame <code>tweets_df</code>. Parts of the code from your previous work are also provided.</p>
</div>

<li>If <code>col_name</code> is <em>not</em> a column in the DataFrame <code>df</code>, raise a <code>ValueError 'The DataFrame does not have a ' + col_name + ' column.'</code>.</li>

<li>Call your new function <code>count_entries()</code> to analyze the <code>'lang'</code> column of <code>tweets_df</code>. Store the result in <code>result1</code>. </li>

<li>Print <code>result1</code>. This has been done for you, so hit 'Submit Answer' to check out the result. In the next exercise, you'll see that it raises the necessary <code>ValueErrors</code>.</li>
<div>

```python
# Define count_entries()
def count_entries(df, col_name='lang'):
    """Return a dictionary with counts of
    occurrences as value for each key."""
    
    # Raise a ValueError if col_name is NOT in DataFrame
    if col_name not in df.columns:
        raise ValueError('The DataFrame does not have a ' + col_name + ' column.')

    # Initialize an empty dictionary: cols_count
    cols_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]
    
    # Iterate over the column in DataFrame
    for entry in col:

        # If entry is in cols_count, add 1
        if entry in cols_count.keys():
            cols_count[entry] += 1
            # Else add the entry to cols_count, set the value to 1
        else:
            cols_count[entry] = 1
        
        # Return the cols_count dictionary
    return cols_count
  
# Call count_entries(): result1
result1 = count_entries(tweets_df, 'lang')

# Print result1
print(result1)
```

```
## {'en': 97, 'et': 1, 'und': 2}
```
</div>

<p class="">Great work!</p>

### Bringing it all together: testing your error handling skills


<div class><p>You have just written error handling into your <code>count_entries()</code> function so that, when the user passes the function a column (as 2nd argument) NOT contained in the DataFrame (1st argument), a <code>ValueError</code> is thrown. You're now going to play with this function: it is loaded into pre-exercise code, as is the DataFrame <code>tweets_df</code>. Try calling <code>count_entries(tweets_df, 'lang')</code> to confirm that the function behaves as it should. Then call <code>count_entries(tweets_df, 'lang1')</code>: what is the last line of the output?</p></div>

- [ ] 'ValueError: The DataFrame does not have the requested column.'
- [x] 'ValueError: The DataFrame does not have a lang1 column.'
- [ ] 'TypeError: The DataFrame does not have the requested column.'

<p class="">Correct!</p>

## Congratulations!

### Congratulations!

Well done. You're now well on your way to being a Pythonista Data Science ninja.

### What you???ve learned:

You're now able to write functions in Python that accept single and multiple arguments and can return as many values as you please. You're also adept at using default and flexible arguments and keyword arguments. You've gained insight into scoping in Python, can write lambda functions and handle errors in your very own function writing practice. You've also gained invaluable practice in using all of these techniques to write functions that are useful in a Data Science context. You have come a long way in your developing practice as a budding Pythonista Data Scientist.

### There???s more to learn!

There are more basic skills that you will need to learn in Python to be valuable as a working Data Scientist and many of these we'll cover in the sequel to this course so if you're finding yourself still thirsty for more Pythonista Data Science chops, I'd head over there right now. There you'll learn all about list comprehensions, which allow you to wrangle data in lists to create other lists, a tool utilized by all Data Scientists working in Python. You'll also learn about iterators, which you have already seen in the context of for loops without having necessarily known it. Iterators are everywhere in PythonLand and, to put it simply, allow you to rapidly iterate Data Science protocols and procedures over sets of objects; these are a couple of the cool functionalities in PythonLand you'll encounter in the sequel to this course, which will conclude with an entire chapter devoted to a case study in which you'll apply time and time again techniques learnt in both of these courses.

### Let's practice!

I'm looking forward to seeing you there and congratulations once again!
