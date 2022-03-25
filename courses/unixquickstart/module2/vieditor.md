---
title: Working with vi editor
include_in_preview: false
---

### Vi editor 

When you work on Linux server vi is the default text editor you will find. The oldest and most commonly used text editor. Vi is visual editor, you can use only keyboard and perform text editing operations.

vi works on two modes.

1. Command Mode - where all the key strokes are treated as commands and executed on the text file.

2. Insert Mode - in this mode whatever you type will get recored/inserted in the file.

#### Vi examples 

```Esc``` is used to go to command mode

Some commands will take you to edit mode

Lets see step by step how to work with vi editor. 


### Creating file 

We can create file using ``` vi filename``` it will display editor as follow 

```
vi filename
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
"filename" [New File]
```
+ Please note when we use filename to start vi editor, if file exist it will open it else vi will create the file and open it.

+ If we start vi editor without specifying the file name then while saving you can specify the name

Now we have created the file lets edit it. 

Vi starts the editor in command only so all the keystrokes are now considered as commands no they are not inserted in the file. 

To go to insert mode you can user following commands

1. i - To insert before the cursor position 
2. o - Open a line below the current line 
3. O - Open a line above the current line

Lets follow the instructions to create file, edit it and use curson movement keys.

Step 1 : Start vi editor using ```vi filename```

Step 2 : Press ```i``` once, you wont see anything on screen but mode is changed to insert mode 

Step 3 : Type following lines in the editor 

```
Hello This is vi editor 
This is first time i am using it 
~                                                                              
~                                                                              
~ 
~                                                                              
"filename" [New File]
```

Use only use enter button to insert new line, not mouse or any other button.

Step 4 : Once the lines are typed go back to command mode using ```Esc``` button

Now you know how to open file and swithc to insert mode using ```i``` and come back to command mode.

Lets now use cursor movement keys. You can move your curson in command mode using the following keys 

1. H - Move to upper Left corner 
2. M - Move to middle line 
3. L - Move to lower left corner
4. h - Move to one char back
5. j - Move to down a line
6. k - Move to up one line 
7. l - Move to one char forward
8. ^ - Move to beginning of line
9. $ - Move to end of the line 
10. w - Move one word forward 
11. b - Move one word backword 


Try to practice all above keys to move your cursor in the file.

You will be able to do it very quickly once to practice enough.


Lets now also use the small ```o``` and Capital ```O``` to insert line belo and above the curson positions

Go to the last line of the file using cursor movement keys and use ```O``` to insert line, your mode is now changed to insert mode and you can type in the file.

Remember once you finish typing press ```esc``` to go back to command mode.

Similarly you can also do ```o``` to insert line below the curson position.

Now you lets move forward and save the file.

Step 1 : You must be in command mode to save file. Press ```Esc``` if you are not in command mode.

Step 2 : User ```:w``` to write changes to file. Editor will tell you few charactors are wrtten in the file. 

Step 3 : If you have not give name of file then while saving you have to specify file name as ```:w filename```

Step 4 : If you want to quite from file then use ```:q``` command.  You can only use it if you have saved all your work. 

Step 5 : To save your work and quite from vi you can combine command like ```:wq```

Step 6 : To quit without saving your work use ```:q!```


Summary of file saving commads 

1. :w - to save file 
2. :w filename - specify the file name in which we want to save
3. :wq - Save and quite file 
4. :q! - quite vi without saving the file


Lets now see window movement commands and how to use them

To see the effect of window movement commands we will need a file with good amount of content in it, We can make use of Lorem Ipsum website to get dummy content. 

So lets go to https://www.lipsum.com/ and copy content in file 

Once you save the file, go back to command mode and use following keys to scroll through screen content and do a pattern search 

1. <ctrl>d - Scroll down (half a screen)
2. <ctrl>u - Scroll up (half a screen)
3. <ctrl>f - Page forward
4. <ctrl>b - Page backward
5. /string - Search Forward 
6. ?string - Search backward
7. n - Repeat search forward 
8. N - Repeat search reverse
9. G - Go to last line
10. :n - Go to line number n

Note : you can use ```:set number ``` to see the line numbers in the vi editor, and use Ctrl + g to see the current line number 

Lets now see how we use delete commands, all these commands will be used in the command mode.

1. dd - to delete entire line under the cursor ( acts like cut)
2. ndd - n is number of lines to delete from the cursor position ( acts like cut)
3. dw - delete the word under the cursor ( acts like cut)
4. dnw  - delete n words from the cursor
5. d) - delete till the end of the sentance 
6. db - delete previous word 
7. D - delete to end of the line 
8. x - delete the character under the cursor

Note first three  commands acts like cut means you can paste the deleted content using paste commands which are as shown below 

Lets see copy and paste commands 

1. yy or Y - to copy the line 
2. yw - copy word 
3. p - Paste after the cursor
4. P - Paste before the cursor 

Undo commands are as follows 

1. u - undo last change 
2. U - undo all changes on the line 


Finally we will see search and replace commands 
The syntax for the search and replace command is as follows 

```[address]s/old_text/new_text/```

Address or addresses can be specified as follows 
    . --> specifies current line 
    n --> specifies Line number n
    .+m -->current line + m lines 
    $ --> Last line 
    /string/ --> Line containing the string 
    % --> Entire file 

Lets see some of te examples so that you know how to use the find and replace 

Example 1 : Search for the first occurrence of the string apple in the current line and replace it with banana
    ```:s/apple/banana/```


Example 2 : Replace all occurrences of the search pattern in the current line
      ```:s/apple/banana/g```

Example 3 : Search and replace the pattern in the entire file
          ```:%s/apple/banana/g```

Example 4 : Search and delete the pattern 
          ```:%s/apple//g```


### Excercise 

1. Create file helloVi.txt using vi editor

2. Type 5 lines in the file as shown following 

    ```
    Now the tide has receded
    And the sand is coated in bitter salt
    From tears of loss and recrimination.
    Time like the tide will wash away tears
    But will never be able to fill the empty heart
    ```

3. Save file and exit the vi 

4. Open helloVi.txt file and make wash work Capital from 5 line

5. Set line numbers in the vi editor 

6. Convert the tears to fear using search and replace in vi 

7. Delete the 3rd line 

8. Copy paste the 4th line and paste below the last line

