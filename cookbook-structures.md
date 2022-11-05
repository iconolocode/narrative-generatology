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
> 0 one 00 two 000 drie 0000 four 00000 vijf
 
> 0 een 00 deux 000 trois 0000 quatre 00000 five

> 0 een 00 two 000 drie 0000 vier 00000 vijf

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
> 000 three 0000 four 00000 cinq

> 000 drie 0 one 00 deux 00000 five

> 00000 cinq 0000 vier 000 three 00 deux 0 un

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
> In this story, Only o 000 secondly 00 OO 000 O

> In this story, A because not a, thus BBB and CC, in other words B CC instead of bb cc

> In this story, first aaa bb and b c and again aa bb ccc

> In this story, now A BBB CCC finally AAA B and o 0 OO after this -- ~~ because O

> In this story, In the capital AA B CCC because AAA BBB

### causal chain

note: the further, the rarer.
tip: by multiplying an option, it has more chance to happen (`["two #3#", "two #3#", "two #3#", ""]` the "" to break the chain has less chance to happen now)

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
> one two

> one two three four five

> one

## loops

### simple
don't forget an end exit
```json
{
"origin": "#loop#",
"loop": ["o.#loop#", "0.#loop#", "O.#loop#", ""]
}
```
> 0.o.0.0.o.O.

> O.o.O.0.O.O.0.0.0.0.o.O.O.0.

> 0.0.O.

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
> 0.oo.

> 0.OoO.O00.

> o0.Ooo.0.

### constrained variation
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
> 0.00.0.

> 000.00.

> ooo.ooo.oo.o.o.ooo.ooo.ooo.

### with memory
```JSON
{
"origin":"#[language:#mode#]greeting#",

"greeting": [
"#language# #people#! #greeting#",
"#language#! #greeting#",
"#language# !!!"],

"people":["World", "Sybelle", "Molly", "Fanny"],

"mode":["#NL#","#EN#","#FR#"],
"NL":"Hallo",
"EN":"Hello",
"FR":"Bonjour"
}
```
> Bonjour World! Bonjour !!!

> Bonjour World! Bonjour! Bonjour World! Bonjour! Bonjour !!!

> Hello World! Hello Fanny! Hello !!!

## Probabilities
### simple probabilities
```json
{
"origin": "#probability#",
"rareSymbol": "*",
"probability": ["#rareSymbol#","","","",""]
}
```
Rare symbol has a probability of one chance of five to happen

### memorize probability options
```json
{
"origin": "#[rare:#rareSymbol#][common:#commonSymbol#]array#",
"rareSymbol": ["*", "$", "@"],
"commonSymbol": [".",",","-"],
"array": "#p# #p# #p# #p# #p# #p# #p# #p# #p# #p# ",
"p": ["#rare#","#common#","#common#","#common#","#common#"]
}
```
> - - - - - * - - * -

> , @ @ , , , , , , ,

> $ - $ $ - - - - - -

## formatting

### general

- HTML tags / inline css can be incorporated
- To make linebreaks use </br>

### mini template
```json
{
"origin": "<center>#verse#</br>#verse#</br>#verse#</br>#verse#</br>#verse#</br></center>",
"verse": [
"#sound#",
"#sound##sound#",
"#sound##sound#"
],
"sound": ["li", "...", "lalala", "LalalLaLa", "LALALA"]
}
```

### apply tags
```json
{
"origin": "#formatting#",
"formatting": [
"<b>#greeting#</b>",
"<i>#greeting#</i>",
"<u>#greeting#</u>",
"<h2>#greeting#</h2>",
],
"greeting": ["hello", "bonjour", "hallo"]
}
```
> <b>bonjour</b>

> <u>hallo</u>

> <i>bonjour</i>

### escaping characters
double quotes are needed and recignized both in the JSON and HTML syntax.
Use the double quotes for the Tracery grammar, and inside the strings use single quotes or escape the double quotes with a backslash.
```json
{
"origin": "#formatting#",
"formatting": [
"<font color = 'red' >#greeting#</font>",
"<font color = \"blue\" >#greeting#</font>",
"<font color = \\\"lightgreen\\\" >#greeting#</font>"
],
"greeting": ["hello", "bonjour", "hallo"]
}
```
