## sequence
### order
```
{
"origin": "#1# #2# #3# #4# #5#",

"1": ["0 een", "0 un", "0 one"],
"2": ["00 twee", "00 deux", "00 two"],
"3": ["000 drie", "000 trois", "000 three"],
"4": ["0000 vier", "0000 quatre", "0000 four"],
"5": ["00000 vijf", "00000 cinq", "00000 five"]
}
```

### reordering
```json
{
	"origin":"#plot#",
	"plot":[
		"#1# #2# #3#",
		"#3# #4# #5#",
		"#1# #2# #3# #4# #5#",
		"#5# #4# #3# #2# #1#",
		"#1# #3# #5#",
		"#3# #1# #2# #5#"
	],
	"1":["0 een","0 un","0 one"],
	"2":["00 twee","00 deux","00 two"],
	"3":["000 drie","000 trois","000 three"],
	"4":["0000 vier","0000 quatre","0000 four"],
	"5":["00000 vijf","00000 cinq","00000 five"]
}
```
### nested plot structures
```json
{
"origin": "In this story, #plot#",
"plot": [
"#start# #1# #middle# #2#",
"#start# #1# #middle# #2# #middle# #2#",
"#start# #1# and #1# and again #1#",
"In the capital #upper# #middle# #upper#",
"Only #round# #middle# #round# #round#",
"#A# because not #a#, thus #B# and #C#, in other words #upper# instead of #lower#"
],
"start": ["first", "before", "yesterday", "now"],
"middle": ["because", "then", "and", "secondly", "finally", "after this"],

"1": ["#case#", "#case# #middle# #case#"],
"case": ["#upper#", "#lower#"],
"upper": ["#A# #B# #C#", "#A# #B#", "#B# #C#"],
"lower": ["#a# #b# #c#", "#a# #b#", "#b#  #c#"],
"a": ["a", "aa", "aaa"],
"b": ["b", "bb", "bbb"],
"c": ["c", "cc", "ccc"],
"A": ["A", "AA", "AAA"],
"B": ["B", "BB", "BBB"],
"C": ["C", "CC", "CCC"],

"2": ["#shape#", "#shape# #middle# #O#"],
"shape": ["#stripe#", "#round#"],
"stripe": ["#-# #~# #=#", "#-# #~#", "#~# #=#"],
"round": ["#o# #0# #O#", "#o# #0#", "#0# #O#"],
"-": ["-", "--", "---"],
"~": ["~", "~~", "~~~"],
"=": ["=", "==", "==="],
"o": ["o", "oo", "ooo"],
"0": ["0", "00", "000"],
"O": ["O", "OO", "OOO"]
}
```
### causal chain
```json
{
"origin":"#1#",
"1":["one #2#"],
"2":["two #3#", ""],
"3":["three #4#", ""],
"4":["four #5#", ""],
"5":["five #6#", ""],
"6":["six #7#", ""],
"7":["seven #8#", ""],
"8":["eight #9#", ""],
"9":["nine", ""]
}
```

## loops

### simple
don't forget an end exit
```json
{
"origin": "#loop#",
"loop": ["o#loop#", "0#loop#", "O#loop#", ""]
}
```

### some variation
```json
{
"origin": "#loop#",

"symbol": ["o", "0" , "O"],

"loop": [
"#symbol#.#loop#",
"#symbol##symbol#.#loop#",
"#symbol##symbol##symbol#.#loop#",
""]
}
```

### extra variation
```json
{
"origin": "#[symbol:#pattern#]loop#",

"pattern": ["o", "0" , "O"],

"loop": [
"#symbol#.#loop#",
"#symbol##symbol#.#loop#",
"#symbol##symbol##symbol#.#loop#",
""]
}
```

### with memory
```JSON
{
"origin":"#[mode:#language#]greeting#",

"greeting": [
"#language# #people#! #greeting#",
"#language#! #greeting#",
"#language# !!!"],

"people":["World", "Sybelle", "Molly", "Fanny"],

"language":["#NL#","#EN#","#FR#"],
"NL":"Hallo",
"EN":"Hello",
"FR":"Bonjour"
}
```
