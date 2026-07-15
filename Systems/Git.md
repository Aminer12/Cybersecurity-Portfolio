Lessons:
	Labex.io - Git for beginners 

Initializing a git repository 
```
git init 
```
git status 
```
git status
```
branch master -> the main timeline of the project 

No commits yet -> save points within the timeline 

nothing to commit -> There are no changes for Git to record 

Git does not track every file you create, only the ones you give to the git repository 

adding a file to git 
```
git add filename.txt
```
Creating a commit | like creating a snapshot of the file in the current moment 
```
git commit -m "Send a message to the future"
```
log of our history 
```
git log 
```

Git configuration
	system level -> applied to all time machines in this dimension
	Global level -> Your personal settings for all your time travels
	Local level -> specific to this particular time experiment 

view time machine settings
```
git config --list 

specific setting 

git config user.name

```
Global Name:
```
git config --global user.name "Your Name"

email 

git config --global user.email "email"

Verify -> same code just without the quotations 
```
Color config
```
git config --global color.ui auto 
auto -> use colors when outputting to the terminal 
```
setting text editor 
```
git config --global core.editor nano
```

cross-compatibility
Windows uses carriage-return and a line-feed character (CRLF)
Unix-based / macOS uses line-feed (LF )

setting auto cross compatibility
```
git config --global core.autocrlf input 

this tells git to convert crlf to lf when you commit (input), but not when you output 
```
alias for checking the current state of your timeline
```
git config --global.st status

alias -> st for the status command 

git st -> now runs the status command 
```

experimental setting -> which override global setting but only for the experiment
```
git config user.name "name" -> this is done at the experiment level
```

ignore files command 
```
echo "*.log" > .gitingnore 

ignore any files with the .log extension
```

see changes before commit 
```
git diff q
```
un-staging files 
```
git restore --staged hello.py
```

Great a new Branch
```
git branch feature-dimension

see branches 

git branch
-a -> to see all
```
\* -> what branch you are currently in
change branches 
```
git checkout feature-dimension 

or 

git switch feature-dimension

switch and create 
git switch -c new_branch
```
Merge branches 
```
git merge branch-name
```
close branches 
```
git branch -d branch-name
-d -> delete the branch, but only if its been merged 
-D -> to force delete
```