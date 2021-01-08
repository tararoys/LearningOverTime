# Talonscript Symbols Cookbook


### Declaring the most basic kind of voice command.

```
plus: "+"
```

This means when you say "plus", Talon will type the plus sign + 

[read more](talonscript-symbols-cookbook-long-version.md#declaring-the-most-basic-kind-of-voice-command)

### Declaring Optional Commands

```
question [mark]: "?"
```

If you put a word in square brackets, that means the word is optional.  So if you say "question" or "question mark" talon will type out a question mark.  

[read more](talonscript-symbols-cookbook-long-version.md#declaring-optional-commands)

### Declaring Alternative Commands with Or

```
( downscore  | underscore ): "_"
```

If you want to have two different commands do the same thing, you can use Or syntax.  

```( downscore  | underscore )```

means you can say "downscore" OR you can say "underscore", either one, and have it print out "_".


[read more](talonscript-symbols-cookbook-long-version.md#declaring-alternative-commands-with-or)

### Multi-line Command

If you are doing something more complex in Talon, you can use multi-line commands.  

``` 
empty dubstring:  
    '""'
    key(left)
```

Each line below the command is a thing that happens one right after the other. In this one Talon writes out two quotation marks, then presses the left arrow key to put the cursor in between the two quotation marks you just placed. 

[read more](talonscript-symbols-cookbook-long-version.md#multi-line-command)

### Variables

You can use variables to hold values in talonscript.  

```
angle this: 
    text   =  edit.selected_text()
    user.paste("<{text}>")
```

Text is a variable.  A variable is like a box you can put things in to use later.  

In this case, it takes text that has been selected and stores it in our text variable.  In the next line, in order to paste over the select text, you use the user.paste command.  The {} is interesting, because that is a signal to talonscript to go look for a variable called 'text' inside the parentheses and insert it's value into the string. 

[read more](talonscript-symbols-cookbook-long-version.md#variables)

### Comments 


```
#ellipses: "…"
```

If you have a piece of talonscript that isn't really working, you can comment it out by putting a hash in front of it.  

###

```
(bracket | brace) this: 
    text = edit.selected_text()
    user.paste("{{{text}}}")
```

If you need to have a curly brace in your string, you can escape the curly brace by putting another curly brace in front of it.  Many characters have special meanings- to 'escape' a character means, "No, don't do the special meaning when you see the character, just write it out."

