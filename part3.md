## Regular Expressions Workshop: Part 3

These materials are for part 3 of the regular expressions workshop.  

* [Part 1 materials](part1.html)
* [Part 2 materials](part2.html)

You may find [this cheatsheet](https://paulvanderlaken.files.wordpress.com/2017/08/davechild_regular-expressions.pdf) to be a useful reference.

## Intro

This session of the workshop series focuses on putting the pieces from [Part 1](part1.html) and [Part 2](part2.html) together.  Learning the individual components is the first step to writing regular expressions, but interesting things can happen when you start to combine multiple pieces together.  

How do we write complex regular expressions?

1. Try to define what you're looking for (to extract, replace, or match).
2. Try the expression and see what it matches.
3. If it matches too much, how can you make the expression more specific to exclude data you don't want?  If it doesn't match everything you want, why not?
4. Iterate.  

Remember: you're generally going to be using regular expressions as part of a programming language.  So there may be other strategies you can use for cleaning up your results, and you may be able to write multiple regular expressions if you want to match multiple pieces of information -- you don't have to write one expression to capture it all at once.

There's no one "right" regular expression -- it depends on the specific text you're working with.  Getting an expression that works for your data is the goal.

## Case 1

This is real address data from the Evanston 311 requests line:

```
2100 Ridge Ave, Evanston, IL 60201, USA
1454 Elmwood Avenue, Evanston, IL, United States
2100 Ridge Avenue, Evanston, IL, United States
1945 Jackson Ave,Evanston, IL 60201
635 Chicago Avenue, Evanston, IL, USA
1734 Orrington Avenue, Evanston, IL, USA
1031 Ridge Ave, Evanston, IL 60202, USA
430 Elmwood Avenue, Evanston, IL, USA
1228 Oak Avenue, Unit 1, Evanston, IL, USA
901 Maple Avenue, Evanston, IL, USA
811 Emerson St,Evanston, IL 60201
1640 Chicago Avenue, Evanston, IL, USA
1720 Maple Avenue, Evanston, IL, USA
1902 Green Bay Rd, Evanston, IL, USA
605 Sheridan Road, Evanston, IL, USA
820 Mulford St,Evanston, IL 60202
Davis & Orrington, Evanston, IL 60201, USA
312 Custer Ave, Evanston, IL 60202, USA
1132 Maple Ave,Evanston, IL 60202
```

### Reminder

You can make an entire group optional by putting a `?` after the `()`:

Example: 
```
The cat ate a bird.
The cat ate a blue racoon.
The cat ate a red worm.
```

Regular expression: `The cat ate a (.+?\b)? ?(.+)\.`

Group matches (`$1,$2`)
```
,bird
blue,racoon
red,worm
```

This is complicated, but the thing to focus on is the `?` after the first group -- it makes that first group optional.  So in the results, the first line has an empty string for the first group because that group didn't match anything.

This was tricky to write and not get any extra spaces in either group.  But in practice, you could include the space in the match, and then trim the white space as a secondary step:

Regular expression: `The cat ate a (.+ )?(.+)\.`

Group matches (`$1,$2`)
```
,bird
blue ,racoon
red ,worm
```

### EXRECISE

**Goal:** Extract three groups from the data above: house/street number, street name, zip code.

[Open the RegExr tool with this text](http://regexr.com/5taau)

* Write an expression to find any zip codes.
* Write an expression to extract the house/street number AND street name as two separate pieces of information (capture with two different groups).

For both steps, remember to use the bottom pane to write an expression to display the groups (click on "List" instead of "Replace").  Example List expression: `$1, $2`




