## Part 2 Answers

Answers to exercises in part 2 of the regular expressions workshop.  [Part 2 materials](part2.html)

One answer is provided.  Other regular expressions may also fulfill the exercise criteria.


### EXERCISE 1

`\w+y\b`

Last word that matches is: `Ashby`


### EXERCISE 2 

`^ *`

### EXERCISE 3A

`^ *(.)`


### EXERCISE 3B

`^ *(.+?) (male|female)`


### EXERCISE 4

#### Part 1

`(, | \()`

#### Part 2

`^ *(.+) (male|female) (.+?)($|, | \()`

Note: the expression will also work without the leading `^` 

Replacement Expression: `$1,$2,$3`

