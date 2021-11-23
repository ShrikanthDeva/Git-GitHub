# Git reset

  
  - Command that unstages the file but it preserves the file contents.
  - ```
    git reset [file] 
    ```
  ---
  
  
  - Command that undoes the commit,basically resets the pointer which is currently pointing to **HEAD** (the last commit) and sets it to **HEAD-1**. 
  - ```
      git reset HEAD~1  
    ``` 
  ---
   
  - Command that undoes all the commit after the specified commit and preserves the changes locally.
  - ```
      git reset [commit] 
    ```
  ---
  
  
  - Command that discards all the history and goes back to specified  commit.
  - ```
      git reset --hard [commit] 
    ```  
  ---
  
  + **[commit]** here refers to the **hashkey** which can be found in first line of every commit in **git log** command.
  + Eg - 
     ``` 
      git reset --hard iasbfvoiqub198rhh9hrf 
     ``` 
