Submodules
=
Submodules is fully functional git repo you can do all the things in it.
+ Copy pasting third-party code , mixing external code with your own files is not a good approach
+ The libraries are project of itself , theres no need to keep them in same version control can be kept seprately.
+ A standard git repository speciality is its nested inside another parent repository.

### Working
+ Create a folder where you want to keep the submodule in.
+ Use command
  ```
    git submodule add [url of the repo]
  ```
+ In case , the submodule you want contains a submodule use
   ```
      git clone --recurse-submodules [URL]
    ```

+ Then commit using ``` git commit -m "msg"   ```.

  
#### Note:
  + The actual content of the submodule is not stored in parent repository.
  + Parent repository only stores the ***remote URL***, the ***local path inside the main project*** and ***checked out revision***.
  + Working files are inside parent repo but they are not part of the version control context.
  + Use the below command to get the path and remote url of the submodule.
    ```
      cat .gitmodules
    ```
  + There will be a record of the submodule in ``` cat .git/config ``` command also.
  + Git also keeps the copy of each submodules git repository in its internal ``` Git modules ``` Folder.
  + Do not mess with internal configuration.
  + Dont do any submodule work mannually use proper Git Commands.
  + If your cloning a repository which itslef has the submodule, then initially you wont get those submodules ie they might be an empty folder.
    As you that git repo does not store the submodules content only stores the confiugration.
  + Step into the submodule folder and Use the below command to get the submodules of the submodule.
    ```
      git submodule update --init --recursive
    ```
  + ***INSTEAD OF ALL THESE STEPS YOU CAN EVEN DO THEM IN A SINGLE STEP USING THE BELOW COMMAND***.
    ```
      git clone --recurse-submodules [URL]
    ```
  + In ***SUBMODULES*** the checkout is is always on a specific commit not a branch.
  + When a new commit happens, the checked out commit does not change.
  
    
    
    
  
