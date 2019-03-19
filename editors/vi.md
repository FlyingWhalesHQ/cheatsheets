---
layout: default
title: vi
parent: Editors
nav_order: 1
---

# vi Cheatsheet

---

## File management

| Command               | Description                 |
|:----------------------|:----------------------------|
| `vi filename`         | open file to edit           |
| `:w`                  | save                        |
| `:wq` or `:x` or `ZZ` | save & quit                 |
| `:q`                  | quit                        |
| `:q!`                 | quit without saving changes |

---

## Movement

| Command | Description           |
|:--------|:----------------------|
| `h`     | move left one character     |
| `j`     | move down one character    |
| `k`     | move up one character           |
| `l`     | move right one character    |
| `w`     | move forward one word     |
| `b`     | move to the start of current word     |
| `e`     | move to the end of current word     |
| `(`     | move back one sentence     |
| `)`     | move forward one sentence     |
| `^`     | move to the beginning of current line     |
| `$`     | move to the end of current line     |
| `{`     | move to start of previous paragraph or code block     |
| `}`     | move to end of next paragraph or code block     |
| `Ctrl+F`| move forward one screenful     |
| `Ctrl+B`| move backward one screenful     |
| `<n>G`  | move to the nth line     |
| `G`     | move to the last line     |
| `gg`    | move to the first line     |
| `%`     | move to the matching bracket     |
| `t<char>` | move forward until the next occurrence of the character     |
| `f<char>` | move forward over the next occurrence of the character     |
| `T<char>` | move forward until the previous occurrence of the character     |
| `F<char>` | move forward over the previous occurrence of the character     |

---

## Search and Replace

| Command                 | Description                    |
|:------------------------|:-------------------------------|
| `/pattern`              | search for _pattern_                                 |
| `n`                     | find the next occurrence of _pattern_                |
| `:%s/pattern/replace/g` | replace every occurrence of _pattern_ with _replace_ |

---

## Deletion

| Command               | Description                    |
|:----------------------|:-------------------------------|
| `x`                   | delete a single character      |
| `D`                   | delete the rest of the line    |
| `dd`                  | delete the entire current line |
| `ndw`                 | delete the next n words        |
| `:q!`                 | delete the next n lines        |
| `:x,yd`               | delete from line x through to line y |


---

## Copy & Paste

| Command               | Description                     |
|:----------------------|:--------------------------------|
| `yw`                  | yank (copy) current  word       |
| `yy`                  | yank current line               |
| `y$`                  | yank to the end of current line |
| `p`                   | paste the clipboard content     |
