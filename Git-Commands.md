1. Check out new branch and publish branch
git checkout -b <branch>
git push -u origin <branch>

1. Pushing empty commit to trigger build
git commit --allow-empty -m "Empty-Commit"
git push origin

1. Deleting local branch
git branch --delete Datha/SPS-2910-SASTest1

1. Deleting remote branch
git push origin --delete Datha/SPS-3423-APM-Postman

1. To see all remote branch names
git branch -r

1. To see Local branch
git branch

1. Reset hard
git fetch origin
git reset --hard origin/trunk

1. Cleaning or Removing untracked files
View untracked files - git clean -n
git clean -fdx
