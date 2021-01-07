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


