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
 and the wildcard character `*`
- using "pipes" to combine commands and `>` to redirect output
- where to get more information and help
- time permitting: `cut`, `sort`, and `uniq`

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

## Navigating files and directories

Stuff on your computer is organized into files and folders (also called
directories). You might be used to navigating through your filesystem using a
navigator application and clicking on directory icons, and we can do the same
thing from the command line.

First, the command `pwd` (*print working directory*) tells us where we are in
the filesystem.

```{Bash}
pwd
```

The output you see will likely be different depending on your operating system.
We're all likely in our *home* directory, where terminal or Git Bash opens by
default.

`ls` lists the files and directories inside the current directory. We can add
*flags* or *options* to commands to modify their behaviour: try adding `-F` and
see if you notice what changes about the output.

```{Bash}
ls -F
```

In general, a Bash command begins with the command name (`ls`), is followed by a
list of options that begin with `-` or `--` (`-F`), and ends with arguments. We
can add an argument to `ls` that specifies which directory we want `ls` to look
in. Try the following commands and see what they do.

```{Bash}
ls -a
ls Downloads
ls -F Downloads
ls -F -a /
ls -Fa /
ls *.txt
```

The flag `-a` stands for "all": `ls` shows all files and directories, even
hidden ones. The hidden directory `..` is shorthand for the parent directory,
and the hidden directory `.` is shorthand for the current directory.

The character `*` is a *wildcard* - it matches any character. The command
`ls *.txt` will list any file that ends in `.txt`, since `*` matches anything
that comes before. This is handy if you're looking for something and you know
a bit about it, like that it ends in `.jpg` or starts with `a`, for example.

`ls` has many options - we've just seen two. To get more information about a
command, you can use the option `--help`, which will print out the manual page
for the command.

```{Bash}
ls --help
```

Another way to access the manual page is with `man`, which stands for *manual*:

```{Bash}
man ls
```

It's possible that only one of these two will work depending on your environment.

> **Challenge**
>
> What does `ls` do when used with
> the `-l` option? What about if you use both the `-l` and the `-h` option?

`pwd` and `ls` tell us about where we are and what's there, but we can also
move around through our filesystem. The command `cd` (*change directory*) is
how to do this.

```{Bash}
cd Downloads
pwd
ls
```

What if we want to go back up one level? We might try using the name of the
higher directory:

```{Bash}
cd madeleine # or whatever your home directory is called
```

But this gives an error: `bash: cd: madeleine: No such file or directory`.

*Path names* are relative: commands like `cd` and `ls` try to relate file and
directory names to ones that can be seen from the current location. We have a
few options to go up one level:

1. Specify the full path

```{Bash}
cd /home/madeleine
pwd
```

2. Use the shortcut `..` to go up one level

`..` is shorthand notation for "the directory that contains the current
directory."

```{Bash}
cd Downloads
cd ..
pwd
```

3. Use the shortcut `-` to go back to the previous directory

`-` is shorthand for "the directory we were in last," which in this case also
happens to be the directory above us.

```{Bash}
cd Downloads
cd -
pwd
```
4. Use the shortcut `~` to go to the home directory

'~' is shorthand for the *home directory*, which in this case is where we want
to go.

```{Bash}
cd Downloads
cd ~
pwd
```

All of these options have the same result in our case where we want to go from
a directory below the home directory back to home. But if we were somewhere else,
they wouldn't necessarily be equivalent.

> **Challenge**
>
> Starting from `/Users/amanda/Desktop/data`, which of the following commands could
> Amanda use to navigate to her home directory, which is `/Users/amanda`?
> Hint: play around with these choices on your own computer by creating and
> navigating to a folder called `data` on your desktop using the following commands:
> `cd Desktop`
> `mkdir data`
> `cd data`
> Remember that `cd -` will take you back to the previous directory after each
> trial solution you use, and that `pwd` will show you where you are to check if
> it worked.
>
> 1. cd .
> 2. cd /
> 3. cd /home/amanda
> 4. cd ../..
> 5. cd ~
> 6. cd home
> 7. cd ~/Desktop/data/../..
> 8. cd
> 9. cd ..

**Handy tip: tab completion**

Whenever you're typing in your terminal, you can hit `Tab` to auto-complete a
command, filename, or directory name. If there's only one possibility, it will
auto-complete; if there are more than one, hitting `Tab` a second time will show
all the possibilities.

```{Bash}   
cd Des # and hit "Tab"
```

**Handy tip: up-arrow**

Hitting the `up` arrow key will fill in the most recent command you've run.
Hitting `Enter` will run it again. Hitting `up` more than once will cycle back
in time through all the previous commands you've run.

## Working with files

We've seen how to navigate our computer using commands, and now it's time to
actually make some changes.

Let's work on the Desktop so that we're all in the same place.
Header One
```{Bash}
cd ~/Desktop
ls
```

The command `mkdir` *makes a directory* in the current working directory. We'll
make a directory called 'thesis'.

```{Bash}
mkdir thesis
ls
```

You could also create a directory using whatever file navigator you're used to,
and it would turn out exactly the same.

Now let's go into the thesis directory and create a file.

```{Bash}
cd thesis
touch intro.txt
```

The command `touch` will either update the timestamp of a file that exists, or
create a new file if the filename you give as an argument doesn't exist yet.

The file `intro.txt` is blank, which we know because we just made it and haven't
done anything to it. In general, how can you tell if a file is empty? There are
many ways, and we'll see more that could be applied to this question as we go.

```{Bash}
ls -lh intro.txt
```

The flag `-l` stands for *long*, and it causes `ls` to display more information
about a file: the permissions, user information, size, and time information. The
flag `-h` stands for *human-readable*: it converts the file size from just bytes
to human-readable sizes like KB or MB. Using `ls -lh` tells us that the file
`intro.txt` has size 0.

Another way to see if a file is empty is to check directly what's inside it. The
command `cat` (*concatenate*) will print the contents of a file to the screen.

```{Bash}
cat intro.txt
```

There's no output because the file is empty.

You can copy a file using the command `cp`. The first argument to `cp` is the
filename you want to copy, and the second argument is the name of the destination
file.

```{Bash}
cp intro.txt intro_v1.txt
ls
```

The command `mv` *moves* a file to a new location or filename. Since renaming is
fundamentally the same thing as moving, you can use *mv* to rename files.

```{Bash}
mv intro_v1.txt intro_backup.txt
ls
```

With `mv` and `cp`, you can specify different paths for the filenames. In this
example, supplying a destination directory but not a filename will tell `mv` to
re-use the same filename.

```{Bash}
mv intro_backup.txt ../
ls ../
```

> **Challenge**
>
> Suppose that you created a plain-text file in your current directory to
> contain a list of the statistical tests you will need to do to analyze your
> data, and named it: `statstics.txt`
> After creating and saving this file you realize you misspelled the filename!
> You want to correct the mistake, which of the following commands could you use
> to do so?
>
> 1. `cp statstics.txt statistics.txt`
> 2. `mv statstics.txt statistics.txt`
> 3. `mv statstics.txt .``
> 4. `cp statstics.txt .`

The command `rm` will *remove* the file whose name you supply as the argument.
Be careful: this is not reversible! The file will be deleted forever, bypassing
the recycling bin. If you do want a bit more warning, however, you can use the
flag `-i`, which will ask for confirmation before removing the file.

```{Bash}
touch test.txt
rm test.txt

touch test.txt
rm -i test.txt
```

### Working with the contents of a file

We've seen how to create, delete, move, copy, and rename files and directories.
Now we'll learn some commands for working with and analyzing the contents of
files.

First, a handy command that shows you the most recent commands you've run in
reverse chronological order:

```{Bash}
history
```

Using `history` is a great way to quickly make a task reproducible - if you've been
trying different things and you find the one that works, you can find it back
again using history. Better yet, you can *redirect* the output of a command from
the screen to a file, and doing this with `history` saves the command history to
a file.

```{Bash}
history > history.txt
ls
```

Now we have a file called 'history.txt' that contains the output of the `history`
command. Let's have a look at the contents of this file.

```{Bash}
cat history.txt
```

`cat` is great for seeing what's in a file, but if the file is very big, `cat`
will still try to print the entire thing. Two commands that are very helpful for
getting a taste of a file without a huge amount of output are `head` and `tail`.

```{Bash}
head history.txt
tail history.txt
```

Both of these commands have an option `-n` that specifies the number of lines to
return:

```{Bash}
tail -n 20 history.txt
```

A command I love and use a lot is `wc`, *word count*, which returns the number
of lines, words, and characters in a file.

```{Bash}
wc history.txt
```

`wc` has options to turn off and on each of its outputs: `wc -l` just returns
the number of lines in the file.

```{Bash}
wc -l history.txt
```

## Combining commands using pipes

Much of the power of Bash comes from combining a few commands to make powerful
pipelines. To do this, there's one more operation to learn: the *pipe*.

```{Bash}
cat history.txt | tail
```

The vertical bar `|` is a *pipe*: it tells Bash to take the output of the first
command and use it as the input to the next command. Remember that `tail` takes
a file as its argument; now it's taking the output of `cat history.txt` in place
of a filename. The result here is the same as `tail history.txt`, which means
we probably don't need to use a pipe in this example. But it can be very useful
to skip intermediate steps sometimes: for example, instead of saving `history.txt`,
we could have directly piped `history` into the command `tail` to see the most
recent commands we've run.

```{Bash}
history | head
```

You can combine multiple pipes in a chain as long as you want.

```{Bash}
history | head | wc -l
```

> **Challenge**
>
> Which line of `history.txt` will be returned by the following command?
>
> `cat history.txt | head -n 5 | tail -n 1`

### A practical example: counting your most frequent Bash commands

Let's combine what we've learned so far with a few new commands to do something
useful: figure out which Bash commands we used most often. We already have a
file `history.txt` which has the ~2000 most recent Bash commands in it, so we'll
use this file to do our analysis.

```{Bash}
head history.txt
```

`history.txt` has several columns: the first column is a number that gives the
order in which each command was run, and the second column is the command itself.
But we don't want to know all the sub-specifics of each time we ran `ls`, we want
to count just `ls` by itself. We can think of there being at least
three columns: the first with the number, the second with the command, and the
third with options and arguments.

My second all-time favourite Bash command is `cut`: `cut` *cuts* columns in a file
by a delimiter that you specify, and you can return one or more of the resulting
columns by itself.

```{Bash}
cat history.txt | cut -d' ' -f4
```

`-d` specifies which character delimits the columns; here it's a *space*
character. `-f4` tells cut to return the 4th column. It's the 4th column and not
the 2nd because it looks like there's a few extra whitespace characters that `cut`
is counting as their own columns. You might need to change the number by trial
and error until you get a list of just commands, the output we want.

Next, we want a list of all the unique commands and how many times they appear.
There's a command `uniq` that can do just that!

```{Bash}
cat history.txt | cut -d' ' -f4 | uniq
```

But wait: some commands are still showing up multiple times. It turns out that
`uniq` only collapses repeated lines if they are *adjacent*: if you have the
sequence `ls, cd, ls`, `uniq` will still return all three. We need an intermediate
step where we sort all the commands using the command `sort`.

```{Bash}
cat history.txt | cut -d' ' -f4 | sort | uniq
```

That's more like it! To count how many times each command turns up, we can add
the flag `-c` to `uniq`:

```{Bash}
cat history.txt | cut -d' ' -f4 | sort | uniq -c
```

A final pipe to `sort` will arrange these in order:

```{Bash}
cat history.txt | cut -d' ' -f4 | sort | uniq -c | sort
```

`sort` by itself sorts based on the first character; we can add the `-n` flag
to sort by the numeric value of each line.

```{Bash}
cat history.txt | cut -d' ' -f4 | sort | uniq -c | sort -n
```

If you wanted, you could save this output to a file as a record of your command
use:

```{Bash}
cat history.txt | cut -d' ' -f4 | sort | uniq -c | sort -n > common_commands.txt
```

## Where to get help

When you're getting familiar with the command line, it can be hard to know what's
possible and where to get help. It's not that easy to make an irreversible error,
so a good way to learn is to try things. If you're wondering how to do something
in particular, a Google search for your question, like
"Bash how to get the second column of a text file",
will usually return a StackOverflow page with the same or similar question.
There's usually more than one way to do something, and it's up to you which
methods you end up being comfortable with.

If you'd like a more in-depth tutorial, I recommend [Software Carpentry's Bash
lesson](https://swcarpentry.github.io/shell-novice/). This workshop is based on
the Software Carpentry material, but there's much more in the online notes than
we had time to cover today.
