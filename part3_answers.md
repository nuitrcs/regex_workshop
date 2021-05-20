## Case 1

`([A-Z]{2,4}): ?([0-9.]+\b)`

## Case 2

`[sS]low.{1,15}down`

If you use the case insensitive flag, then you could eliminate the `[sS]` at the beginning.  


## Case 3

`(\d{5})`

`(\d+)?(?: |^)(.+?),.+`

## Case 4

`(.+?) \((\d.+?)\)\n\n.+\n\nEffective (.+)$` with the multiline flag on

Because the pieces have commas in them, if you wanted to turn this into a csv file, you'd want to quote some of the pieces: `"$1",$2,"$3"`


