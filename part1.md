These materials are for the first part of the regular expression workshop.

## What are regular expressions?

Regular expressions are patterns we can use to search text.  These patterns are built using a special syntax that allows us to express different concepts, such as character classes, repetition, and the beginning and end of text.  This syntax can vary across different implementations of regular expressions (in different programming languages), but there are some common components.  

Regular expression is often shortened to regex (say: reg-ex).  

### Why use regular expressions?

Regular expressions let us extract information from text or change text when 1) there is some structure, but 2) the specific content may vary.  

For example, if we're working with tweets:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Looking for <a href="https://twitter.com/hashtag/EarthDay?src=hash&amp;ref_src=twsrc%5Etfw">#EarthDay</a> fun? Look no further!<br><br>Register for our all-day event: <a href="https://t.co/OVnjNU2ZXb">https://t.co/OVnjNU2ZXb</a><br><br>Set a reminder to watch on <a href="https://t.co/z1RgZwQkWS">https://t.co/z1RgZwQkWS</a>:<br>🛰️ 11am ET - Q&amp;A with astronauts in space, hosted by <a href="https://twitter.com/ShawnMendes?ref_src=twsrc%5Etfw">@ShawnMendes</a><br>🌳 3pm ET - <a href="https://twitter.com/hashtag/NASAScience?src=hash&amp;ref_src=twsrc%5Etfw">#NASAScience</a> Live Q&amp;A with <a href="https://twitter.com/NASAClimate?ref_src=twsrc%5Etfw">@NASAClimate</a> experts <a href="https://t.co/B6WnYYHcBl">pic.twitter.com/B6WnYYHcBl</a></p>&mdash; NASA (@NASA) <a href="https://twitter.com/NASA/status/1385241483201110016?ref_src=twsrc%5Etfw">April 22, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

How do we get the links or hash tags out?  We know there are links and hash tags.  We can identify them with `@` or `#`, which provides some structure.  But the content (the specific link or hash tag) differs.

The data we're going to work with is copied from a [list of astronauts from Wikipedia](https://en.wikipedia.org/wiki/List_of_space_travelers_by_name
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

How do we get this into a format that we could use?

## Concept 1: Fixed Matches

## Concept 2: Match Anything

## Concept 3: Character Classes

## Concept 4: Predefined Character Classes

## Concept 5: Repetition
