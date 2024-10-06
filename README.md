Learning git############


1. Created project
2. Created empty public repo in github
3. open project base folder in terminal
4. git init
5. git add .
6. git commit -m "first commit"
7. git branch -M main
8. git remote add origin https://github.com/avinashvermawf/sample-public-blank.git
9. git push -u origin main


Point 8 is incorrect. Even though this support has been removed in 2021, 
the github recommendation in newly created repo still show this command to be used.
Damn you github for wasting my time.

So the correct command is
1. Go to Profile->Settings->Developer Settings
2. Choose personal access tokens -> tokens(classic)
3. Generate new token -> Generate new token (classic)
4. Enter purpose in Note field
5. Select scopes -> public_repo and repo
6. create token and save somewhere safe
7. You can also use fine grained PAT option and select Content permissions read and write
8. Refer https://stackoverflow.com/questions/63906613/minimal-set-of-scopes-to-push-to-github-using-an-access-token
9. Use this command instead in step 8
   https://{Your PAT token}@github.com/avinashvermawf/sample-public-blank.git
(using curly braces above instead of less than greater than sign as git is ignoring those for some reason)


Trying second commit
1. We updated some text in github directly and committed the changes. Now we need to check how our local changes can be committed over it
2. There are multiple ways to resolve this conflict as mentioned in https://stackoverflow.com/questions/15745045/how-do-i-resolve-git-saying-commit-your-changes-or-stash-them-before-you-can-me
3. Using below commands for now
4. git pull       ---- this is combination of git fetch and git merge
5. if there is conflict pull will be aborted
6. git stash
7. git pull
8. git stash pop
9. this gave conflict with stashed changes section in file. Resolve conflict by removing the portions not required and section headers
10. git add .
11. git commit -m "second local commit"
12. git push

For using a remote repo first time local
1. git clone https://github.com/avinashvermawf/sample-public-blank     for public repo
2. git clone https://{Your PAT token}@github.com/avinashvermawf/sample-public-blank.git      for private repo

3. Step 1 clone is helpful only for read only. For write access use step 2.



Renaming default branch from main to master
1. Go to repo in github->Settings->Default branch->edit to master save.
2. If you have local changes, use git stash
3. If you have a local clone, you can update it by running the following commands.
git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a
4. git stash pop
5.  (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)



Use standard way of commiting changes to branch and creating PR
1. Go to github repo settings-> Rules -> Rulesets -> New branch ruleset
2. give some name to rule
3. Add target branch to default branch
4. Under Rules-> branch rules, check Require a pull request before merging
5. Select additional checkboxes that appeared based on requirement
6. Click on Create

Now if you will try to push to master, you will get error. To resolve follow below steps:
1. Create new branch either in github or by command
2. git branch new_branch      ---will create from current branch
3. git branch        -- this is to list out branches. for remote list use git branch -a
4. git checkout new_branch       -- switch local repo to new branch
5. git checkout -b new_branch ----- this is combination of 2 and 4
6. git push origin new_branch     -- to push to remote
7. git add .
8. git commit -m "commit in new branch"
9. git push --> this will show error
10. git push -u origin new_branch     --- -u means --set-upstream
11. Above command not require again on next commit. simply use git push

