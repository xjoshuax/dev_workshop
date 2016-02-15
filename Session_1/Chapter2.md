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
2. Open the browser, go to your Fork of this project at http://github.com/(your-username)/dev_workshop
1. Click the drop-down menu where it reads "master"
2. Type the name `my-experiment` on the text box
3. 
