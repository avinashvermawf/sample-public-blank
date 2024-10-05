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
   https://<Your PAT token>@github.com/avinashvermawf/sample-public-blank.git
