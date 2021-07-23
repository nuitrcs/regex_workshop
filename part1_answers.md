Answers to the exercises in the [Part 1](part1.html) workshop.  Additional regular expressions may meet the exercise criteria.

## EXERCISE 1

`soviet union` should not match because regular expressions are case sentisitive by default (unless you specifically set them to be case insensitive).

`female`

It should be found 2 times 


## EXERCISE 2

1. `A.a`

2. `A...n`

3. `\.`

There are 7 "."


## EXERCISE 3

1. `A.{3}n`


2. A space character followed by `{2,}`  (leading spaces don't render in code formatting correctly)


CHALLENGE: `f?e?male`

The `?` makes the letter before it optional.  The expression above would also match `fmale` or `emale` but since those aren't in our text, we won't worry about them.  

## EXERCISE 4

`United.+?s`

You could shorten "United" in the regex above and still match, but `U.+?s` will match more than just the two country names.


## EXERCISE 5

1. `\d,`

2. `[mM]oon`

It appears 4 times.

CHALLENGE: `[A-Z]\w+`
