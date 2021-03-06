# LearningOverTime
 
I am marking what I understand and what I don't understand on a github repository by highlighting the parts of the page I don't understand in red, the parts I partially understand in green, and the parts I completely understand in yellow.  I am doing this by adding css classes to span tags.  Each commit represents one or two new span tags highlighting something I'm paying attention to. 

If I put this repository up on github, people will see the raw source code.  It is extremely difficult to pick out <span class="dunno"> {{}} </span> from a forest of other html tags.  Especially when it's so easy to spot {{}} when it is highlighted in red.  

The solution? github has a way that you can preview html pages.  Take the github address of the page you are looking for.  Then prepend  https://htmlpreview.github.io/?
And github will kindly show you the page.  

https://stackoverflow.com/questions/8446218/how-to-see-an-html-page-on-github-as-a-normal-rendered-html-page-to-see-preview

Here is an example:

https://htmlpreview.github.io/?https://github.com/tararoys/LearningOverTime/blob/main/TarasTalonScripts_symbols.talon%20at%20main%20%C2%B7%20tararoys_TarasTalonScripts.html

It appears to take about five minutes for the external assets to appear.  

You can also use a service called https://raw.githack.com/, which produces a url like
 https://raw.githack.com/tararoys/LearningOverTime/main/TarasTalonScripts_symbols.talon at main · tararoys_TarasTalonScripts.html

This is how to do it with a private repository, but the following method creates a token at the end of the url which appears to only work once and for a short period of time.  It also does not include the css, which completely defeats the purpose.  

https://github.com/htmlpreview/htmlpreview.github.com/issues/80

