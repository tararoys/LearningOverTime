# Talonscript Symbols Coobook Long Version

### Declaring the most basic kind of voice command.

```
plus: "+"
```

This means when you say "plus", Talon will type the plus sign + 

The technical term for this is called declaring a voice command.  A voice command is a key-value pair.  A key-value pair is two things usually connected in such a way that the value is accessed using the key.  

In this case, the plus to the left of the colon is the key.   The "+" to the  right of the colon is the value.  When you say the key on the left talon types out what is in the quotation marks on the right.

 What is on the left is the string literal "+"  A string literal is a set of letters (more generally, characters) enclosed in double quotation marks.  String literals are used to represent what you want talon to type out.  More specifically, talon types out, character by character, the sequence of characters inside the double quotation marks of the string literal. 


[back to basic](Talonscript-Symbols-Cookbook.md#declaring-the-most-basic-kind-of-voice-command)

### Declaring Optional Commands

```
question [mark]: "?"
```

If you put a word in square brackets, that means the word is optional.  So if you say "question" or "question mark" talon will type out a question mark.  


There appears to be an ongoing debate about whether [optional rules should even be allowed in talon.](https://talonvoice.slack.com/archives/C9MHQ4AGP/p1608013506415600)  

To quote @aegis


>which makes me think of yet another reason to not allow them, if you define a capture such as
>
>```
>@mod.capture(rule="[totally optional]")
>def capture(): ...
>```
>
>then in talon file:
>
>```
>user.capture>: "test"
>```
>
>this means you have a fully optional command, so it's totally legal for that command to trigger basically all the time on its own, and it's not even obvious at the command site that this would happen (edited) 
>I can't even trivially block the command, because you can changecaptures per context, so a capture could be optional only some of the time -_-


Note: the previous 100 lines of that conversation are very interesting, too, since it contains a lengthly explanation of how the talon command parser works. 

[back to basic](Talonscript-Symbols-Cookbook.md#declaring-optional-commands)

### Declaring Alternative Commands with Or

```
( downscore  | underscore ): "_"
```

If you want to hoave two different commands do the same thing, you can use Or syntax.  

```( downscore  | underscore )```

means you can say "downscore" OR you can say "underscore", either one, and have it print out "_".


This is another part where I am not sure if this is fully implemented, yet.  It works, however in the slack all searches of (a | b) 

https://talonvoice.slack.com/archives/C7ENXA7C4/p1520030327000373

> the (a | b) syntax is fine

I found a [document about rules  in the slack,  thanks to 2shea](https://talonvoice.slack.com/archives/C7ENXA7C4/p1536365569000100)

[from the unnofical talon voice docs:] (https://github.com/dwighthouse/unofficial-talonvoice-docs/blob/master/docs/Rules.md#alternatives)

>Alternative words and phrases can be recognized as the same Rule by separting the options with a pipe ("|"). For now, Alternatives have to be contained within a Grouping set of parentheses (see below).
>
>This is mostly used when there is more than one common way to describe an Action, or to provide a shorthand verbal syntax while retaining the more verbose and understandable original.
>
>This can also be useful for very similar sounding words if that word is harder to recognize.
>
>```
>    (enter | return) - Recognizes either "enter" or "return"
>    (dubquote | double quote) - Recognizes either "dubquote" or "double quote"
>    (tilde | till duh | till day) - Recognizes "tilde", in spite of alternative pronounciations
>
>

[back to basic](Talonscript-Symbols-Cookbook.md#declaring-alternative-commands-with-or)

### Multi-line Command


Talon lets you make multi-line commands.  This make what you are attempting to do easier to read.  The commands happen one after the other.  

	
> empty dubstring:  
>    '""'
>    key(left)


Each line below the command is a thing that happens one right after the other. What happens in this one is Talon writes out two quotation marks, then presses the left arrow key to put the cursor in between the two quotation marks you just placed. 

There is an assertion that talonscript [can do only one operation per line)[https://talonvoice.slack.com/archives/C7ENXA7C4/p1603387567303400]

>rntz:ocean:  12:26 PM
I think talonscript only allows one operation per line? try using an intermediate variable
>
>You can't mix the syntax of a single line command with a multi-line command.  

For example, this gives an error, as described in this [slack message](https://talonvoice.slack.com/archives/G9YTMSZ2T/p1593673661414300): 

>```
>Trader name: key(tab)
>	insert("trader aa")
>	key(tab)
>	insert("password")
>	key(tab enter)
>```
>
>aegis:talon:  2:07 AM
>ah, you're missing the newline after the :
>2:07
>you either get single-line commands or multi-line commands, you can't mix the syntax in a single command (edited) 
>

[back to basic](Talonscript-Symbols-Cookbook.md#multi-line-command)

### Variables

You can use variables to hold values in talonscript.  

```
angle this: 
    text   =  edit.selected_text()
    user.paste("<{text}>")
```

Text is a variable.  A variable is like a box you can put things in to use later.  

In this case, it takes text that has been selected and stores it in our text variable.  In the next line, in order to paste over the select text, you use the user.paste command.  The {} is interesting, because that is a signal to talonscript to go look for a variable called 'text' inside the parentheses and insert it's value into the string. 



Here's someone [discovering variables for the first time](https://talonvoice.slack.com/archives/G9YTMSZ2T/p1586803914443300)

>Grue
>ah now I understand; was confused about the "variable in talon script" part
>
>aegis:talon:  1:52 PM
>what do you mean by that
>oh
>
>right
>
>yeah talonscript has variables and expressions
>
>Grue  1:52 PM
>named variables too?
>
>aegis:talon:  1:52 PM
>```
>test <phrase>:
>    x = phrase + "a"
>    y = phrase + "b"
>    insert(x + y)
>```
>
>Grue  1:52 PM
>this works ???? nobody told me that o_O

The strings Talon uses appear to be (based off Talon strings)[https://talonvoice.slack.com/archives/G9YTMSZ2T/p1604380817292900].

> Nov 2nd 2020
> - now format strings are properly type checked and interpreted as TalonScript (now that it's fixed, I feel safe saying the original implementation was to run them as python with eval() -_____- which is why it was super janky, had terrible error messages, and couldn't be type checked haha)

Snce the strings were run in python with eval(), which [allows you to evaluate arbitrary Python expressions](https://realpython.com/python-eval-function/), I feel safe to assume that talon strings and python strings are closely related.  

Talon strings look like [python f-strings](https://matthew-brett.github.io/teaching/string_formatting.html), except without the need to put an f in front of them. 


[back to basic](Talonscript-Symbols-Cookbook.md#variables)
### Comments 

```
#ellipses: "…"
```

If you have a piece of talonscript that isn't really working, you can comment it out by putting a hash in front of it.  

After testing, it appears that commands of the form 

```
try out : "hello world" #try to print hello world 
```

do not work, so you cannot comment on your talonscript on the same line as a script. 

This also does not work:  

```
try out command: 
	"test" #commemt
```

it gives an "

```
Line: 1, Column: 8 - unexpected token
      "test" #test
             ^"
```

###How to Write a Curly Braces

```
(bracket | brace) this: 
    text = edit.selected_text()
    user.paste("{{{text}}}")
```

If you need to have a curly brace in your string, you can escape the curly brace by putting another curly brace in front of it.  Many characters have special meanings- to 'escape' a character means, "No, don't do the special meaning when you see the character, just write it out."



```
inside (bracket | braces): 
	insert("{}") 
	key(left)
```

It is interesting that you do not need to escape braces in the above command. I assume this is because a pair of empty braces without anything inside it is interpreted as a string.  
