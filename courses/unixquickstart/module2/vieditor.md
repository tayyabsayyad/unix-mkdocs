---
title: Working with vi editor
include_in_preview: false
---

# Vi editor 

When you work on unix / linux server this is the default text editor you will find. The oldest and most commonly used text editor.
Vi is visual editor, you can use only keyboard and perfrom most of the text editing operations.

vi works on two modes.

1. Command Mode - where all the key strokes are treated as commands and executed on the text file.
2. Insert Mode - in this mode whatever you type will get recored/inserted in the file.

In this lession we will learn to

1. How to open and save files 
2. How to move within file
3. How to copy, paste, delete, find etc.

# Vi modes operations 

## Comand mode 

When we start the vi editor we get into the command mode, to start vi editor we use followng command 

```
vi filename.txt
```

When we use filename to start vi editor, if file exist it will open it else vi will create the file and open it.

What if use only vi and not provide the name of the file ? 

Well vi will allow you to provide file name when you try to save the file. 

