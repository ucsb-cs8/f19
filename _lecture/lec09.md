# Lecture 9: String Processing Cryptography

On the menu today: fruity looped strings and indices, a dash of imported modules, and a cipher sundae. But before we begin…

# Some words of wisdom

Try not to hardcode values into your programs. Write code that can be reused in many different situations without modification. You can do this by keeping automation in mind.

For example, instead of specifying that there are 26 letters in a string, use the `len()` function to get that same number. That way, your program can quickly and easily adapt to different cases, such as a string with 33 letters.

# Now, a bit of review (or, the appetizers)

## (Froot) Loops

A **`for` loop** is a *count*-controlled loop that repeats a specific number of times based on how many items are in a collection, such as a list, a tuple, or a range. As such, you don't need to tell it specifically when to end, because it ends by itself ~~when it feels like it~~ when it has gone through all of the items in the collection. Here's the rough format of a `for` loop:

```python
for item in collection:
    action
```

Compare this to a **`while` loop**, which is a *condition*-controlled loop that does require you to specify an end condition, such as when a counter reaches a certain value.

This lecture will exclusively use `for` loops. `while` loops will be saved for another meal.

## Strings (and string cheese)

Happy Halloween! Soon. Let's define a string:

```python
s = "Halloween"
```

As you (hopefully) recall, individual characters in a string can be accessed with their **index**. Here are the indicies, both positive and negative, of each of the characters of our string `s`.

| H | a | l | l | o | w | e | e | n |
| :---: | :---: |  :---: |  :---: |  :---: |  :---: |  :---: |  :---: |  :---: |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |

The syntax for accessing characters is

```python
c = s[i]
```

where `c` is a variable for storing the retrieved character, `s` is the variable of the string `"Halloween"`, and `i` is the index.

## Home on the `range()`

The **`range()`** function generates an incremental set of numbers from one number to another number. It sounds simple, but there's a lot that's going on. So let's unpack everything.

Here's `range()` written out, with all three possible arguments and their positions represented by placeholder values:

```python
range(start, end, step)
```

Let's go through each of those arguments one by one.

| Argument | What it means | Optional? | Default value |
| -------- | ------------- | --------- | ------------- |
| `start` | The number you, well, start counting from. | yes | `0` |
| `end` | The number you stop counting at, plus 1. For example, writing `3` means `range()` will only return up to `2` at the most, and writing `10` means `range()` will only return up to `9` at the most. (You must specify an end value. Otherwise, you'll get a nasty `TypeError`.) | no | N/A |
| `step` | How many numbers you count by from the start value to the end value. Remember how, when you were younger, you used to count by 2's and 3's and 5's and whatnot? You might've even made a game out of it. 2, 4, 6, 8, 10, and so on until you got tired. Same thing in `range()`. | yes | `1` |

# On to the main course

## String indexing and iteration

Remember the `len()` function? It's amazing.

Let's combine everything we've done so far to print every character in string `s` using a `for` loop. Here's what that would look like:

```python
s = "Halloween"
for i in range(len(s)):
    print(s[i])
```

Here's what the Python shell returns when we run the code:

```
H
a
l
l
o
w
e
e
n
```

If you're a bit confused about the syntax of the Python code above (especially with the `range()` part), here's the same code but with the optional and default `range()` arguments included:

```python
s = "Halloween"
for i in range(0, len(s), 1):
    print(s[i])
```

Here, `range()` is telling the `for` loop to assign `i` a value of `0`. When the loop finishes running once, `range()` tells the `for` loop to increase `i` by a value (step) of `1`. These iterations continue until `i` is equal to a value of `8`, which is one less than the value of `len(s)`, which is equal to `9`.

Of course, you don't need to include `0` at the beginning of `range()`, nor do you need to include `1` at the end. But these are the implied and unseen values at work here, and sometimes it helps to make the unseen seen.

So if `i` is first equal to `0`, then the `for` loop is basically telling `print(s[i])` to `print(s[0])`, or to `print('H')`. Then, since there are no more statements within the loop, a new iteration begins, and `i` becomes `1`. Now, `print(s[i])` becomes `print(s[1])` becomes `print('a')` on a new line. And on it goes until `print(s[8])` becomes `print('n')` and the final character, `n`, is outputted onto the shell.

## `range()` shenanigans

Now that you're (hopefully) more confident about `range()`, let's start messing around with the `start`, `stop`, and `end` values and changing their defaults. Perhaps it'll be easier for you if you actually represent `start`, `end`, and `step` as variables, like so:

```python
s = "Halloween"

start = 2
end = len(s)
step = 3
 
for i in range(start, end, step):
    print(s[i])
```

And the output of the Python shell:

```
l
w
n
```

## Printing a string backwards

You're not out of the woods yet.
