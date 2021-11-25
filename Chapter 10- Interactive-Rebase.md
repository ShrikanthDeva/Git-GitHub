Interactive Rebase
=

  ## A tool for optimizing & Cleaning up Commit history
  + Change a commit's Message
  + Delete commit's
  + Re-order Commit's
  + Combine multiple Commits into one.
  + Edit/split an existing commmit into multiple new ones.
  
   ## Things to keep in mind
   + Manipulated commmits will have new **Hash-Id**, technically they are new commits.
   + Should not use Interactive Rebase on the commits that you've already pushed/shared on remote repository.
   + Use it to Clean local commit history before merging it into shared team branch.
   + Optimise the commit structure in feature branch using it so that its more easier for other do look onto what has been changed.
   
   ## Work flow
   + Find the base commit you want to change ( how far you want to go back ).
   + To change recent commits message use
      ``` 
      git commit --ammend "Changed commit msg" 
      ```
   + For anything older than that we need IRB, use
      ``` 
      git rebase -i HEAD~[no.of commits you want to go back]  
      ```
   + An Editor window pops up, Give what kind of manpulation you need
      + NOTE:
         *   Do not Edit the contents.
         *   Commits will be listed in reverse order.
         *   It lists the oldest commit at the top rather than the newest.
      + Kinds of Manipulation you can do
          ```  Commands:
               p, pick <commit> = use commit
               r, reword <commit> = use commit, but edit the commit message
               e, edit <commit> = use commit, but stop for amending
               s, squash <commit> = use commit, but meld into previous commit
               f, fixup <commit> = like "squash", but discard this commit's log message
               x, exec <command> = run command (the rest of the line) using shell
               b, break = stop here (continue rebase later with 'git rebase --continue')
               d, drop <commit> = remove commit
               l, label <label> = label current HEAD with a name
               t, reset <label> = reset HEAD to a label
               m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
               .       create a merge commit using the original merge commit's
               .       message (or the oneline, if no original merge commit was
               .       specified). Use -c <commit> to reword the commit message.
           ```
      + Edit the Script according to your need from the above commands.
      + To do so , Change the work ***PICK*** to word ***WHAT ACTION YOU WANT TO DO*** for each of the commits you want to script for.
      + for Example if you need to change the 3rd commit your file looks similar to this
          ``` 
          edit f7f3f6d Change my name a bit
          pick 310154e Update README formatting and add blame
          pick a5f4a0d Add cat-file
          ```
      + Save and exit the editor **(DONT NOT CHANGE ANY SCRIPTS)**, Now Git rewinds you back to the last commit in that list and drops you on the command line with the following message
          ```
          $ git rebase -i HEAD~3
          Stopped at f7f3f6d... Change my name a bit
          You can amend the commit now, with

          git  commit --amend

          Once you're satisfied with your changes, run

          git rebase --continue
          ```
   + Do all the changes you need and exit the editor, then run
      ```
        $ git rebase --continue
      ```
   + This command will apply the other two commits automatically, and then your done.
   + If you have to change multiple commits,  ***REPEAT THESE STEPS AGAIN*** .
   + Git will stop, let you ammend the commit and continue when you're finished.
      
   ## Re-Order Commits
   
   + Do the first **[4]** steps given in Work flow.
   + Your editor will pop up. Eg -
      ```
        pick 4c39bca gemspec tweak
        pick 85409cf Version bump to 0.4.1
        pick eb32194 Regenerated gemspec for version 0.4.1
      ```
   + Re ordering is as simple as moving the various "PICK" commands around.
   + So if we want to swap the first commit with the last :
      ```
        pick eb32194 Regenerated gemspec for version 0.4.1
        pick 85409cf Version bump to 0.4.1
        pick 4c39bca gemspec tweak
      ```
   + Swap it and save the file, hopefully everything will go alright.
   + If it gets too messy to take care of, just do 
        ```
        git rebase --abort
        ```
   + You will be back to where it started.
   + NOTE : After the swap the commit dates will be reversed it may seem strange.
   
   ## Squashing Commits
   
   ### Squashing a commit in Git means that you are taking the changes from one commit and adding them to the **Parent commit**. 
   
   + It is possible to take a serires of commits and squash them down into one single commit.
   + Do the first **[4]** steps given in Work flow.
   + Instead of ***pick*** give ***squash***, Git applies both that change and the change directly before it and makes you merge the commit messages together.
   + So, if you want to make a single commit from these three commits, you make the script look like this:
      ```
        pick f7f3f6d Change my name a bit
        squash 310154e Update README formatting and add blame
        squash a5f4a0d Add cat-file
      ```
   + Save and exit the editor, Git applies all three changes and then puts you back into the editor to merge the three commit messages:
      ```
        # This is a combination of 3 commits.
        # The first commit's message is:
        Change my name a bit

        # This is the 2nd commit message:

        Update README formatting and add blame

        # This is the 3rd commit message:

        Add cat-file
      ```
   ## Splitting a commit
   + Splitting a commit undoes a commit and then partially stages and commits as many times as commits you want to end up with. 
   + For example, suppose you want to split the middle commit of your three commits. Instead of “Update README formatting and add blame”,
     you want to split it into two commits:“Update README formatting” for the first, and “Add blame” for the second.
   + You can do that in the ``` rebase -i ``` script by changing the instruction on the commit you want to split to “edit”:
      ```
        pick f7f3f6d Change my name a bit
        edit 310154e Update README formatting and add blame
        pick a5f4a0d Add cat-file
      ```
   + Then, when the script drops you to the command line, you reset that commit, take the changes that have been reset, and create multiple commits out of them. 
   + When you save and exit the editor, Git rewinds to the parent of the first commit in your list, applies the first commit``` (f7f3f6d) ```, applies the second ``` (310154e) ```, and drops you to the console.
   + There, you can do a mixed reset of that commit with ``` git reset HEAD^ ```, which effectively undoes that commit and leaves the modified files unstaged.
   + Now you can stage and commit files until you have several commits, and run ``` git rebase --continue ``` when you’re done:
   
      ```
        $ git reset HEAD^
        $ git add README
        $ git commit -m 'Update README formatting'
        $ git add lib/simplegit.rb
        $ git commit -m 'Add blame'
        $ git rebase --continue
      ```
   + Git  applies the last commit ``` (a5f4a0d) ``` in the script, and your history looks like this:
      ```
        $ git log -4 --pretty=format:"%h %s"
        1c002dd Add cat-file
        9b29157 Add blame
        35cfb2b Update README formatting
        f7f3f6d Change my name a bit
      ```
   + This changes the SHA - 1 of three most recent commits, make sure no changed commmit shows up in that list that you’ve already pushed to a shared repository.
   + Notice that the last commit ``` (f7f3f6d) ``` in the list is unchanged. Despite this commit being shown in the script, because it was marked 
     as “pick” and was applied prior to any rebase changes, Git leaves the commit unmodified.
     
   ## Deleting a commit
   
   + Do the first **[4]** steps given in Work flow.
   + put the word “drop” before the commit you want to delete (or just delete that line from the rebase script)
      ```
        pick 461cb2a This commit is OK
        drop 5aecc10 This commit is broken
      ```
   + Deleting or altering a commit will cause the rewritting of all the commits that follws it.
   + The further back in your repo’s history you go, the more commits will need to be recreated.
   + This can cause lots of merge conflicts if you have many commits later in the sequence that depend on the one you just deleted.
   + If you got into any trouble use
      ```
        git rebase --abort
      ```
   + Your repo will be returned to the state it was in before you started the rebase.
   + If you finish a rebase and decide it’s not what you want, you can use ``` git reflog ``` to recover an earlier version of your branch. 
   
