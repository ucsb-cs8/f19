---
layout: lab
num: lab07
ready: true
desc: "String Formatting, Random, and File IO"
assigned: 2019-11-20 9:00am
due: 2019-11-27 08:59am
---

In this lab, you'll get more practice with:

* Testing your functions with pytest
* Using String Formatting
* Reading and processing files

## This lab should be done solo.

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_tests.py` - file containing test cases
* <strong>Please comment your name / perm at the top of each file.</strong>
* <strong>Make sure to have a docstring for every function.</strong>

Starter code is provided for you at the bottom of this page.

1.  Create a directory called `~/cs8/{{page.num}}` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_tests.py` in that `~/cs8/{{page.num}}` directory.


# Some notes about the File I/O functions

Create two files `input1.txt` and `input2.txt` in the `~/cs8/{{page.num}}` directory. Use these two input files to test your functionality: add a small number of words (2-10) first to make sure that you can verify that your function is working correctly. Add punctuation next to make sure you can correctly remove it; test for contractions, e.g., "don't".

These files are used when running pytest on `{{page.num}}_tests.py`. We will be using additional input files to test your submission on Gradescope.

Note that all words are separated by a whitespace character, and a word contains only alpha-numeric characters that does not include punctuation characters. For simplicity, you may assume the text only contains the `,.!?;` punctuation characters. Your code will need to split and strip the text file string appropriately.


# Notes on computing the most common words

If you run `mostCommonWords("input1.txt", 1)`, this function should essentially return the mode value from the file (the word that occurs most often). To be able to return **the list** of most common words, you will need to count how many times each word occurred in a file. Implement `wordFrequency` to help you first count the words in a file, then `mostCommonWords()` can sort them by the frequencies and store `N` of them into the returned list.

* Test your function by making sure your input file has something like "hello hello hello world" and that you are able to return "hello" as the most frequently occuring word. 
* Test your function by making sure if your "input1.txt" has something like "hello hello hello world" and you call `mostCommonWords("input1.txt", 2)`, the function correctly returns `['hello', 'world']`.
* Test your function by making sure if your "input2.txt" has something like "hello world world world" and you call `mostCommonWords("input2.txt", 2)`, the function correctly returns `['world', 'hello']`.
* Test your function by making sure if your "input2.txt" has something like "hello world world world" and you call `mostCommonWords("input2.txt", 3)`, the function correctly prints `[Error] The "input2.txt" contains 2 unique words (you asked for 3).`. Check that it also returns `None`.



# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "Lab06" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.


# `{{page.num}}.py`

```python
# lab07.py

# Student: (insert name and perm number here)


def totalWords(filename):
    '''
    (20 points)
    Reads the file from filename in your function and returns
    the number of words in the file.
    - Words are separated by whitespace characters, but the count doesn't include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - The split and strip functions may be useful in your implementation.
    - Your function should open the file for reading, and close
    the file before returning.
    '''
    return "stub"


def longestWord(filename):
    '''
    (20 points)
    Reads the file from filename in your function and returns
    the longest word in the text file.
    - Words are separated by whitespace characters, but do not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - In the case of a tie, the 1st occurrence of the longest word
    is returned.
    - The split and strip functions may be useful.
    - Your function should open the file for reading, and close
    the file before returning.
    '''
    return "stub"


def charactersPerWord(filename):
    '''
    (20 points)
    Reads the file with filename into your function and returns
    the average number of characters per word.
    - Words are separated by whitespace characters, but does not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - The split and strip functions may be useful.
    - Your function should open the file for reading, and close
    the file when done.
    '''
    return "stub"


def wordFrequency(filename):
    '''
    (20 points)
    Reads the file from filename in your function and returns a dictionary 
    with the frequency of each word as its value.
    - Words are separated by whitespace characters, but do not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - The split and strip functions may be useful.
    - You can assume contractions count as one word 
    (i.e. "don't", "you'll", etc. are one word).
    - Your function should open the file for reading, and close
    the file before returning.
    '''
    return "stub"
    
    
def mostCommonWords(filename, N):
    '''
    (20 points)
    Reads the file from filename in your function and returns a list of N most
    common words in the text file (i.e., N words with the highest frequency),
    sorted by the number of times they occured in the file (most common first).
    - Use wordFrequency() helper function to count the frequency of each word.
    - Print "[Error] The "<filename>" contains <X> unique words (you asked for <N>)." 
    and return None if N is larger than the number of words in the file (substitute 
    "<filename>", <X>, <N> with the actual values).
    '''
    return "stub"

```


# Extra Credit Challenges

(make sure you read all 3 sections including this one: Extra Credit Challenges, Extra Credit Tests, and Extra Credit Submission)

Below are three extra credit challenges.
- For each one, you need to implement a modified version of each of the lab07 functions (`totalWords`, `longestWord`, `charactersPerWord`, `wordFrequency`, and `mostCommonWords`).
- Each of the three challenges involves pre-processing the input text in a new way.
- Each modified function that you will implement must call the original version of the function after doing the specified pre-processing.
- __The pre-processing is cumulative__: that means your solution to challenge 3 must perform the pre-processing required by challenge 3, in addition to the pre-processing required by challenges 1 and 2.

The challenges are:
1. Remove double-quotes from the file content
2. Remove "stop words" using the provided [stopwords.txt](stopwords.txt).
  * every line of stopwords.txt contains exactly one word, called a stop word (some of them are contractions, e.g. "you'd")
	* Hint about how to remove all occurences of a word from a list of words: if you use the lists's `remove` method, it will only remove the first occurence of that word from the list. To address this you can use a while loop to keep removing a word as long as it is still found in the list. Alternatively, instead of removing the desired word from the list, you could create a new list and add to it all words except for the one you'd like to remove.
3. Convert all letters to lower case
  * In English, "Hi" and "hi" are the same word, even though in Python they are different strings. For this challenge, enforce that by pre-processing all words to lowercase. The result will be that "hi", "Hi", "HI", and "hI" will all be counted as the same word "hi". (Yes, "HI" is the state abbreviation for Hawaii so you could argue it actually is a different word. In this assignment do not worry about that, just treat them as the same word).

__REMINDER--the pre-processing is cumulative__: that means your solution each challenge must perform the pre-processing required by that challenge, in addition to the pre-processing required by the previous challenge(s).

# Extra Credit Tests

For each challenge we are providing the tests below to help you get started. The autograder for this assignment will contain additional tests for cases that are not covered by the tests below, so you are advised to think about which test cases are missing and write them yourself.

Initial tests for challenge 1:
```python
```

Initial tests for challenge 2:
```python
```

Initial tests for challenge 3:
```python
```

# Extra Credit Submission

For each challenge that you complete, you will sumbmit one file, called `lab07_challenge1.py`, `lab07_challenge2.py`, or `lab07_challenge3.py` for challenges 1, 2, and 3 respectively. Each file must contain a modified implementation of `totalWords`, `longestWord`, `charactersPerWord`, `wordFrequency`, and `mostCommonWords`. In order to reuse your original functions, we recommend copying them into your challenge files with new names, for example `longestWord_original`.
