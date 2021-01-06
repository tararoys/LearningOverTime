

why talonscript is better than python


JL0w  9:07 AM
Hey, stupid question, but is anywhere the super/win key specified? As  needed in switch window:
key(win-tab)
Please excuse my english, I hope it makes sense. (edited) 






timotimo:six:  9:53 AM
https://talonvoice.com/docs/index.html#document-modules/ctrl - this has a few

Joseph Garvin  10:31 AM
dumb question: dragonfly lets me specify a sequence of keys in one call, e.g. key("c-a,x,t"). Do I need to use multiple calls in .talon files? If so I assume the pythonesq syntax means I need to put them on separate lines?

aegis:talon:  10:44 AM
You can put spaces between keys
10:44
key(a b c d)

Joseph Garvin  11:30 AM
ah nice thanks

Joseph Garvin  11:40 AM
I don't mind the talon files too much but I don't see what the advantage is over just regular key/value dicts in Python like I did with dragonfly? This just seems like yet another niche config file syntax I have to learn.
11:41
like if I'm puttting spaces this definitely isn't just "grammar: <regular_python_code>"

aegis:talon:  11:41 AM
key syntax is a one-off
11:41
99% of it is a reduction of python syntax
11:41
the overall syntax of talon files is extremely basic
11:42
command:
    x = x * 1
    action(x)
    action("{x}")
(edited)

Joseph Garvin  11:42 AM
but can I have ifs/loops/lambdas/functions/etc? like what subset of python are we talking about. yesterday I learned we have vars :slightly_smiling_face:

aegis:talon:  11:42 AM
that's about it, there's not much other syntax

Joseph Garvin  11:42 AM
I see so no control flow or anything

aegis:talon:  11:42 AM
no ifs, loops, lambdas, functions, etc
11:42
there's or to null coalesce (provide default values for optional) captures
11:42
command [<number>]:
    n = number or 1
11:43
there are significant benefits to using talon files
11:43
they are fully machine readable/writable
11:43
so I can make a gui for editing them
11:44
they are completely separate from load-bearing python, and python isn't allowed to declare commands. so when there are third party plugins, to install a plugin's grammar, talon will actually copy the plugin's talon grammar files into a central directory
11:44
which you can edit without editing the upstream plugin (edited) 

Joseph Garvin  11:45 AM
interesting

aegis:talon:  11:45 AM
I can also record macros in terms of talonscript
11:45
which, because it's a simple scripting language, we can just regurgitate into a file and you have a persistent macro
11:46
let's say you have the commands:
hello: key(1)
command two: key(2)
and you record a macro of you saying "hello command two", and save it as the command "double"
double:
    key(1)
    key(2)
11:46
you can't do that with python (with python, just one global in scope and it gets really complicated) (edited) 
11:47
talonscript is also completely statically checked from capture (inputs), through all expressions, to action calls (edited) 
11:48
also, many newcomers to talon won't know python, talonscript is simpler than python and the .talon file format is extremely hardened to user error in the command area
11:49
you can put 1mb of /dev/urandom into the middle of a .talon file without breaking anything besides the next command