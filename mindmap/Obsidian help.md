```md
# This is a heading 1
## This is a heading 2
### This is a heading 3
#### This is a heading 4
##### This is a heading 5
###### This is a heading 6
```

| Style                  | Syntax                 | Example                                  | Output                                 |
| ---------------------- | ---------------------- | ---------------------------------------- | -------------------------------------- |
| Bold                   | `** **` or `__ __`     | `**Bold text**`                          | **Bold text**                          |
| Italic                 | `* *` or `_ _`         | `*Italic text*`                          | _Italic text_                          |
| Strikethrough          | `~~ ~~`                | `~~Striked out text~~`                   | ~~Striked out text~~                   |
| Highlight              | `== ==`                | `==Highlighted text==`                   | ==Highlighted text==                   |
| Bold and nested italic | `** **` and `_ _`      | `**Bold text and _nested italic_ text**` | **Bold text and _nested italic_ text** |
| Bold and italic        | `*** ***` or `___ ___` | `***Bold and italic text***`             | **_Bold and italic text_**             |
```md
- First list item
- Second list item
- Third list item
```
```md
1. First list item
2. Second list item
3. Third list item
```
```md
- [x] This is a completed task.
- [ ] This is an incomplete task.
```
To create a nested list, indent one or more list items. You can mix list types within a nested structure:

```md
1. First list item
   1. Ordered nested list item
2. Second list item
   - Unordered nested list item
```
You can use three or more stars `***`, hyphens `---`, or underscore `___` on its own line to add a horizontal bar. You can also separate symbols using spaces.

```md
***
****
* * *
---
----
- - -
___
____
_ _ _
```
## Code
```md
Text inside `backticks` on a line will be formatted like code.
```
Text inside `backticks` on a line will be formatted like code.
To format a block of code, surround the code with triple backticks.
````
```
cd ~/Desktop
```
````
You can add syntax highlighting to a code block, by adding a language code after the first set of backticks.

````md
```js
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
````
Obsidian uses Prism for syntax highlighting. For more information, refer to [Supported languages](https://prismjs.com/#supported-languages).
```md
This is a simple footnote[^1].

[^1]: This is the referenced text.
[^2]: Add 2 spaces at the start of each new line.
  This lets you write footnotes that span multiple lines.
[^note]: Named footnotes still appear as numbers, but can make it easier to identify and link references.
```
## Footnotes
You can add footnotes to your notes using the following syntax:
```md
This is a simple footnote[^1].

[^1]: This is the referenced text.
[^2]: Add 2 spaces at the start of each new line.
  This lets you write footnotes that span multiple lines.
[^note]: Named footnotes still appear as numbers, but can make it easier to identify and link references.
```
You can also inline footnotes in a sentence. Note that the caret goes outside the brackets.
```md
You can also use inline footnotes. ^[This is an inline footnote.]
```
https://help.obsidian.md/Editing+and+formatting/Advanced+formatting+syntax