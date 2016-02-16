# Chapter 2: Getting familiar with Git

Git is the most popular software today used by developers to do version control for source code.
That means that developers can work with a shared code base, but still be free to make mistakes and break things, without creating barriers on the workflow of teammates.

Working with Git can be quite tricky in the beginning, because you have to create a mental model of all the different versions, and understand Git's unique branching system, all the while getting used to a completely new vocabulary.

The reason why I think it's important to understand the concepts behind Git is that maintaining different versions of the software are big parts of how developers interact with all the non-dev teams and so it's important to get at least a part of this vocabulary understood by both parties.

Github is the most used cloud-based solution for Git, so we'll assume for the purpose of this chapter that this is what the student is using.

## Basic Git Glossary
### Fork
"Forking" someone else's repository means that you are copying that repository to your own Github account. That means that you are free to do changes and create your own version of the software, without interfering on someone else's work. If you think your changes can be useful to the original author of the code, you can submit these changes to him in a Pull Request (more on that topic later).

To make the concept easier to understand, let's imagine that a repository instead of containing software contains the blueprint for a household appliance. Let's say, a microwave.


So you go online, you find the perfect microwave that has all the features and settings that you need but the electricity plug is not compatible to the standard in your country. So what could you do? In the Git world, you could basically copy that blueprint to your factory (it's an open-source blueprint), change it just a little bit so that it fits the standard for your country and turn on the factory floor, producing amazingly compatible microwave ovens.
If you decide that the original creators of the microwave oven could profit from you new electricity plug, you can then send them your updated blueprints and they can choose to use it or not.


#### Exercise: Forking this repository from Github
1. Open your browser, go to [github.com](http://github.com)
2. Login with your account
3. Go to the [repository for this workshop](https://github.com/edgarjcfn/dev_workshop)
4. On the top-right, click the "Fork" button
5. Wait until the process is done
6. Now you can download your own copy (or "Fork") of the project, by giving the command `git clone https://github.com/<your-username>/dev_workshop.git` in the Terminal app
7. This copy is yours. You can freely change it, and nobody else will see these changes


#### Exercise: Submitting a pull request
1. For the purpose of this exercise, we will go back to the browser, and do the changes from there.
2. Open the browser, go to your Fork of this project at http://github.com/(your-username)/dev_workshop
3. Locate the file /Project/Git Experiments/Awesome_People.txt
4. Click the pencil icon on the top right to edit the file using the in-browser editor
5. Add your name to the list of awesome people
6. On the "commit changes" form on the bottom, add a message explaining what you changed in the file
7. Click the green "commit changes" button
8. Now go back to the home page of your forked repository
9. Click the submit pull request button
10. Congratulations, after I accept your pull request, your name is officially in the original repo, and will remain forever in the hall of Awesome People.


### Branch
Forking and branching are actually conceptually similar, but used for very different purposes. Branching is also done to create a copy of the code to a separate place, so you can do experiments and have the freedom to break it, without creating barriers for other people working on the same product.

To understand the basic differences between forking and branching, let's go back to the microwave example from before. So you've found a nice open-source blueprint for a microwave oven, you copied that blueprint to your factory ("Fork") and now you are working on your own adaptation, the electricity plug. As you do this, someone else in your team decides that he wants to work on a different feature, let's say, to have the oven display a blue internal light, instead of yellow. Yet another colleague wants to experiment with a more energy-efficient model, that according to her can improve energy consumption in 60% for the whole oven. In the git world, each of these colleagues would start to work on their own "Branches" of the blue print. That would mean they each get a copy of the original blueprint and start working individually on their own features.

If they break something on their design, or their experiment fails, this doesn't stand in the way of the work of the other two colleagues. In the other hand if they are happy with the changes, they can decide to merge this changes together into a single blueprint, and you can end up with a blue-lighted, energy-efficient, standards-compatible microwave oven.

So as you can see, the concepts between Fork and branch are very similar (give me a copy of something, so I can work on it without getting in your way), but the usages are very different. One is used to get your own copy of someone else's work ("Fork"), while the other is used so your team can work freely on multiple features of the same design ("Branch").

One important thing to notice: branches are not just used by teams. It is very useful even when coding by yourself, to create a new branch for each of your new features and experiments. This way you can easily discard ongoing changes, without compromising the working version of your code.

#### Exercise: Git branching
2. Open the browser, go to your own fork of this project at http://github.com/(your-username)/dev_workshop
1. Click the drop-down menu where it reads `master`
2. Type the name `my-experiment` on the text box and hit `<enter>`
3. You've just created a branch called `my-experiment`. It's essentially a copy of what was in `master`, but now changes made to the files won't show up in the master file
4. Create a new file in the folder "Git Extensions" named `my-new-file.txt`
5. Commit the creation of the new file with a message
5. Now select the master branch again, and navigate to that folder
6. You'll realize your newly created file is not there
   - That is because the `my-experiment` branch was not merged to `master` yet
7. Now proceed to the main view of the repository and click the "Compare & Pull Request" button
8. Follow the instructions to merge the `my-experiment` branch into `master`


### Pull, push and commit : Synchronizing with the repository
At this moment, I hope there are no doubts about forking and branching because in my experience this next topic is where things tend to get a bit tricky to understand.
Git works by creating a history of version on your local computer, and gives you absolute control of when you want to synchronize this information with the server (thus, sharing these changes with your team). It's a tricky concept to grasp because we are used to tools that do auto-updating with a server like Dropbox and Google Drive. Git is just different.

Think about when you make changes to a document that is backed up with Google Drive. Each time you save the document, a new input in the history of that document is created. It states what was changed, who changed it and when. Later, anyone in the team can inspect these changes, and even download a previous version of the file if needed. But when you hit "save", the software _automatically_ uploads those changes to the server. You had no control in that.

That approach can cause a lot of conflicts if the repository is holding many files, that are constantly changed by multiple people, and have lots of internal dependencies.  What git does is allow developers to bundle significant changes locally and then send them to the server when they want to. By saving this information locally, we can go back in history and undo changes even without communicating with the server.

In the following exercises we will present some important concepts on that matter. As an added challenge, all the file changes (creating files, adding text) should be done in the terminal, using the commands we learned on Chapter 1.

#### Exercise: using `add` and `commit` to write to local history
1. Using the terminal, navigate to the folder `Project/Git Experiments` (remember the `cd` command?)
2. Open the file `edit.me` using the Atom editor (Remember, you can do this via command-line as well, using the `atom` command)
3. Marvel at the amazing content of the file
4. Make some modifications to the file. Do whatever you like to the text. (Maybe you want to append some text to it, using `echo` and the `>>` redirect?)
3. Now in the command line type `git status`
4. You should see that the modifications appear in a list called `Changes not staged for commit`
   - Changes not staged for commit are changes that are still not written to git history
   - Because there's no historical data written yet, these changes are super easy to lose.
   - A git "change" can be anything. In this case it's text modified inside a file, but it could also be a deleted file, for example.
5. Use the command `git add edit.me`
6. Nothing seems to happen
6. Now try `git status` again, what changed?
  - `edit.me` now shows up in a different list: `Changes to be commited`
  - At this point you still haven't written to history, you're merely saying: "this file should be included, next time I write changes to history"
1. Now it's time to actually write history (sounds epic, doesn't it?)
2. Tell the terminal to `git commit -m "My first commit"`
  - Note that you *always* have to provide a message to the commit
  - Messages help use read the history and see what was changed
3. Now if you try the `git status` once more, you'll see that there are no more changes to be commited.
  - It might warn you though, that your changes are out of sync with the server
  - The `commit` only writes to your *local* history: Github (the server) still has no idea of what you just did. It all happened on your computer and you can't share this change with your team just yet.
7. Now use `rm delete.me` to remove this other file
8. Now try to commit the deletion by replicating the steps 9 to 12.

#### Exericse: using `pull` and `push` to synchronize with server
1. Now that you have at least 2 changes (the commits from last exercise), we should push them to the server. This is the safest thing you can do with your changes. Once they are on github, you can always recover to this state
2. Since the changes are already commited. All you have to do now is `git push`
3. Wait until it's completed
4. Check your changes on the github project page.
5. Since we're in the github project page, let's do some changes from the browser
6. Go to the `Project/Git Experiments` folder
7. Do some more changes to `edit.me` via the in-browser editor, and commit these changes.
  - For the purpose of this exercise, we can pretend that these changes were done by a team mate, somewhere else in the world.
8. Now back to terminal, use `git pull`. This will update your local changes with the changes done somewhere else.
