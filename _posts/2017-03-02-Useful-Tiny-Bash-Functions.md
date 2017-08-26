---
title: Useful Tiny Bash Functions
---
Super nerd people spend most of their time in CLI. As long as we use terminal for our needs, we can also unlock new features from it by appending some codes in `bashrc` file. Here are some examples which we can use.  
&nbsp;

**History auto-completion (type `sudo` and press up-arrow key, history includes `sudo` will come up)**
{%highlight bash linenos%}
bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'
{%endhighlight%}

**Countdown timer**
{%highlight bash linenos%}
function countdown(){
  date1=$((`date +%s` + $1)); 
  while [ "$date1" -ne `date +%s` ];
    do echo -ne "$(date -u --date @$(($date1 - `date +%s`)) +%H:%M:%S)\r";
    sleep 0.1
  done
}
{%endhighlight%}

**Stopwatch**
{%highlight bash linenos%}
function stopwatch(){
  date1=`date +%s`; 
  while true; 
    do echo -ne "$(date -u --date @$((`date +%s` - $date1)) +%H:%M:%S)\r"; 
    sleep 0.1
  done
}
{%endhighlight%}

**Alarm**
{%highlight bash linenos%}
alarm() {
sleep $1; 
while :; 
  do paplay /usr/share/sounds/freedesktop/stereo/alarm-clock-elapsed.oga; 
  read -t 0.01 -n 1; 
  if [ $? = 0 ]; then 
    break; 
  fi; 
  done
}
{%endhighlight%}

**Random commands from commandlinefu.com**
{%highlight bash linenos%}
cfu () { 
  wget -qO - http://www.commandlinefu.com/commands/random/plaintext | \
  sed -n '/AD/!p' | sed -n '/commandlinefu.com/!p' | tee ~/.cfu; 
  read -p "Do you want to save? (y/n) " ans
  if [ $ans == y ]; then
    cat ~/.cfu >> ~/Useful_Commands;
  fi
}
{%endhighlight%}
