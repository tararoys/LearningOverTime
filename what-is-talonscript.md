# What is Talon Script?

Talonscript is an extremely limited

Per [this slack message](https://talonvoice.slack.com/archives/C7ERD5Q5T/p1607549480243500) 

talonscript is just

```python

<phrase>:
    call() # call an action
    print(phrase) # use the captured <phrase> as a variable
    print(phrase or '') # do null coalescing if phrase is optional and was not provided
    user.long_action_name(phrase, 1, 2, 3, 4) # call a longer action with parameters
    a = phrase # assign a variable
    b = 1 + 2 # do math (limited to a single operator per expression)
    print("{b} do some string interpolation")
```
