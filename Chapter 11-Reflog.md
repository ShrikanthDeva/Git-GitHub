# Reflog

Git keeps track of updates to the tip of branches using a mechanism called reference logs or "reflogs" in local repositories. 

### USE CASE :
  + Recovering Deleted Commits.
  + Recovering Deleted Branches.
  + Timed Reflog

#### Steps To Recover Deleted Commits

+ Use command
  ```
  git reflog
  ```
+ It shows the all the logs of Git. Entries are arranged in chronological order (i.e) most recent at the top.
+ Copy the required state before's **HASH_KEY** and use,
  + ```
    git reset HEAD~1
    ```
    (OR)
    
  + ```
      git branch [branch name] [hashkey]
    ```
    
#### Steps To Recover Deleted Branches

+ Say you have to delete a feature branch, you ***CHECKOUT*** from it and delete it.
+ But , now you regret it and think you need the deleted feature branch again.
+ Use command
  ```
  git reflog
  ```
+ From the log history copy the ***HEASH_KEY*** of the previous state of ***CHECKOUT***.
+ Use command
  ```
  git branch [branch-name] [hashkey]
  ```
+ You, will be back to your feature branch.

#### Timed Reflog
+ Every reflog entry has a timestamp attached to it. These timestamps can be leveraged as the qualifier token of Git ref pointer syntax. 
+ This enables filtering Git reflogs by time. The following are some examples of available time qualifiers:
  ```
    1.minute.ago
    1.hour.ago
    1.day.ago
    yesterday
    1.week.ago
    1.month.ago
    1.year.ago
    yyyy-mm-dd.hr:min:sec
  ```
+ These Time qualifiers can be combined too ```1.day.2.hours.ago```
+ Additional plural forms are accepted ``` 5.minutes.ago```
+ Eg -
  ```
    git reflog --since="2 days ago" --all
  ```
  
