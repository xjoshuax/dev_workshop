# Chapter 1: Getting familiar with the command-line

You probably noticed that most programmers spend a lot of time in the Terminal app. We sometimes even have customized versions of the app with better colors and richer features. That is because the terminal is the most powerful tool you can use to control a computer. And in the end of the day, that's all programming is: making a computer do what you tell it to do, by speaking its language.

You can do all sorts of things in the terminal. But don't take my word for that. This is supposed to be a very hands-on approach to learning. So roll up your sleeves and let's start with some warm-up exercises:

## Exercise: Navigating with Terminal
Here we will cover some basic terminal commands and learn how to explore the file system within the terminal

1. Open up Terminal.app
1. In terminal, type in the command `pwd` and hit `<Enter>`
1. You should see the terminal print something like `/Users/<username>`
  - By typing `pwd`, we just told the terminal to "Print Working Directory"
  - The directory `/Users/<username>` is also known as "Home Directory"
  - The home directory is special. So special it has its own shortcut. In terminal it can be used interchangeably with the character tilde (`~`)
  - In other words, as far as the terminal understands, `/Users/<username>/report.doc` is exactly the same as `~/report.doc`
1. Now, let's explore what's inside that folder. Give the command `ls -l` (from here on, we should agree that giving a command means typing something and hitting `<enter>`, so I won't emphasize the `<enter>` part anymore)
  - The command `ls` is short for "List".
  - What comes after the command are its arguments. Here we gave the argument `-l` that's a shortcut for "long". That means we want the long version of the list
  - To get a shorter version of the list, try the command `ls -1`
  - To get all files, including hidden and system file, try the command `ls -a`

1. Let's move on to another folder. Give the command `cd Documents`
  - The command `cd` is short for "Change Directory"
  - Now the terminal is pointing to the directory `~/Documents`
  - To prove that, give the command `pwd` once more
1. Kinda boring so far? Tired of just walking around the folders? Let's actually make some changes next.



## Exercise: Creating files and folders within Terminal
Here we will actually make some changes to the file system from within the terminal.

 1. I'm assuming you've left Terminal.app open and pointing to `~/Documents` since the last exercise
 2. Open up a Finder window
 3. If possible, leave it side-by-side with the terminal window so that you can see them both simultaneously
 4. Give the command `mkdir Programming`
    - As you might have guessed, `mkdir` is shorthand for "make directory"
    - You should have now seen a folder called "Programming" appear on your Finder window
 5. Using the `cd` command from before, make the Terminal point to `~/Documents/Programming`
 6. Use the `ls -l` command from before and verify that the new folder is empty
 6. Also, open up the Programming folder on your Finder window
 6. Give the command `touch file.txt`
   - The `touch` command creates a file if it doesn't exist, and leaves it in peace if it already exists
 7. Now you can use the `ls -l` command again to verify that the changes you can see in Finder are also recognized by the Terminal.

## Exercise: Changing files within Terminal
So far we have been talking a lot to Terminal. As you may have noticed, we give it a command, it executes the command, and immediately asks us for the next command.
This cycle is sometimes referred by programmers as REPL: Read, Eval, Print, Loop. This is to say that every time we press the `<enter>` key, the terminal 1- Reads what we typed, 2- Evaluates what that command was, 3- Prints something to the screen if necessary (i.e. the `ls` command prints the list of files in that folder, the `pwd` command prints the address of the working directory), 4- Loops, that is, goes back to the first step and starts over again (the blinking cursor, waiting for a new REP cycle)
In this step by step, it will be really important for us down the line to let our programs communicate state, and print something back to the user, so let's learn how to do that

1. In Terminal, give the command `echo "Wake up, Neo..."`
  - The `echo` command does what the name suggests: it only repeats back to you what you just said, in this case, the string of characters `"Wake up, Neo..."`
  - Notice the double quotes around our string of characters. Remember when we talked about arguments? Like the `-1` or the `-a` that followed the `ls` commands? If we didn't use the double quotes here, each of the words in the sentence would be understood as different arguments. By surrounding it with double-quotes we are grouping it all into one argument. Remember this, it will be important later.
1. Now it's time to write that to our file. In terminal, give the command `echo "Mary had a little lamb" > file.txt`
  - This time we will see nothing printed in terminal, it will immediately ask us for the next command
  - This happened because we told terminal to execute this echo inside the file with the `> file.txt`. This is called a redirect.
1. Give the command `atom file.txt`
  - The command `atom` is only available if you have installed the Atom editor, like the SETUP.md file has told you to do
  - This should've opened the file `file.txt` with Atom editor
  - You'll now see that the file contains our sentence "Mary had a little lamb"
1. Keep the file atom editor with the file open, and the terminal window side by side
2. Give the command `echo "Its fleece was white as snow >> file.txt"`
  - Notice the double `>>` redirect.
  - While the single `>` redirect meant "execute this command, and write its output to the file", the double `>>` redirect means "execute this command, and *append* its output to the file"
  - You should have seen the new sentence appear below the existing sentence in the file

## Exercise: Copying the project files from Github
Now let's get out of the Terminal for just a moment.
1. Open your browser, go to [github.com](http://github.com)
2. Login with your account
3. Go to the [repository for this workshop](https://github.com/edgarjcfn/dev_workshop)
4. On the top-right, click the "Fork" button
  - We will cover the "Fork" action in more detail later, but for now just know that it's creating your own copy of the project files. This copy is yours to modify at will, without impacting the work of others.
5. Wait until the process is done
6. Now you can download your own copy (or "Fork") of the project, by giving the command `git clone https://github.com/<your-username>/dev_workshop.git` in the Terminal app
7. We will cover the inner-workings and magic of GIT in the next chapter
