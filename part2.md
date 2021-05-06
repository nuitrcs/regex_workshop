## Regular Expressions Workshop: Part 2

These materials are for part 2 of the regular expressions workshop.  [Part 1 materials](part1.html)

You may find [this cheatsheet](https://paulvanderlaken.files.wordpress.com/2017/08/davechild_regular-expressions.pdf) to be a useful reference.

## Example Text

We are going to continue to work with text copied from a [list of astronauts on Wikipedia](https://en.wikipedia.org/wiki/List_of_space_travelers_by_name
): 

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

Write a regular expression to find all words that end in a `y`.  Have your expression match the entire word, not just the ending `y`.  Hint: recall `\w` will match any "word" characters, which may help for capturing the first part of the word that isn't "y". 


## Concept 2: Beginning and End of Lines

### EXERCISE 2

## Concept 3: Groups

### EXERCISE 3

## Concept 4:

### EXERCISE 4

## Concept 5:

### EXERCISE 5
