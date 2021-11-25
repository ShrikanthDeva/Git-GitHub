Git Commands
=
Git init
-
  + ``` git init [repository name] ```  command to initiate or start a new repo.
  + Eg -   
     ``` 
      git init folder1/folder2/folder3 
     ```
 
Git clone
-
  + ``` git clone [url] ```  command to obtain a repo from an existing url into local machine.
  + Eg - 
    ``` 
     git clone https://github.com/abc/123.git 
    ```
   

Git add
-
  + Command to track down the files and changes in git (Add basically means add the change).
  + Adds one or more file to the staging area.
  + ``` git add [file name] ```  command to add the change in that particular file.
  + ``` git add . (or) git add -A ```  command to add all the changes of tracked file and **COMMITS THEM**.
  + Eg - 
    ```
      git add abc.md 
    ``` 

Git commit
-
  + Command to records or snapshots the file permanently in the version history.
  + ``` git commit -m " Commit message " -m " some desc " ```  command that commits with the message given.
  + ``` git commit -a ```  command that commits any files you’ve added with the git add command and also commits any files you’ve changed since then.
      + This does not commit a new file.
  + ``` git commit -am " Title" -m " Desc " ```  command that adds and commits with the message given.
  + Eg - 
    ```
      git commit -m " changed the 4th line " 
    ``` 
  
Git diff
-
  + ``` git diff  ```  command that shows the differences which are not yet staged.
  + Unchanged lines -> White colour, Removed line -> Red colour, Added lines -> Green colour. 
  + ``` git diff --staged ```  command that shows the differences between the files in the staging area and the latest version present.
  + ``` git diff [first branch] [second branch] ```  command that shows the differences between the two branches mentioned.
  + Eg - 
     ``` 
      git diff branch2 branch3 
     ``` 

Git reset
-
  + ``` git reset [file]  ```  command that unstages the file but it preserves the file contents.
  + ``` git reset HEAD~1  ```  command that undoes the commit, basically resets the pointer which is currently pointing to **HEAD** ( the last commit ) and sets it to HEAD-1. 
  + ``` git reset [commit] ```  command that undoes all the commit after the specified commit and preserves the changes locally.
  + ``` git reset --hard [commit] ```  command that discards all the history and goes back to specified  commit.
  + **[commit]** here refers to the **hashkey** which can be found in first line of every commit in **git log** command.
  + Eg - 
     ``` 
      git reset --hard iasbfvoiqub198rhh9hrf 
     ``` 

Git status
-
  + ``` git status  ```  command that lists all the files that need to be committed.
  + Eg - 
    ``` 
      git status 
    ``` 

Git log
-
  + ``` git log  ```  command that lists the version history for the current branch.
  + ``` git log --follow[file] ```  command that lists the version history for the file , including the remaining of the files also.
  + Eg - 
    ```
      git log --follow proj_1 
    ```

Git show
-
  + ``` git show [commit]  ```  command that shows the metadata and content changes of the specified commit.
  + Eg - 
    ``` 
      git show iasbfvoiqub198rhh9hrf 
    ``` 

Git remote
-
  + ``` git remote add [variable name] [Remote server link]  ```  command that is used to connect your local repository to the remote server.
  + ``` git remote -v ```  command that checks if the connection has been established to the repository.
  + Eg - 
     ``` 
      git remote add origin https://github.com/abc/123.git 
     ``` 

Git push
-
  + ``` git push [variable name] master  ```  command that sends the committed changes of master branch to remote repository.
  + ``` git push [variable name] [branch] ```  command that sends branch commits to remote repository.
  + ``` git push -u origin master ```  command that pushes all the committed files to the master branch in the remote repository.
  + ``` -u ``` sets the default push location to origin master.
  + ``` git push --all [variable name] ```  command that pushes all the branch to remote repository.
  + ``` git push [variable name] :[branch name] ```  command that deletes a branch on remote repository.
  + Eg - 
     ``` 
      git push origin master 
     ```
     ``` 
      git push --all origin 
      ```

Git pull
-
  + ``` git pull [Repository link] ``` (or) ``` git pull origin master ```  command that fetches and merges changes on the remote server to working directory.
  + Eg - 
    ``` 
      git pull https://github.com/abc/123.git 
    ``` 

Extra Notes:
-

+ Command to delete the particular file/folder ( This deletes from filesystem) :
    ```
      git rm -r one-of-the-directories 
    ```
    + Then Commit the changes and push to origin.

+ Command to undo the last commit :
    ```
      git push origin +[hashkey]^:main
    ```
    






  
 
