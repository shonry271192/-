---
title: Fancy Terminal
---
All Hacker's movies have one thing in common which attract us the most is computer terminal that feeds continuous text. Here, I have a simple script that resembles those fancies a very little.
{%highlight bash linenos%}
function fetch {
while [ 0 ] 
do wget -qO - http://www.commandlinefu.com/commands/random/plaintext | \
grep -v questions/comments | \
grep -v ScriptRock.com |  \
pv -q -L 9
sleep 1s
done
}
{%endhighlight%}
Append this script in `.bashrc` file and source the same to see the magic like this.
&nbsp;

![hacker](img/hacker.gif)
