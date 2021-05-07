## Regular Expressions Workshop: Part 2

These materials are for part 2 of the regular expressions workshop.  [Part 1 materials](part1.html)

You may find [this cheatsheet](https://paulvanderlaken.files.wordpress.com/2017/08/davechild_regular-expressions.pdf) to be a useful reference.

## Example Text

We are going to continue to work with text copied from a [list of astronauts on Wikipedia](https://en.wikipedia.org/wiki/List_of_space_travelers_by_name
) that we used in Part 1](part1.html)
: 

```
    United States male Joseph M. Acaba
    United States male Loren Acton
    United States male James Adamson
    Soviet Union Russia male Viktor M. Afanasyev
    Kazakhstan male Aydyn Aimbetov, first cosmonaut by KazCosmos-selection in space
    United States male Thomas Akers
    Japan male Toyohiro Akiyama, the first business-sponsored hi space traveler and the first Japanese person in space
    Soviet Union male Vladimir Aksyonov
    Saudi Arabia male Sultan Salman Al Saud, first Saudi Arabian in space, only royal person in space, first Middle Eastern person in space
    United States moonwalked male Buzz Aldrin, flew on Apollo 11; second person to walk on the Moon
    Bulgaria male Aleksandr Panayotov Aleksandrov
    Soviet Union male Aleksandr Pavlovich Aleksandrov
    United States male Andrew M. Allen
    United States male Joseph P. Allen
    United Arab Emirates male Hazza Al Mansouri, first UAE astronaut
    United States male Scott Altman
    United States male William Anders, first Asian-born person in space (born in Hong Kong, but an American citizen)
    United States male Clayton Anderson
    United States died male Michael P. Anderson (1959–2003), died on February 1, 2003, in the Space Shuttle Columbia disaster of STS-107[7]
    (Claudie André-Deshays – see Claudie Haigneré)
    Iran United States female Anousheh Ansari, fourth spaceflight participant and first female spaceflight participant, first woman of Muslim descent in space, and first Iranian in space
    United States male Dominic A. Antonelli
    United States male Jerome Apt
    United States male Lee Archambault
    United States moonwalked male Neil Armstrong (1930–2012), flew on Apollo 11; first person to walk on the Moon[8]
    United States male Richard R. Arnold
    Russia male Oleg Artemyev
    Soviet Union male Anatoly Artsebarsky
    Soviet Union male Yuri Artyukhin (1930–1998)[9]
    United States male Jeffrey Ashby
    Soviet Union male Oleg Atkov
    Soviet Union male Toktar Aubakirov, first Kazakh born person in space
    United States female Serena Auñón-Chancellor
    Soviet Union Russia male Sergei Avdeyev
```

## Concept 1: Word Boundaries

In [Part 1](part1.html), we wrote some regular expressions that matched across words.  Sometimes, we can use spaces to denote the edges of words, but what about cases where a word is followed by punctuation, or when a word starts a line of text?  Luckily, we have a way to indicate a word boundary: `\b`.  This doesn't match a specific character.  Instead, it matches any transition between word (`\w`) and non-word (`\W`) characters.  Recall from last time that word characters are letters, digits, and underscores (it gets more complicated with non-ASCII text, but the same concept applies).

### Example

Text:
```
Alex identifies as female, and Casey identifies as male.
```

Regular Expression: `\bmale`

Matches:
```
male
```

With the word boundary `\b` at the beginning of the expression, it only matches the "male" at the end of the sentence.  It does not match the "male" in "female" like `male` without a word boundary indicator would.


### EXERCISE 1

Open the [blank example](regexr.com/5rddd). 

Write a regular expression to find all words that end in a `y`.  Have your expression match the entire word, not just the ending `y`.  Hint: recall `\w` will match any "word" characters, which may help for capturing the first part of the word that isn't "y".  Need a refresher on how to represent [repetition](part1.html#concept-3-repetition)?

Type the last word that you match in the chat when you're done.


## Concept 2: Beginning and End of Lines

Similar to how we can match the beginning and end of words, we can also match the beginning `^` and end `$` of lines.  

There are two definitions of "line" that you may encounter.  By default, a line is the full text you are matching against.  `^` matches the beginning of the full text you're matching against, and `$` is the end of the full text you're matching against.

With the "multiline" flag, you can instead specify a line is terminated by `\n`, so there can be multiple lines in the text you're matching.  

*Note: line endings are actually a bit more complicated than this.  On Windows systems, when you type ente/return, you actually get `\r\n`; with Mac/Unix, you just get `\n`.  The `\r` is a carriage return (CR).  The `\n` is a line feed (LF).  In either case, `\n` is the last character, but with Windows, there may also be a `\r`. You might see `\r\n` noted as CRLF, and `\n` as LF.*

### Example

Text:
```
This is line 1
This is line 2
This is line 3
```

Regular Expression: `.$`, **without** the multiline flag

Matches:
```
3
```

Regular Expression: `.$`, **WITH** the multiline flag

Matches:
```
1
2
3
```

### EXERCISE 2

Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

Write a regular expression to match any number of spaces (0 or more) at the beginning of each line of the text.  

Spaces are visualized in the text in the RegExr tool with a circle.  

Hint: Need a refresher on how to represent [repetition](part1.html#concept-3-repetition)?  

## Concept 3: Groups

With regular expressions, we can go beyond matching text to extracting or changing text.  When doing that, sometimes it's helpful to retrieve or identify only part of an expression, rather that the whole thing.  For example, if you want to capture text between html tags, without including the html tags.  Or information inside parentheses.  Or part of a filename.  

We denote a group with parentheses `()`.  

This means that if we want to match an actual `(` or `)` in the text, we'll need to escape it: `\(` or `\)`.  

We'll get into more detail on this shortly, but each group we include in the regular expression gets a number, starting with 1.  We can use these numbers to refer to the text that each group matches.

### Example

Text:
```
Dayton, OH
Chicago, IL
Washington, DC
San Francisco, CA
```

Regular Expression: `, ([A-Z]{2})`

The **entire expression** matches:
```
, OH
, IL
, DC
, CA
```

*Note: The regular expression above requires capital letters to make sure we're matching a state abbreviation.  But this more general regular expression would also work: `, (.{2})` (match any two characters after a comma and space) or even `, (.+)` (match 1 or more characters after a comma and a space).  Which regular expression is appropriate will depend on the specific text you're matching, and sometimes it takes some trial and error to make an expression specific enough or general enough to match everything that you want, but only what you want.*

The **group** (in parentheses) matches:
```
OH
IL
DC
CA
```


### EXERCISE 3A


Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

To see the results of the group match, instead of the entire expression, in the bottom, change `$&\n` to `$1\n`.  The `1` is for the first group in the expression you'll write.

Recall that before we wrote a regular expression to match the spaces at the beginning of the line: `^ +`

Now write a regular expression that includes a group to capture the first letter that appears after those spaces at the beginning of the line.


### EXERCISE 3B

Open the [blank example](regexr.com/5rddd).  Under the "Flags" menu in the upper left, turn on the "multiline" option (should be checked) so that the text is treated as multiple lines, not just one.

To see the results of the group match, instead of the entire expression, in the bottom, change `$&\n` to `$1\n`.  The `1` is for the first group in the expression you'll write.

Recall that we've written two regular expressions before:

* Match spaces at the beginning of the line: `^ +`
* Match male or female (challenge from Part 1): `f?e?male`

Using these components, we want to write a regular expression to capture the name of the country in each line.  The country name comes after the beginning of the line and the spaces, and before a space and then male or female.  Combine these components with a new part of a regular expression that includes a group to capture the name of the country.  Goal: regular expression that includes a group (in `()`) that will capture the name of the country.

Hint: You'll probably want a non-greedy quantifier: `.+?` will match 1 or more characters, until the next part of the expression matches.  

## Concept 4:

### EXERCISE 4

## Concept 5:

### EXERCISE 5

## Learning More

What to learn more about regular expressions?  Check out our [resource guide for free, online learning resources](https://sites.northwestern.edu/researchcomputing/2021/03/04/online-learning-resources-regular-expressions/).
