# Git branch
  + Command that lists all the local branches in the current repository.
     ``` 
      git branch 
     ``` 
  ---
  
  + Current branch is indicated with ``` * ```.
  ---
  
  + Command that creates a new branch.
    ``` 
      git branch [branch name]
    ```  
  ---
  
  + Command that deletes the feature branch.
    ```
      git branch -d [branch name] 
    ```  
  ---
  
  + Eg - 
    ``` 
      git branch branch1 
    ``` 
    
    
# Git merge
  + Command that merges the specified branch's history into current branch.
    ``` 
      git merge [branch name]  
    ```  
  + Eg - 
      ``` 
        git merge branch2 
      ``` 
      
# Git checkout
  + Command that is used to switch from one branch to another.
    ``` 
      git checkout [branch name]  
    ```  
  + Command that creates a new branch and also switches to it.
    ```
      git checkout -b [branch name] 
    ```  
  + Eg - 
    ``` 
      git checkout -b branch2 
    ``` 
