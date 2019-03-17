---
layout: default
title: vi
parent: Editors
nav_order: 1
---

# vi Cheatsheet

---

## File management (command mode)

| Command               | Description           |
|:----------------------|:----------------------|
| `vi filename`         | open file to edit     |
| `:w`                  | save                  |
| `:wq` or `:x` or `ZZ` | save & quit           |
| `:q`                  | quit                  |
| `:q!`                 | quit without saving changes     |

---

## Deletion (command mode)

| Command               | Description                    |
|:----------------------|:-------------------------------|
| `x`                   | delete a single character      |
| `D`                   | delete the rest of the line    |
| `dd`                  | delete the entire current line |
| `ndw`                 | delete the next n words        |
| `:q!`                 | delete the next n lines        |
| `:x,yd`               | delete from line x through to line y |


---

## Copy & Paste (command mode)

| Command               | Description                     |
|:----------------------|:--------------------------------|
| `yw`                  | yank (copy) current  word       |
| `yy`                  | yank current line               |
| `y$`                  | yank to the end of current line |
| `p`                   | paste the clipboard content     |
