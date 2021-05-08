## Part 2 Answers

Answers to exercises in part 2 of the regular expressions workshop.  [Part 2 materials](part2.html)

One answer is provided.  Other regular expressions may also fulfill the exercise criteria.


### EXERCISE 1

Open the [blank example](regexr.com/5rddd). 

Write a regular expression to find all words that end in a `y`.  Have your expression match the entire word, not just the ending `y`.  Hint: recall `\w` will match any "word" characters, which may help for capturing the first part of the word that isn't "y".  Need a refresher on how to represent [repetition](part1.html#concept-3-repetition)?

Type the last word that you match in the chat when you're done.

`\w+y\b`

Last word that matches is: `Ashby`


### EXERCISE 2

Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

Write a regular expression to match any number of spaces (0 or more) at the beginning of each line of the text.  

Spaces are visualized in the text in the RegExr tool with a circle.  

Hint: Need a refresher on how to represent [repetition](part1.html#concept-3-repetition)?  

`^ *`

### EXERCISE 3A


Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

To see the results of the group match, instead of the entire expression, in the bottom, change `$&\n` to `$1\n`.  The `1` is for the first group in the expression you'll write.

Recall that before we wrote a regular expression to match the spaces at the beginning of the line: `^ *`

Now write a regular expression that includes a group to capture the first letter that appears after those spaces at the beginning of the line.


`^ *(.)`


### EXERCISE 3B

Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

To see the results of the group match in the bottom, , instead of the entire expression, change `$&\n` to `$1\n`.  The `1` is for the first group in the expression you'll write.

Recall that we've written two regular expressions before:

* Match spaces at the beginning of the line: `^ *`
* Match male or female (challenge from Part 1): `f?e?male`

Using these components, we want to **write a regular expression to capture the name of the country in each line.**  The country name comes after the beginning of the line and the spaces, and before a space and then male or female.  Combine these components with a new part of a regular expression that includes a group to capture the name of the country.  Goal: regular expression that includes a group (in `()`) that will capture the name of the country.

Hint: You'll probably want a non-greedy quantifier: `.+?` will match 1 or more characters, until the next part of the expression matches.  

`^ *(.+?) (male|female)`


### EXERCISE 4

Open the [blank example](regexr.com/5rddd). Click on Replace for the bottom tab so that you can substitute or replace text.  Turn on the multiline flag.

Enter this regular expression: `^ *(.+?) (f?e?male)`

Write a replacement expression so that the first few lines of output look like the following, with the name of the country, followed by a colon and space, and then the rest of the information from each line, minus male/female.

Example output:
```
United States: Joseph M. Acaba
United States: Loren Acton
United States: James Adamson
Soviet Union Russia: Viktor M. Afanasyev
Kazakhstan: Aydyn Aimbetov, first cosmonaut by KazCosmos-selection in space
United States: Thomas Akers
```

Replacement expression: `$1,`

### EXERCISE 5

Open the [blank example](regexr.com/5rddd). Click on Replace for the bottom tab so that you can substitute or replace text.  Turn on the multiline flag.

We're going to finally turn the astronaut text into a data set that we could maybe use.  We want to extract the three pieces of information that appear in every line: country, male or female, and name.  We want to convert these to be comma separated values, meaning there is a comma between each piece of information on the same line.  We want to discard all other information.

Fair warning: we're going to have to put together lots of pieces we've learned in the first two parts of this workshop to write an expression that is much more complicated than the previous exercises.  This is a signifcant step up in difficulty.  We're going to approach it in parts.

#### Part 1

There are two types of lines in the text:

* Ones with 4 spaces, then country, space, male/female, space, name, end of the line
* Ones with the info we want, followed by a space, then the either space and `(` or `,` and space and other info

To build up a larger expression, first **write a regular expression that will match a space then `(` or `,` then a space, and then any amount of text after that.**  Make sure the multiline flag is turned on.

Hint: to match any amount of text, use `.*`.  

`(, | \().*`

#### Part 2

Putting it all together: **write a regex to extract country, male/female, and name from each line and turn them into comma separated values.**

Since the expression above doesn't match every line, we also need to account for cases where the name is followed by the end of line `$`.  Add `$` to your "or" expression above to allow for this possibility.  For example, if your "or" expression above was `(____|____)`, then you should make it: `($|____|____)` 

Now, add to the beginning of the expression to match the 4 leading spaces, and the 3 capturing groups: one for country, one for male or female, and one for the astronaut's name.  You can find a start at this expression in Exercise 4 (the expression in exercise 4 matches the spaces, country, and male/female; add another capturing group to it for the name).

Write a replacement expression to make the comma separated values data we want.  The first few lines of output after replacement should look like:

```
United States,male,Joseph M. Acaba
United States,male,Loren Acton
United States,male,James Adamson
Soviet Union Russia,male,Viktor M. Afanasyev
Kazakhstan,male,Aydyn Aimbetov
United States,male,Thomas Akers
Japan,male,Toyohiro Akiyama
```

`^ *(.+) (male|female) (.+?)($|, | \().*`

Note: the expression will also work without the leading `^` 

