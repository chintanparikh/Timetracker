#Timetracker

##What is Timetracker?
Timetracker is a simple application I wrote in order to keep track of how much time I spend in each branch of a git repository. Many firms require programmers to log hours in for tasks they do, and most different tasks are done on different branches. Thus, Timetracker saves you the hassle of manually writing down the times you start and finish tasks, and instead collects all that data automatically and outputs it in a handy project: time format.

##Installation
Installation isn't the easiest at the moment, but I'm working to fix that.
First, you want to clone this repository somewhere in your local filesystem, and cd into it
```bash
git clone git@github.com:chintanparikh/Timetracker.git
cd Timetracker
```
Next, copy timetracker into a folder in your PATH, typically /usr/bin
```bash
cp timetracker /usr/bin/
```
Lastly, copy ```hooks/post-checkout``` into ```.git/hooks``` in any git repository you want to use timetracker with, and ```chmod +x``` it

For example, if your git repository was located at ```~/Gitrepo```,:
```bash
cd ~
git clone git@github.com:chintanparikh/Timetracker.git
cd Timetracker
cp timetracker /usr/bin/
chmod +x /usr/bin/timetracker
cp hooks/post-checkout ~/Gitrepo/.git/hooks/
chmod +x ~/Gitrepo/.git/hooks/post-checkout
```

##Usage
Most usage is automated with checkouts - whenever you checkout a branch, timetracker with automatically detect that you're working on a new branch/task.
However, timetracker can also manually manage your tasks (especially useful if you are doing something without git)

It supports the following:
```bash
timetracker <options>
```
Possible ```<options>``` are:

* ```  start [PROJECT NAME]``` - starts/continues a project with ```PROJECT NAME```
* ```  end``` - stops work on the current project
* ```  break``` - pauses work on the current project (time not recorded until ```timetracker back```is run)
* ```  back``` - resumes work on the current project
* ```  status``` - gives you the project name and time you have been working on a project
* ```  get``` - gives you project names and time you have been working on all projects
* ```  clear``` - clears the log of all projects and times. WARNING: This cannot be undone
* ```  finish``` - combination of ```timetracker status && timetracker get && timetracker clear```

##Todo List (feel free to fork and help out!)
* Make installation easier - perhaps a script/utility to automatically copy the required files?
* Have ```timetracker start <branch name>``` run when entering a git directory