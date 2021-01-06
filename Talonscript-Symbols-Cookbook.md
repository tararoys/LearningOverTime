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

If you want to hoave two different commands do the same thing, you can use Or syntax.  

```( downscore  | underscore )```

means you can say "downscore" OR you can say "underscore", either one, and have it print out "_".


[read more](talonscript-symbols-cookbook-long-version.md#declaring-alternative-commands-with-or)