# Lecture 9: String Processing Cryptography

On the menu today: fruity looped strings and indices, a dash of imported modules, and a cipher sundae. But before we begin…

# Some words of wisdom

Try not to hardcode values into your programs. Write code that can be reused in many different situations without modification. You can do this by keeping automation in mind.

For example, instead of specifying that there are 26 letters in a string, use the `len()` function to get that same number. That way, your program can quickly and easily adapt to different cases, such as a string with 33 letters.

# Now, a bit of review (or, the appetizers)

## (Froot) Loops

A **`for` loop** is a *count*-controlled loop that repeats a specific number of times based on how many items are in a collection, such as a list, a tuple, or a range. As such, you don't need to tell it specifically when to end, because it ends by itself ~~when it feels like it~~ when it has gone through all of the items in the collection. Here's the rough format of a `for` loop:

```python
for VARIABLE in COLLECTION:
    STATEMENT(s)
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

## Bigger steps (or, more `range()` shenanigans)

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

## Printing a string backwards (or, *even more* `range()` shenanigans)

You're not out of the woods yet. You've printed all of the characters in a string, and you've even printed some of the characters in a string based on a step value. But what if you wanted to print a string backwards?

Well, here you go:

```python
s = "Halloween"

start = -1
end = -len(s) - 1
step = -1

for i in range(start, end, step):
    print(s[i])
```

Remember those negative indices? Time to put them to use.

| Argument | Value | But why? |
| -------- | ----- | -------- |
| `start` | `-1` | Printing a string backwards means beginning from the last character in the string, which in this case is `-1`. |
| `end` | `-len(s) - 1` | Okay, okay. Start from `-1`, and count backwards by 1 until you hit the character `'H'` in the string `s = "Halloween"`. You should get `-9` (refer to the table of indices up above if you're confused). But remember that thing about automation? "Try not to hardcode values into your programs." So to get `-9` automatically, the function `len()` (which gets the length of a string) seems like a good place to start.<ul><li>`len(s)` returns a value of `8`, since there are 8 characters in string `s`.</li><li>`-len(s)` thus returns the negative value of `len(s)`, meaning `-8`.</li><li>`-len(s) - 1`, which subtracts `-1` from `-len(s)`, thusly returns `-9`, which is what we want.</li></ul>Notice that now, if we redefine string `s` to something like `s = "candy"`, `end` will automatically change to `-6` so that we don't have to change it ourselves. Hooray.|
| `step` | `-1` | You counted backwards by 1 to get the `end` value. That's exactly the same thing as `step`! "Backwards by 1" is just an informal way of saying `-1`. In other words, `range()` increments, or steps, by `-1` per iteration. |

All of this outputs:

```
n
e
e
w
o
l
l
a
H
```

# Side dishes

You've done `for` loops, string indexing, string iteration, and lots of `range()`-related stuff. Time for some more advanced topics.

## Handling index overflow

String `s = "Halloween"` has positive indices of `0` to `8` and negative indices of `-1` to `-9`, so statements like `print(s[6])` and `print(s[-3])` work perfectly fine.

But what happens if you choose an index that doesn't exist in this case, like `42` and `-1729`, and use them in statements like `print(s[42])` and `print(s[-1729])`? You run into an `IndexError` and your day is ruined.

Well, not quite. What if there was some way you could "loop" an index back to one of the valid indices? Fortunately, there is a way.

```python
s = "Halloween"

i = input("Enter an index: ")
i = int(i)

if i > len(s) - 1:
    i %= len(s)
elif i < -len(s):
    i %= len(s)
    
print(s[i])
```

As usual, we first define a string `s = "Halloween"` with which to work with.

Then, the program prompts the user to type in an index and stores that value in variable `i`. Let's assume the user types `42` as the input. Because `input()` normally gives values in the string data type, the program must convert `42` into an integer type so that mathematical operations on the value are possible. (You can also combine the first two lines into something like `i = int(input("Enter an index: "))` if you find that easier to understand.)

Now comes the index checking part. The first `if` statement checks to see if the index exceeds the upper indexical bound of string `s`, which in this case is `8`. Again, in the interest of automation, `len(s) - 1` becomes `9 - 1` becomes `8` by itself without programmer interference, which is the ideal scenario.

Since we earlier defined `i` to be equal to `42`, `i` is indeed greater than `len(s) - 1`. The `if` statement successfully proceeds to the next statement `i %= len(s)`, which is just a shorthand way of writing `i = i % len(s)`. Recall that the `%` symbol, or modulo, divides a number on the left side by the number on the right side and returns the remainder of the operation. In this case, `i = i % len(s)` becomes `i = 42 % 9` becomes `i = 6`.

Because the `if` statement has been satisfied, the program skips the `elif` statement during execution and moves on to `print(s[i])`. Now that `i = 6` instead of `i = 42`, `print(s[i])` returns the character `e` instead of a scary `IndexError`.
