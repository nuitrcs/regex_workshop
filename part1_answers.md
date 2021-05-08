Answers to the exercises in the [Part 1](part1.html) workshop.  Additional regular expressions may meet the exercise criteria.

## EXERCISE 1

Open the [example](http://regexr.com/5rddd):

1. Change the pattern to: `soviet union` - does it still match?

`soviet union` should not match because regular expressions are case sentisitive by default (unless you specifically set them to be case insensitive).

2. Change the pattern to find female astronauts.  Type the number of times "female" is found in the text in the chat.

`female`

It should be found 3 times -- there are only two distinct female astronauts in the list though.


## EXERCISE 2

Open the [blank example](regexr.com/5rddd).  

1. Write a regular expression to find any substrings consisting of a capital A, followed by any character, followed by a lower case a.  For example, the regex should match both `Aca` and `Ada`.  Type the last match in the chat.  

`A.a`

2. Write a regular expression to find any 5 letter sequences starting with A and ending with n.  

`A...n`

3. Write an expression to find actual period marks in the text.  How many are there?  Put the answer in the chat.  

`\.`

There are 7 "."


## EXERCISE 3

Open the [blank example](regexr.com/5rddd).  

1. Repeat the exercise above, but use a quantifier this time: Write a regular expression to find any 5 letter sequences starting with A and ending with n.  

`A.{3}n`


2. Find any sequences of 2 or more spaces (the character made by the space bar key on your keyboard).  

Looks like: ` {2,}`

But if you copy and paste the above, it won't work correctly; you'll need to actually type the space with the spacebar.

CHALLENGE: write an expression that will match either `male` or `female` and no other words in the example text

`f?e?male`

The `?` makes the letter before it optional.  The expression above would also match `fmale` or `emale` but since those aren't in our text, we won't worry about them.  

## EXERCISE 4

Open the [blank example](regexr.com/5rddd).  

Write an expression using a non-greedy quantifier that matches both `United States` and `United Arab Emirates` and no other words in the astronaut text.

`United.+?s`

You could shorten "United" in the regex above and still match, but `U.+?s` will match more than just the two country names.


## EXERCISE 5

Open the [blank example](regexr.com/5rddd).  

1. Write an expression to find a digit followed by a comma `,`

`\d,`

2. Use a character class to write an expression to match both `moon` and `Moon` - type how many times the word appears in the chat.

`[mM]oon`

The word appears 4 times.

CHALLENGE: Write an expression to find all capitalized words in the example text.  The expression should only match the letters in the word and not include any spaces before or after it.  You probably want to include the character class for word characters noted above.  The answer would also match parts of strings where the capital letter isn't at the start (e.g. "elNiri"), but there aren't any cases like that in our example data, so we won't worry about that!  (We'll learn how to actually deal with word boundaries in Part 2).  

`[A-Z]\w+`
