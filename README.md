# vim advanced cheatsheet

This is a collection of fairly advanced vim (popularly known as the 'vi editor') commands that make coding feel like a walk in the park. 

**Important note:** 

Please consider installing the latest stable version of the vim editor, preferably the gvim editor from [vim.org/download.php](https://www.vim.org/download.php)

The default vi editor that comes pre-installed on most operating systems is probably not going to be adequate for using these commands. 



# Follow a link

Position the cursor on the link and press:

```
Ctrl + ]
```

# Multiple windows

Edit more than one file at the same time.

*pre: Open a file in vim*

```
:split secondFile.txt
```

## Switching between files in multiple window mode

Cursor remains on the first file that was open (always on the top). To switch to the second file (always on the bottom):

*Switch down:*
```
Ctrl + Wj
```

*Switch up:*
```
Ctrl + Wk
```

# Open a file using wildcard filename

*Open pom.xml using wildcard*
```
:e pom*
```

Open a file anywhere in the diretory tree: 

*In this case, consider AppTest.java is located in src/test/.../AppTest.java*
```
:e AppTest*
```

# Open files using :args

Open multiple similarly named files, one after another.

*In this case, consider three files named*
1. AppTest.java
2. AdditionTest.java
3. SubtractionTest.java 

*in src/test/ subfolders*

```
:args *Test.java
```

The first file that matches the wildcard is opened.

## Switch between multiple open files

1. Go to next file on the list:
```
:next
```

2. Go to the previous on the list:
```
:previous
```

3. Go to the first file on the list:
```
:first
```

4. Go to the last file on the list:
```
:last
```

5. Show the list of files:
```
:args
```

# Searching through multiple files

Look at all occurrences of a word in your project:

*In this case, look at occurrences of the keyword softAssertions in all Test java files*

```
:vimgrep /softAssertions/ **/*Test.java
```

The file with the first occurrance of the keyword opens with the cursor on line 1.

1. Go to next occurrence of the keyword

Opens the next file that has the keyword.
```
:cnext
```


2. Go to the previous occurrence of the keyword
```
:cprevious
```

# Automatic spell checking

To enable automatic spell checking:

```
:set spell
```

Any misspelled lines in the text will be highlighted

## Correct a spelling error

Move the cursor to the incorrectly spelled word and execute the command **z=** to display a list of suggested possible corrections.

# Auto-completion

Type the first part of a word and press **Ctrl + p** and the editor will complete it for you.

If more than one word matches, the editor will display a list of words. Toggle through the list of words using **Ctrl + p** (previous word) and **Ctrl + n** (next word) and select the word you want.

# Diff between two files

From the command prompt, execute:

```
vimdiff file1.txt file2.txt
```

The two files are opened side-by-side in the editor. 

To switch between the two files:
```
Ctrl + W h # Switch to left side
Ctrl + W l # Switch to right side
```

To move a chunk of text to the current file:
```
do # diff obtain
``` 

To move a chunk of text to the next file:
```
dp # diff put
```

## Patchmode to backup files when using gvimdiff

The following vi editor command will enable automatic backup of the files being diff'ed (not a real english word).

***Example**: a file named testfile.txt will be backed up as testfile.txt.old by gvimdiff*

```
:set patchmode=.old
```
**Note:** After editing code, one can perform a code inspection by diff'ing (ya, I said it!) the latest file against the .old file.

