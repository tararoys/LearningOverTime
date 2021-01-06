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


[back to basic](Talonscript-Symbols-Cookbook.md#declaring-optional-commands)
