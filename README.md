# B23 Day 2 : 

## Review : 
  - Version Control System 
  - Git 
    - local software to keep track of changes 
    - command line tool 
  
  - GitHub 
    - Online git repo hosting platform with many collaboration features
  
  - GitHub Desktop 
    - git client tool to make it easy to work with git and github 
    - easy git config set up 
      - provide name and email 
      - link text editors like sublime or others
      - easy Github.com account connection
  
  ### Git Terms
  - Working Direcory (Project folder)
    - This is where all the projects file stay 
  
  - Local Repository 
    - This is where git keep track of chanegs 
    - `.git` folder 
    - Commits : 
      - The changes from last point till this point
      - Name and email of the author of this commit
      - Commit message 
      - SHA : a comination of letetr and number to uniquely identify this commits 
  
  - Staging Area 
    - This is an hyphothetical area in between your working directory and Local repository 
    - You can visualize it as changes tab in GitHub Desktop or IntelliJ 


 - Remote Repository 
   - The repository under Github.com 
   - Can be shared on internet publicly 
   - Can be connected to local repository 


 - Ignoring the files we do not want to keep track of
   - `.gitignore` file is a special file that git use to stop git from keeping track of the files in the list seprated by new line 
    
    your filename here 
    your another file name here
    your folder namem here 
    or your pattern to describe files or folder
--- 

# Day 3 : 

## Review 

- Creating java project and setting up local repo 
- Adding `.gitignore` file
- Making initial commit by selecting all unversioned files 
- Making more commits to do more work 
- Publishing repository to remote GitHub.com 
  - Github.com remote repository has been created for you by Intellij directly 
  - Connection between local repo and remote repo is established 
  - local commits get pushed to remote repository
- Now do more work make more commits 
- Now we can simply `push` the local commits to remote 

- If we have commits in remote repository that we do not have locally -> `pull`  

--- 
### Getting Remote Repository to Local --> `Clone` 
When you clone , 
- It will get remote repository to your local computer
- It will have connection with the remote repo 
- It has all the history of that repo 
- If you own this remote repo , you can directly push more commits back to remote 


### Resetting the history 
We can go back in time in history and remove all the history from that point on 
```
1-2-3-4-5 commits 
reset -- hard 3
-->  1-2-3  and all changes in 4-5 will be lost 

reset soft-mixed  3 
--> 1-2-3 and 4,5 will be gone from history but the changes still be there
```
--- 
## Branching 

Branching allow you to work on new code without affecting the existing code safely. 
It's like opening new timeline. 

If you are satisfied with our work you can merge the changes into main timeline `master` branch. 


### Task 1

1. Create a new branch called `list`
2. Create a new class under `day3` package called `ListPractice` 
3. Make few commits under this branch by making few changes
4. Move your head to master 
5. Merge `list` branch into `master`

### Task 2
1. Create a new branch called `set`
2. Create a new class under `day3` package called `SetPractice` 
3. Make few commits under this branch by making few changes
4. Move your head to master 
5. Remove the `--no--ff` option before merging
6. Merge `list` branch into `master`


### Task 3 

1. Create a new branch `tc100` 
2. Update the movie class and make few commits 
3. now let's `checkout master` and generate conflict by updating same Movie class with different content 
4. commit this change in master
5. Merge `tc100` into master and deal with the conflict in 4 ways: 
   1. Abort the merge (`git` -> `Abort merge`)
   2. `Accept Theirs` to keep `tc100` version of the change
   3. `Accept Yours` to keep `master` version
   4. `merge` to have custom content as merge result

### Task 4  
1. Create a new branch `tc200` 
2. Create new Class called `Car` 
3. Make some changes and do 2 commits  
4. now let's `checkout master` 
5. Create a new class called `Animal` 
6. commit this change in master
7. Merge `tc200` into `master` and see the result
8. **CONFLICT** OR **NO CONFLICT** ?  NO


### Task 5 
1. Push all your local master commits to stay in sync with the remote 
2. Go to Github.com and update `FromGitHub.txt` file with different content and commit directly on Github.com 
3. Now from IntelliJ `fetch` to see the commit from the remote (just to get the info)
4. `Update Project` (`pull`) to get this changes from remote to local --> No conflict 

### Task 6 
1. On your local, update `FromGithub.txt` and commit 
2. On your remote , update `FromGithub.txt` with different content and commit (to simulate your team member pushed different update)
3. On your local , try to push this changes , it will be rejected because you have to `pull` down the changes before you can `push` 
4. It will give you option to `pull` and `merge` click on merge and boom! conflict !! 
5. Now resolve the conflict with the technique you learned previously 
   1. `Accept Theirs` to keep `tc100` version of the change
   2. `Accept Yours` to keep `master` version
   3. `merge` to have custom content as merge result
6. Now Push your result to the remote 
7. This is very common scenario while working with team members 




# Day 4 

## Recap 
Merge Conflict - can happen while you have commits in your master branch that the feature branch you are working on , and both of the commits editing same file with different contect 
### **Four ways to resolve**
- Abort merge 
- Accept Theirs (keep feature branch version)
- Accept Yours (keep the master branch version)
- Merge (have custom output)


#### **Task 1** 
Make sure you head is on master and there is no uncommitted changes 
1. Create a branch called `collection` 
1. Create new package called `day4`. 
2. Create a new class called `Conflict`
3. Make a commit for creating file 
4. Add this text inside main method  as comment : `This is collection branch content`
5. commit this change with meaningful commit message 
6. Move your `HEAD` to master
7. Create a package with same name called `day4`  
8. Create a new class with same name `Conflict`
9. Edit the file with the text inside `This is master branch content`
10. Make a commit and merge --> BOOM --> CONFLICT!!! resolve it 
11. In our case , we used last option with `custom output` as merge result 

#### **Task 2**
1. create a new branch called `collection2` 
2. Add a comment in the class `Conflict` with this message `MORE WORK ON COLLECTION2` 
3. Commit this change 
4. Checkout `master`
5. Add a different comment in the class `Conflict` with `This is the change collection2 branch does not know about` 
6. Commit this change into master
7. Now `merge` the `collection2` branch and boom! Conflict!!


## GitHub Flow 
A light weight flow for collaboration 

1. Create a branch called `us-100` 
2. Add a class called `TC001` under `day4` package 
3. Make few commits with good commit message
4. NOW: **`Push`** your branch to remote 
5. This will push your local `us-100` branch to remote (newly created)`origin/us-100` branch
6. Now go to your GitHub repository main page and observe Green `Compare and Open Pull Request` button show up. 
7. Click on it and it will open up pull request creation page 
   1. Add subject to describe what this change is about 
   2. Provide description in description section for more information 
   3.  And Click Create Pull request 
8. This is where conversation , code review can happen 
9. After all the review , team-member or assigned person can merge your code so it can be in origin/master 
10. Now back to IntelliJ , 
    1.  checkout `master` branch
    2.  `pull` down the changes by going to `git`->`update project` 
11. Now you are in sync with the remote 
