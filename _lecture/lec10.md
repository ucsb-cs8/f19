# Lecture 10: Cryptography Hints and Mutable vs. Immutable

Codemakers and codebreakers back in the day didn't have to learn Python (despite their job title), but it probably would've made their lives much easier if they did. Or maybe it would've done the opposite. Eh, depends on how you look at it.

Oh, right, cryptography! Here's more on `range()` and control flow nesting so that you too can live out your childhood dreams of slow-motion dives and personal theme songs.*

\**Disclaimer: Slow-motion dives and personal theme songs not included.*

# Function function, what's your function?

Hooking up variables and keywords and statements! Let's make a function.

```python
def print_range(num):
```

The **`def`** keyword tells Python to, well, *def*ine a function, so always include this. After `def` is `print_range`, which is the name you want to give your function.

Then there's a set of parentheses and that `num` thing. `num` is a variable, but if you really want to be specific, you would say that this variable is a **parameter** because it's inside of a function. Putting a ~~variable~~ parameter in like this allows you to use `num` inside your function and do cool things with it.

It's important to note that `num`, here, is just a placeholder for when you give it a value later in the program with a **function call**, like `print_range(42)`. You could call `num` anything else, like `mac_and_cheese` or `absurdly_long_parameter_that_no_one_should_have_to_read` or good old `x`, but `num` is good here because it's short and sweet and descriptive all the same. As long as you spell `num` as `num` when you use it inside of your function, all will be fine.

(If you don't want or need a parameter for your function, you would just define the function without one, like `def print_range()`. Note that you'd still keep the parentheses, though.)

Oh, and don't forget the colon at the end. A function definition isn't complete without a colon. It'd be a little like if a spy didn't have at least one trench coat in their closet, in which case it would, without question, completely and utterly invalidate their life's work.

# String iteration using `range()`

Let's flesh out the ```print_range``` function from above.

```python
def print_range(num): # Remember that num is just a placeholder.
    '''Outputs various numbers depending on certain conditions.'''
    for i in range(num):
        if i < 3:
            print(i)
        else:
            if i < 5:
                continue # Begins a new for loop iteration (goes back to beginning).
            else:
                return i

print_range(9)
```

Wow. That was fast. Here's the logic behind the function, in plain English.

1. Define a function named `print_range` and with one parameter, `num`.
2. Come up with a docstring that describes the purpose of the function.
3. Create a `for` loop with loop variable `i` that iterates over a sequence of `range(num)`. `range(num)` means that if the values from this `range` call were to be stored in a list, you would get `[0, 1, 2, ... , num-2, num-1]`.
4. Inside this `for` loop, come up with some conditional statements that do certain things if certain, well, conditions are met.
    * If `i` has a value of less than `3`, then print the current value of `i` to the terminal window.
    * If `i` has a value of anything other than less than `3`, then execute another batch of conditional statements.
        * If `i` has a value of less than `5`, then skip back to the beginning of the for loop, increment the value of `i` by `1`, and go through the `for` loop anew.
        * If `i` has a value of anything other than less than `5`, then return the current value of `i` and stop running the function.

# Crash course on binary

There will be times in your programming career where you'll have to wrangle **binary numbers** (think 0's and 1's) as opposed to the usual **decimal numbers** (think everything other than 0's and 1's). You'll have to understand how they work, how to convert between the two, how to add and subtract them, and all that fun stuff.

But this is not one of those times.

All you need to know right now is that binary numbers exist and that Python's built-in function `bin` takes an integer parameter and returns a string starting with `0b` and followed by the binary number. For example, `bin(9)` returns `'0b1001'`.

But if you're *still* interested in learning more (such proactivity!), feel free to read up on these two articles:
* [Number Conversions](https://ucsb-cs8.github.io/topics/number_conversions/)
* [Converting between binary and decimal](https://www.learncpp.com/cpp-tutorial/converting-between-binary-and-decimal/).

# Objects

Everything in the world is an object. The chair you're sitting in right now is an object. Alternatively, if you hate chairs and sitting down because you're concerned that they result in loads of health risks, then the floor you're standing on right now is an object too. Technically, you yourself would also be an object, but people usually don't refer to other people as objects if they're trying to be respectful, as we should all strive to be.

So, from that logic, everything in Python is an [object](https://en.wikipedia.org/wiki/Object_(computer_science)) as well. Variables. Values. Functions. Methods. **Everything.**

Take, for example, this bit of code:

```python
my_bat = "bat"
my_cat = "cat"
```

`my_bat`, `"bat"`, `my_cat`, and `"cat"` are all objects. Sure, they're different kinds of objects (`my_bat` and `my_cat` are variables and `"bat"` and `"cat"` are values, as you know), but they're still objects nonetheless. So when you create a variable and give it a value, you're basically creating a value object and assigning a label (another object) to it.

What happens here, then?

```python
my_bat = "bat"
ur_bat = "bat"
my_cat = "cat"
```

`my_bat` and `ur_bat` both have the same value `"bat"`. Does Python create two different value objects and assign them two different labels? No. Python instead creates just a single value object and has `my_bat` and `ur_bat` both point to that same object. In other words, **a variable that has the same value as another variable is simply a different reference to the same object**.

You can verify this sameness yourself. Python has a built-in function named **`id`** that returns the **[memory address](https://en.wikipedia.org/wiki/Memory_address)** of an object, which is an integer that tells you where a piece of data is stored on your computer. **Different value objects must have unique memory addresses**, so if you define the three variables above in IDLE and call `id("bat")` and `id("cat")`, you should get two different numbers.

You can also call `id` using a variable name instead of the value object itself, and it's here where the usefulness of `id` starts coming into play. If you do `id(my_bat)` and `id(ur_bat)`, you should get the same memory address as if you did `id("bat")`, since the two variables both refer to the value `"bat"`. You now have a way of distinguishing between variables that reference the same object and variables that reference different objects.

# Mutable vs. immutable

Strings are immutable, while lists are mutable.

Because strings are immutable, they don't change no matter what you do to them short of replacing the string entirely.

```python
my_cat = "cat"
my_bat = "bat"
your_bat = "bat"

list = ["cat", "bat"]

def swap_pets(pet1, pet2):
    print("From swap: ", pet1, pet2)
    tmp = pet1
    pet1 = pet2
    pet2 = tmp
    print("From swap: ", pet1, pet2)
    return pet2
    # pet1 and pet2 only exist within this function. Once this function stops executing, pet1 and pet2 disappear; trying to call one of them outside of the function results in an error.

print("Before the swap: ", my_cat, my_bat)
pet = swap_pets(my_cat, my_bat)
print("After the swap: ", my_cat, my_bat)
print(pet)
```

Because lists are mutable, be careful about changing them in functions and requiring the original version.

```python
my_cat = "cat"
my_bat = "bat"
your_bat = "bat"

list = ["cat", "bat"]

def swap_pets_list(a_list): # Need to always double check that there are the proper number of items in a list.
    print("From swap: ", a_list[0], a_list[1])
    tmp = a_list[1]
    a_list[0] = a_list[1]
    a_list[0] = tmp
    print("From swap: ", a_list[0], a_list[1])
    return a_list

print("Before the swap: ", list[0], list[1])
pet = swap_pets_list(list)
print("After the swap: ", list[0], list[1])
print(pet)
```
