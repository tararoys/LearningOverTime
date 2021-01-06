# Talonscript Symbols Coobook Long Version

### Declaring the most basic kind of voice command.

```
plus: "+"
```

This means when you say "plus", Talon will type the plus sign + 

The technical term for this is called declaring a voice command.  A voice command is a key-value pair.  Two values usually connected in such a way that the value is accessed using the key  In this case, when you say plus you get + typed out on your computer.

The plus to the right of the colon is the key.   The "+" to the left of the colon is the value.  When you say the key talon types out what is on the left. 

 What is on the left is the string literal "+"  A string literal is a set of letters (more generally, characters) enclosed in double quotation marks.  String literals are used to represent what you want talon to type out.  More specifically, talon types out, character by character, the sequence of characters inside the double quotation marks of the string literal. 

So 

```
plus: "+"
```
can be rewritten in technical English as 

Set the key to plus and set the value to the string literal "+" 

This is the level of abstraction that explains how the programming is doing what it is doing, while 

the general english 

This means when you say "plus", Talon will type the plus sign + 

explains what they program is supposed to do. 

[back to basic](Talonscript-Symbols-Cookbook.md#declaring-the-most-basic-kind-of-voice-command)