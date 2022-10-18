Cherry Picking
=

#### Cherry picking in Git means to choose a commit from one branch and apply it onto another.
+ This is in contrast with thee other ways such as ``` merge ``` and ``` rebase ``` which normally apply many commitss onto another branch.
#### Steps to follow
+ Make sure you are on the branch you want to apply the commit to. Use
  ```
    git checkout [branch locn]
  ```
+ Execute the following :
  ```
    git cherry pick [hash-key-of-the-commit-you-wanna-copy]
  ```
+ You will get the copy of the commit in your required branch
+ If you cherry-pick from a public branch, you should consider using
  ```
    git cherry-pick -x <commit-hash>
  ```
+ This will generate a standardized commit message. This way, you (and your co-workers) can still keep track of the origin of the commit and may avoid merge conflicts in the future. 
+ Inorder to delete that commit from the branch you copied from, give
  ```
    git reset --hard HEAD~1
  ```

    
 
