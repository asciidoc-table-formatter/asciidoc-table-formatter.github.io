# Asciidoc Table Formatter

This web tools helps to format the [table syntax in asciidoc](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/#tables).

Demo site in [here](https://asciidoc-table-formatter.github.io).

## Usage:

1. Create table in google sheets and add contents
    * You can add following characters inside the google sheets cell for specific operations:
        * Add the asciidoc format in the cell e.g. "[blue]#value#" will make the content "value" becomes blue (which is AsciiDoc syntax)
        * Add cell modifier with a pair of `#` before value in the cell needed
            * E.g. To set the cell with col span=2 (which is `2+|<content>` in asciidoc syntax), change cell value in google sheets to "#2+#<content>"
        * Add #0# before cell value if you don't want to have pipe character due to row span / col span
2. Inside google sheets, drag the cells you want to format and copy it.
3. Clear this textbox and paste the selection inside this textbox, the pasted content should be tab-separated.
4. Click "Format" button. The AsciiDoc table should be created.

In short:

![Instructions](https://github.com/asciidoc-table-formatter/asciidoc-table-formatter.github.io/blob/master/Instruction.jpeg?raw=true)

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

## Limitation:

* Content in each cell inside google sheets must be in single line only, otherwise this tool cannot render correctly
    * E.g. If you want to have newline you can state `:br: pass:[<br/>]` as [AsciiDoc attribute](http://asciidoc.github.io/asciidoc/chunked/ch28.html), then you can state something like line1{br}line2 in the cell in google spreadsheets and render as multiple line.

To see more about how to insert sequential blank lines, please visit [this page](https://github.com/asciidoctor/asciidoctor/wiki/How-to-insert-sequential-blank-lines).
