## Git Exercise

#### Q1: The command to check which version of Git (if any) is installed
Answer: `git --version`
```
git version 2.35.1.windows.2
```
#### Q2: Check the status of the Git
Answer: `git status`
```
On branch feature/NguyenHoangDuy
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   day2/labs/Git-Answer.md

no changes added to commit (use "git add" and/or "git commit -a")
```
#### Q3: Add index.html to the Staging Enviornment
Answer: `git add index.html`
```
On branch feature/NguyenHoangDuy
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   day2/labs/Git-Answer.md
```
#### Q4: Git add all files include deleted, modified and added
Answer: `git add --all` or `git add -A`
```
On branch feature/NguyenHoangDuy
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   day2/labs/Git-Answer.md
```
#### Q5: Commit the changes to the current repository with the message "First release!"
Answer: `git commit -m "First release!"`
```
[feature/NguyenHoangDuy 533667b] Update Git-Answer file
 1 file changed, 6 insertions(+), 3 deletions(-)
```
#### Q6: Commit the updated files directly, skipping the staging environment
Answer: `git commit -a -m "Commit skipping staging"`
```

```
#### Q7: Show status of git
Answer: `git status --short`
```
 M day2/labs/Git-Answer.md
```
#### Q8: View the history of commits for the repository
Answer: `git log --oneline`
```
533667b (HEAD -> feature/NguyenHoangDuy) Update Git-Answer file
5e9138b (origin/feature/NguyenHoangDuy) Update Git-Answer file
c151868 Update Git-Answer file
94dd477 Commit skipping staging
9794f2b Add Answer file
b788343 Add README
125ee9a (origin/feature/thele, origin/feature/ChuDaiDuong, main) Update doc about git
0a33d1b Update Readme
2213b10 Init day1
53d7633 Update README.md
64cbecb Update Readme
2daee09 Update Readme
5125fde Initial commit
```
#### Q9: Create a new branch called feature/hello-world-images, not switch to new branch
Answer: `git branch feature/hello-world-images`
```
fatal: a branch named 'feature/NguyenHoangDuy' already exists
```
#### Q10: List the existing branches
Answer: `git branch`
```
* feature/NguyenHoangDuy
  main
```
#### Q11: Move to the feature/hello-world-images branch
Answer: `git checkout feature/hello-world-images`
```
Already on 'feature/NguyenHoangDuy'
M       day2/labs/Git-Answer.md
```
#### Q12: Create a new branch called feature/hello-world-images-v2 and switch to new branch
Answer: `git checkout -b feature/hello-world-images-v2`
```
fatal: a branch named 'feature/NguyenHoangDuy' already exists
```
#### Q13: Push the current branch to its default remote origin
Answer: `git push`
```
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 6 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 492 bytes | 492.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/vytran4love/DEVOPS-TOOA05.git
   5e9138b..533667b  feature/NguyenHoangDuy -> feature/NguyenHoangDuy
```
#### Q14: Create .gitignore then in .gitignore add a line to ignore all .temp files
Answer: `echo *.temp > .gitignore`
```
 cat .\.gitignore
*.temp
```
#### Q15: In .gitignore add a single line to ignore all files named temp1.log, temp2.log, and temp3.log
Answer: `echo temp[1-3].log> .gitignore`
```
echo temp[1-3].log> .gitignore
temp[1-3].log>
.gitignore
```
#### Q16: In .gitignore, ignore all .log files, except main.log
Answer: 

> `echo "*.log`
> 
> `!main.log" > .gitignore`

```
*.log
!main.log
```
#### Q17: Change the contenxt of message to "Update details message for second release"
Answer: `git commit --amend -m "Update details message for second release"`
```
[feature/NguyenHoangDuy 83b4b79] Update details message for second release
 Date: Thu Apr 21 20:48:36 2022 +0700
 1 file changed, 6 insertions(+), 3 deletions(-)
```
#### Q18: Revert the latest commit
Answer: `git reset --soft HEAD~1`

> Before
```
5e9138b (HEAD -> feature/NguyenHoangDuy) Update Git-Answer file
c151868 Update Git-Answer file
94dd477 Commit skipping staging
9794f2b Add Answer file
b788343 Add README
125ee9a (origin/feature/thele, origin/feature/ChuDaiDuong, main) Update doc about git
0a33d1b Update Readme
2213b10 Init day1
53d7633 Update README.md
64cbecb Update Readme
2daee09 Update Readme
5125fde Initial commit
```
>After
```
c151868 (HEAD -> feature/NguyenHoangDuy) Update Git-Answer file
94dd477 Commit skipping staging
9794f2b Add Answer file
b788343 Add README
125ee9a (origin/feature/thele, origin/feature/ChuDaiDuong, main) Update doc about git
0a33d1b Update Readme
2213b10 Init day1
53d7633 Update README.md
64cbecb Update Readme
2daee09 Update Readme
5125fde Initial commit
```
#### Q19: Revert the two last commits
Answer: `git reset --soft HEAD~2`
```
9794f2b (HEAD -> feature/NguyenHoangDuy) Add Answer file
b788343 Add README
125ee9a (origin/feature/thele, origin/feature/ChuDaiDuong, main) Update doc about git
0a33d1b Update Readme
2213b10 Init day1
53d7633 Update README.md
64cbecb Update Readme
2daee09 Update Readme
5125fde Initial commit
```
#### Q20: Reset to the commit with the hash abc1234
Answer: `git revert abc1234`