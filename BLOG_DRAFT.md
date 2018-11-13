### How to Design a better User Experience for Software Development

#### Hint: It all begins from the terminal

In 2018, Stack Overflow released the results of their massive survey, in which over 100,000 developers told how they learn, build their careers, which tools they’re using, and what they want in a job. [Amongst the highlights](https://insights.stackoverflow.com/survey/2018/#developer-profile-developer-type), almost 60% of respondents identified as back-end developers, 48.2% as full stack developers , and 37.8% worked on Front-end. 11% of developers also worked on Sys-admin and DevOps related roles.

It’s also super interesting to note that the [choice of technology](https://insights.stackoverflow.com/survey/2018/#technology-most-popular-development-environments) for engineers who worked on the back-end —  specifically as DevOps and Sys-admins — was  vim, an editor that works on the command line.

In-fact one of the most common questions asked on Stack Overflow was on how to exit this tool. The numbers are staggering!

![](https://cdn-images-1.medium.com/max/1000/1*xEQLc6fnQtM9ZMGwgd6DQA.png)
<span class="figcaption_hack">[https://stackoverflow.blog/2017/05/23/stack-overflow-helping-one-million-developers-exit-vim/](https://stackoverflow.blog/2017/05/23/stack-overflow-helping-one-million-developers-exit-vim/)</span>

Which brings me to my next point — 

#### The average programmer spends anywhere between [9 to 12 hours](https://insights.stackoverflow.com/survey/2018/#developer-profile-how-much-time-do-developers-spend-on-a-compute ) in front of the computer.

And so, it isn’t a stretch to think that a significant portion of our development time is done using command line-based interfaces. After all, *vim* is just one tool amongst many others.

In my everyday life as Neo the computer programmer, I use the terminal for pretty much everything. Whether it’s installing software, running a Node server, running unit tests, using git for versioning, or using docker for deployment — there’s no shortage of CLIs. 

And they aren’t going away anytime soon! As a software developer, it’s the one place that you probably spend a lot of time in other than your home. Love it, hate it, but you can’t ignore it!

But why are they so important? Why do we have such a hard time using them? And most importantly, what can we do to improve their user experience, and be a faster, more productive engineer in our work? Keep reading!

### Table of Contents

* The need for terminals
* Interaction Design on the CLI
* Let’s talk about Prompts
* Introducing Enquirer

*****

To all the usability enthusiasts out there, I know what you’re thinking — 

### But wait, why even use terminals at all?

*We have GUIs for several of them, don’t we! Besides, aren’t CLIs old-fashioned?*

As a matter of fact, CLIs are pretty great for a number of reasons. Here’s a
very nice [stack exchange](https://ux.stackexchange.com/questions/101990/why-are-terminal-consoles-still-used)
thread on what makes CLIs awesome, but I’ll briefly summarize the most important points — 

* **Copying and Pasting commands are easier**

![](https://cdn-images-1.medium.com/max/800/1*kTP8SkQsI_dfra8RcwS96A.png)

<br> 

If you were to install a piece of software using a GUI, it’s gonna involve a fair amount of dragging your mouse pointer over the screen. There’s definitely a lot of cognitive overhead in knowing the right column to select, the right button to click. Point is — **you most likely can always, always type faster than using a mouse**. 

On the other hand, copying commands and pasting them is much easier. Even if I were to say, read the documentation or a blog article on how to install software using the terminal, the commands are usually highlighted on the page (so they’re a lot easier to find than other text), and I can simply copy them instead of going through the entire article.

* **More efficient**

This is an extension of the above point, but as an example — say if you wanted to make some quick changes to a file, and you already know the file name. It’s much easier to type `subl myFile.txt`, or if you're a freak, `vim myFile.txt`. Contrast that with making a carefully co-ordinated series of finger movements on the trackpad, going to your editor, clicking on File and then Open File, scrolling through the list of files/folders and finally selecting the one that you want to open. Whew!

It might not sound like much, but if you’re a software developer, you’re most likely going to be spending a lot of time opening and closing files. And may I remind you, this is just one example — I’m sure that you can think of several others!

* **More preciseness and control**

Which means, no accidental mouse clicks. Even if you pasted the wrong command, undoing them can be hell-lot-a easier by doing a *CTRL-C* or `rm -rf` or `apt-get remove`!

* **Programming**

GUI tools often tend to hide errors in-case something unexpected happen. With terminals, it is much easier to trace errors and logs when I’m able to see them all on the CLI.

* **Computing Power**

This one probably isn’t a significantly compelling reason to use CLIs, but it’s still an important one to mention. Terminal-based programs use much low CPU power, memory and computer battery than GUI based programs.

![](https://cdn-images-1.medium.com/max/800/1*nrQWTlV4E3KsHr4hzgVvbA.jpeg)
<span class="figcaption_hack">[http://www.commitstrip.com/en/2016/12/22/terminal-forever/](http://www.commitstrip.com/en/2016/12/22/terminal-forever/)</span>

**Now that you understand why they’re important, let’s talk about UX.**

### Interaction Design on the CLI

At first, it seems odd to imagine words like interaction design and #UX in the world of CLI. We often imagine well-polished apps on the web, android or iOS — you know, the ones that have a graphical user interface, using material design and icons and what not.

But as Steve Jobs once famously said — 

> “It’s not just what it looks like and feels like. Design is how it works”

A lot of developers, including myself, find the terminal to be pretty intimidating. There are no fixed standards or design systems in place — after all, who even hires a interaction designer to improve a CLI? And so understandably, sometimes the CLI can be a walk in the park, and other times, the walk might very well be inside a jurassic park — you’re frantically trying to get out! No wonder that GUI enthusiasts tend to stay away from them.

And so process begins by understanding the need. Charles Eames, a noteworthy designer who made significant historical contributions to the development of [modern architecture](https://en.wikipedia.org/wiki/Modern_architecture) and [furniture](https://en.wikipedia.org/wiki/Modern_furniture), had this to say — 

> “Recognizing the need is the primary condition for design.”

#### What can you do to improve the UX for command line based interfaces?

There are many different areas by which you can improve the user interface for CLI based applications. Some of them are — 

* **Using consistent grammar and syntax for commands.**

A big part of design is having naming convention standards. For CLIs it’s important to have short, meaningful names for commands, that are easy to memorize and recall. Here’s a Slideshare link that you’ll find super interesting —
https://www.slideshare.net/dakshika/building-user-experience-for-clicommand-line-interface


* **Meaningful error messages and prompts**

When an CLI spits out a verbose series of sentences in case an error happened, we often end up searching on Stack Overflow for that error. Because quite often, we’re not even sure what the error was to begin with.

How many times have you typed `apt-get install some-package` and watched as your terminal spits out a series of verbose characters, which look like English — but for you they appear gibberish?

And this is true not only in the case of CLIs, but even GUIs. Here’s an example of the Java update prompt which we’re super familiar with — 
https://twitter.com/br_/status/1041186952056254464


And there are plenty more things that we could do. But for now, 

### Let’s talk about Prompts.

CLIs are primarily text-based interfaces. They literally take in text as input and spit out output, again mostly as text. It makes sense to optimize the UX for the least amount of keystrokes possible to get things done.

*Of-course, not this way though —*

![](https://cdn-images-1.medium.com/max/800/1*kk_-Bas7aCdqIfmFyyXglg.gif)
<span class="figcaption_hack">[http://www.commitstrip.com/en/2017/02/28/definitely-not-lazy/](http://www.commitstrip.com/en/2017/02/28/definitely-not-lazy/)</span>

And almost every single application out there, web or mobile, make use of prompts to let you do things faster. It saves you the time and hassle of using a keyboard, is friendly and intuitive, and in many ways, can be super fun too!

#### Prompts are cool because they provide gestures, instructions, and plenty of other things to increase the likelihood that users will make the correct responses faster.

> And What better way to do things faster and easier, than by using prompts on the CLI?

Here's a nifty open source library that does this job for us. It gives you stylish CLI prompts that are user-friendly, intuitive and easy to create - 
https://github.com/enquirer/enquirer/

![](https://raw.githubusercontent.com/enquirer/enquirer/master/media/survey-prompt.gif)
<span class="figcaption_hack">Type caption for image (optional)</span>

