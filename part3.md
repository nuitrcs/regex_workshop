## Regular Expressions Workshop: Part 3

These materials are for part 3 of the regular expressions workshop.  

* [Part 1 materials](part1.html)
* [Part 2 materials](part2.html)

You may find [this cheatsheet](https://paulvanderlaken.files.wordpress.com/2017/08/davechild_regular-expressions.pdf) to be a useful reference.

## Intro

This session of the workshop series focuses on putting the pieces from [Part 1](part1.html) and [Part 2](part2.html) together.  Learning the individual components is the first step to writing regular expressions, but interesting things can happen when you start to combine multiple pieces together.  It's also a significant step up in difficulty to start matching text in real situations.

How do we write complex regular expressions?

1. Try to define what you're looking for (to extract, replace, or match).
2. Try the expression and see what it matches.
3. If it matches too much, how can you make the expression more specific to exclude data you don't want?  If it doesn't match everything you want, why not?
4. Iterate.  

Remember: you're generally going to be using regular expressions as part of a programming language.  So there may be other strategies you can use for cleaning up your results, and you may be able to write multiple regular expressions if you want to match multiple pieces of information -- you don't have to write one expression to capture it all at once.

There's no one "right" regular expression -- it depends on the specific text you're working with.  Getting an expression that works for your data is the goal.


## Case 1

A hypothetical sentence from a news report on the stock market.  

```
Some of the prices were as following TSLA:749.50, ORCL: 50.50, GE: 10.90, MSFT: 170.50, BIDU: 121.40.
```

**Goal:** Extract two pieces of information: stock ticker and price.  


### Reminders

To match an actual period, you will want to escape it: `\.` because `.` alone matches any character.  However, inside a character set `[]`, you can put a `.` without escaping it (because you can only have literal characters inside `[]`).  

To make a character optional, follow it with `?`

Match word boundaries with `\b`


### EXERCISE

[Open the RegExr tool with this text](http://regexr.com/5tac5)

Write a regular expression to extract the ticker and the price.  

Done early?  Try [Regex crossword](https://regexcrossword.com/)


## Case 2

Processing peer feedback given on presentations - find comments that indicate the presenter needs to slow down.  

```
He should slow down a bit.
It would have been easier to understand if she slowed down. 
Slowing down will help them be more effective.
He talked too fast - try slowing down
Slow your pace down a little
We went too slow.
The pace was just right - not too slow or too fast.
Slow and steady is a good approach, but put your notes down when you speak.
```

**Goal:** Match the first 5 lines (containing a variant of slow and down near each other) and not the last 3.

### Reminders

Use `{}` to specify the number of times the previous character (or group) should match.  For example: `z{2,}` would match 2 or more z's.  

Regular expressions are case sensitive.  Use the case insensitive flag, or if you only care about one character, you can do something like: `[aA]`.  

### EXERCISE

[Open the RegExr tool with this text](http://regexr.com/5tc33)

Write an expression to match the first 5 lines and not the last 3.  

Done early?  Try [Regex crossword](https://regexcrossword.com/)



## Case 3

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

**Goal:** Extract three groups from the data above: house/street number, street name, zip code.

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

Once you've extracted these values, you can strip out the unwanted spaces.

### EXRECISE

[Open the RegExr tool with this text](http://regexr.com/5taau)

We'll get the 3 pieces of information in two steps:

* Write an expression to find any zip codes.
* Write an expression to extract the house/street number AND street name as two separate pieces of information (capture with two different groups).

For both steps, remember to use the bottom pane to write an expression to display the groups (click on "List" instead of "Replace").  Example List expression: `$1, $2`

Done early?  Try [Regex crossword](https://regexcrossword.com/)


## Case 4

Here is a part of a list of Illinois executive orders related to COVID-19, from [here](https://www.dph.illinois.gov/covid19/governor-pritzkers-executive-orders-and-rules)

Each executive order has a title, with a code reference in (), a blurb, and then an effective date.  

```
Hospital Licensing Requirements (77 Ill. Adm. Code 250)

This rule suspends portions of the hospital licensing requirements in response to the COVID-19 pandemic and establishes standards and licenses for temporary alternate care facilities. These facilities may be run either by a licensed hospital or by the State of Illinois through one of its agencies or in cooperation with one or more federal or local government bodies.

Effective April 16, 2020

Adverse Health Care Events Reporting Code (77 Ill. Adm. Code 235)

This rule suspends all requirements of the Adverse Health Care Events Reporting Code in response to the COVID-19 pandemic

Effective April 17, 2020

Health Care Worker Background Check Code (77 Ill. Adm. Code 955)

This emergency rule temporarily amends the provisions of the Healthcare Worker Background Check Code to require an individual to have their fingerprints collected within 30 days (increased from 10 working days) after being hired.

Effective April 10, 2020

Emergency Medical Services, Trauma Center, Comprehensive Stroke Center, Primary Stroke Center and Acute Stroke Ready Hospital Code (77 IAC 515)

In order to address Emergency Medical Service (EMS) staffing needs this rulemaking: authorizes Clinical Nurse Specialists to work in  hospital emergency departments designated as an Emergency Department Approved for Pediatrics (EDAP), Standby Emergency Department Approved for Pediatrics (SEDP) or Pediatric Critical Care Center (PCCC), in order to afford hospitals more flexible staffing options; helps reduce hospital staffing costs by permitting nurse practitioners, clinical nurse specialists and physician assistants to provide backup coverage during critical situations; expands the scope of the pediatric intensive care unit committee to include advanced practice providers; clarifies the role and qualifications of Pediatric Clinical Nurse Specialist; clarifies the role and qualifications of the Pediatric Clinical Nurse Expert as a member of the pediatric intensive care unit leadership team; expands the types of minimum training requirements of the Pediatric Clinical Nurse Expert to help alleviate staffing shortages and minimize costs; and updates the equipment list to reflect current medical standards.  

Effective April 10, 2020

Health Care Worker Background Check Code (77 Ill. Adm. Code 955)

This emergency rule temporarily amends the provisions of the Healthcare Worker Background Check Code to require an individual to have their fingerprints collected within 30 days (increased from 10 working days) after being hired.

Effective April 10, 2020

Emergency Medical Services, Trauma Center, Comprehensive Stroke Center, Primary Stroke Center and Acute Stroke Ready Hospital Code (77 IAC 515)

In order to address Emergency Medical Service (EMS) staffing needs this rulemaking: authorizes Clinical Nurse Specialists to work in  hospital emergency departments designated as an Emergency Department Approved for Pediatrics (EDAP), Standby Emergency Department Approved for Pediatrics (SEDP) or Pediatric Critical Care Center (PCCC), in order to afford hospitals more flexible staffing options; helps reduce hospital staffing costs by permitting nurse practitioners, clinical nurse specialists and physician assistants to provide backup coverage during critical situations; expands the scope of the pediatric intensive care unit committee to include advanced practice providers; clarifies the role and qualifications of Pediatric Clinical Nurse Specialist; clarifies the role and qualifications of the Pediatric Clinical Nurse Expert as a member of the pediatric intensive care unit leadership team; expands the types of minimum training requirements of the Pediatric Clinical Nurse Expert to help alleviate staffing shortages and minimize costs; and updates the equipment list to reflect current medical standards.  

Effective April 10, 2020

School Based/Linked Health Centers (77 Ill. Adm. Code 641)

This emergency rule extends the current certifications for school-based/linked health centers whose certifications are scheduled to expire before June 30, 2020.  The rule extends the certification for 150 days from the current expiration. In addition, it ensures that school based/linked centers can remain operational, able to provide necessary services to the communities they serve, and eligible to obtain Medicaid reimbursement. While schools are closed now some these centers continue to provide services. Without the emergency rule, the certification for some school-based/linked health centers would expire and their ability to receive Medicaid reimbursement would be in jeopardy.

Effective April 2, 2020
```

**Goal:** Extract title, code reference, and effective date and put into csv format.


### Reminders

To match a literal `(`, you need to escape it: `\(`

A new line is `\n`.  `.` doesn't match `\n` unless you turn on the dotall flag.  

`$` only matches the end of all of the text unless you turn on the multiline flag.

### EXERCISE

[Open the RegExr tool with this text](http://regexr.com/5tbv8)

Extract the three pieces of information: title, code reference (without the parentheses included), and effective date

Done early?  Try [Regex crossword](https://regexcrossword.com/)




## Answers

[Part 3 Answers](part3_answers.html) - don't cheat!  Try the exercises first.  These are for reference later.  There are other valid solutions to the exercises as well.
