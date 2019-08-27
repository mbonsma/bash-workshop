# Introduction to the command line

This one-hour workshop introduces the basics of interacting with a computer
using Bash (the Bourne Again Shell). You may have heard the terms "command
line", "terminal", "console", "shell", "interactive prompt", "git-bash", etc.
These all refer to using the keyboard to control your computer by typing
commands.

The material for this workshop is based on a
[UofT Coders lesson](https://uoftcoders.github.io/studyGroup/lessons/misc/bash-intro/lesson/)
and the
[Software Carpentry Unix Shell lesson](https://swcarpentry.github.io/shell-novice/).


**Preparation**: To follow along with this workshop on your own computer, you
will need to have `bash` installed. For Linux and Mac users, `bash` is included
as part of the operating system. In OSX, it can be accessed with `terminal`.

For Windows users, I recommend `git bash`, which is packaged with
[git](https://git-scm.com/) (a common version control system). Follow the
instructions [here](http://carpentries.github.io/workshop-template/#git)
to install git bash. Another option
is [Cygwin](https://www.cygwin.com/). As of August 2016, the Windows Subsystem
for Linux (WSL) provides access to most command line tools provided by Ubuntu.
See [here](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide) for
instructions to enable/install the WSL.

## Workshop goals

After this workshop, you will have learned:

- what Bash is and when and why to use it
- how to navigate your computer from the command line using commands like
`pwd`, `cd`, and `ls`
- how to work with files from the command line using commands like `cat`, `cp`,
`mv`, `mkdir`, and `rm`
- handy commands for working with files like `wc`, `head`, `tail`, `history`,
`sort`, and `uniq`
- using "pipes" to combine commands and `>` to redirect output
- where to get more information and help
- time permitting: `cut`

## Why use the command line?

At a high level, computers do four things:

- run programs
- store data
- communicate with each other, and
- interact with us

Computers can interact with us in many different ways, such as through a
keyboard and mouse, touch screen interfaces, or using speech recognition
systems. While touch and voice interfaces are becoming more commonplace, most
interaction is still done using traditional screens, mice, touchpads and
keyboards.

The graphical user interface (GUI) is the most widely used way to interact with
personal computers. We give instructions (to run a program, to copy a file, to
create a new folder/directory) with the convenience of a few mouse clicks.
This way of interacting with a computer is intuitive and easy to learn, but it
can become slow and frustrating if we want to repeat similar actions many times.
For example, if we want to copy the third line of each of a thousand text files
and paste them into a single file, using the traditional GUI approach of clicks
will take several hours to do this.

This is where we take advange of the shell - a command-line interface to make
such repetitive tasks automatic and fast. It can take a single instruction and
repeat it as is or with some modification as many times as we want.

Typing instructions to the computer might at first seem counterintuitive and
unnecessarily difficult, but there are several advantages to learning how to
do this.

### Advantages of text-based communication with your computer

- **Repetitive tasks can be automated**
Like in the example above, text-based commands will make it easy for us to
repeat the same process many times.

- **Familiar tasks can be done very quickly**
Think about learning a language: in the beginning it's nice to look things up
in a dictionary (or a menu in a graphical program), and slowly string together
sentences one word at a time. But once we become more proficient in the language
and know what we want to say, it is easier to say or type it directly, instead
of having to look up every word in the dictionary first.

- **Text-based interfaces are less resource-intensive and faster to develop than
GUIs, which means some programs you might want to use don't have a GUI at all**
Graphical components of programs require more resources from your computer to
be run, and they also take more work to create in the first place. Many powerful
programs are written without a graphical user interface (which makes it faster
to create these programs) and to use these programs you often need to know how
to use a text interface. For example, many of the best data analysis and machine
learning packages are written in Python or R, and you need to know a bit about
these languages to use them. Even if the program or package you want to use is
in a different language, much of the knowledge you gain from understanding one
programming language (like Bash) can be transferred to others. In addition, most
powerful computers that you can log into remotely might only give you a text
interface to navigate the computer with.

- **A record of text commands facilitates reproducibility**
It is much easier to automate and reproduce / repeat any task once you have all
the instructions written down. Compare being shown how to perform a certain
analysis in spreadsheet software, where the instructions will be "first you
click here, then here, then here...", with being handed the same workflow
written down in several lines of codes which you can analyse and understand at
your own pace.

## The shell

The Shell is a program which runs other programs rather than doing calculations
itself. Those programs can be as complicated as climate modeling software and
as simple as a program that creates a new directory. The simple programs which
are used to perform stand alone tasks are usually refered to as *commands*. The
most popular Unix shell is Bash, (the Bourne Again SHell — so-called because
it’s derived from a shell written by Stephen Bourne).

When the shell is first opened, you are presented with a prompt, indicating that
the shell is waiting for input. It might have some text about your computer and
your user identity, and it probably ends with a `$` symbol. Sometimes bash
commands are written down as `$ ls` (for example): you don't have to type the
`$`, only the command itself (`ls`).

```{Bash}
$
```

Let's try a command: `ls` *lists* the contents of the current directory.

```{Bash}
ls
```

If you type a command that Bash doesn't recognize, you'll get an error message:
`ks: command not found`.

```{Bash}
ks
```
