# Asciidoc Table Formatter

This web tools helps to format the [table syntax in asciidoc](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/#tables).

Demo site in [here](https://asciidoc-table-formatter.github.io).

## Usage:

1. Create table in google spreadsheet
2. Add cell modifier with a pair of `#` before value in the cell needed
  * E.g. If the cell have value "111" and if you want the cell with col span=2, change cell value to "#2+#111"
3. Add #0# before cell value if you don't want to have pipe character due to row span / col span
4. Add the asciidoc format in the cell e.g. "[blue]#value#"
5. Click Format

## Example:

Input:
```
header1	header2	header3
#2+#1	#0#2	#a#3
aaa	#.2+#bbb	ccc
4	#0#5	6
```

Output by clicking Format button:

```
[cols="7s,7,7", options="header"]
|===
  |header1    |header2  |header3
2+|1           2       a|3      
  |aaa     .2+|bbb      |ccc    
  |4           5        |6      
|===
```

## Constriant

Since the multiple line in google spreadsheets is troublesome, this formattor does not support multiple line content

Instead, you can state `:br: pass:[<br/>]` as [AsciiDoc attribute](https://www.methods.co.nz/asciidoc/chunked/ch28.html), then you can state something like `line1{br}line2` in the cell in google spreadsheets and render as multiple line.

To see more about how to insert sequential blank lines, please visit [this page](https://github.com/asciidoctor/asciidoctor/wiki/How-to-insert-sequential-blank-lines).
