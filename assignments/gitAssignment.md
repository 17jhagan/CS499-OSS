# Git Assignment

**INDIVIDUAL ASSIGNMENT**

**Value**: Part of in-class/short assignments grade

## Description

### Understanding the repo
To conduct this, you will have to download [handson.zip](handson.zip) and unzip it.
handson folder is a git repository. Using the command line change the directory to "handson/"

The empty boxes
```

```
represent the content you need to fill and post on your private repository


1. Describe what is the output of the following commands
    -  `git branch` 
    -  `git checkout BRANCH_NAME` (USE THE NAME OF AN EXISTING BRANCH)
    -  `git log --decorate`

```
* git branch: 
      feature-foo
    * master

* git checkout feature-foo: 
    Switched to branch 'feature-foo'

* git log --decorate: 
    commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:29:22 2018 -0700

        Adding header of method foo()

    commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:27:16 2018 -0700

        Adding class A skeleton

    commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:26:44 2018 -0700

        Creating all files (all empty)
```

2. Try `git log --graph --all`. What do you see?
```
* commit f67f266cf420735187053f10d32e2c0f7cbc5a43 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:30:05 2018 -0700
|
|     Adding class B skeleton
|
| * commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Fri Aug 24 15:29:22 2018 -0700
|
|       Adding header of method foo()
|
* commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:27:16 2018 -0700
|
|     Adding class A skeleton
|
* commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Fri Aug 24 15:26:44 2018 -0700

      Creating all files (all empty)

It creates a visual for all the different branches that have been made thus far.
```

3. Use `git diff BRANCH_NAME` to view the differences from a branch and the current branch.
   Summarize the difference from master to the other branch.

```
First, diff compares A.java from feature-foo and master. This tells us that lines 1 and 4 were edited in feature-foo, and that lines 1 and 7 were edited in master.
    diff --git a/A.java b/A.java
    index 3ea227e..674b8ce 100644
    --- a/A.java
    +++ b/A.java
    @@ -1,4 +1,7 @@
     public class A {
    -
    +
    +   public void foo() {
    +
    +   }

     }
 
Then, diff compares B.java from feature-foo and master. This tells us that lines 1 and 4 were changed in feature-foo, while no changes were made in the master branch version.
    diff --git a/B.java b/B.java
    index ae64e6b..e69de29 100644
    --- a/B.java
    +++ b/B.java
    @@ -1,4 +0,0 @@
    -public class B {
    -
    -
    -}
```

4. Write a command sequence to merge the non-master branch into `master`

```
git checkout master
git merge feature-foo

Then git will ask for a commit message. Fill that in, then you're done!
```


5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) 
and (ii) change to this branch

```
git branch math
git checkout math
```
   
6. Edit B.java adding the following source code below the content you have there
```java
System.out.println("I know math, look:")
System.out.println(2+2)
```

7. Write a command (or sequence) to commit your changes
```
git add B.java
git commit -a

This will open vim and you'll be able to type your message here. Save the file and close vim.
```

8. Change back to the `master` branch and change B.java adding the following source code (commit your change to `master`):
```java
System.out.println("Hello World")
```

9. Write a command sequence to merge the `math` branch into `master` and describe what happened
```
git merge math

Auto-merging B.java
CONFLICT (content): Merge conflict in B.java
Automatic merge failed; fix conflicts and then commit the result.
```
   
10. Write a set of commands to abort the merge
```
git merge --abort
```
   
11. Now repeat item 9, but proceed with the manual merge (Editing B.java). All implemented functions are needed. Explain your procedure
```
I reinitiated the merge between master and math with:
    git merge math

Upon recieving the merging conflict, I used:
    git mergetool

This then opens up vimdiff, which has a few different views and options to manually edit how the merge will occur.

Once I save and exit the file, I will move on to finish merging.
```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch up-to-date
```
git commit -m "This combines B.java from math and master."

Then you can verify if master is up to date by:
    git merge master
    
Which returns:
    Already up to date.
```



