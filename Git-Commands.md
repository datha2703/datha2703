1. Clone
	1. git clone ssh://datha.krishnabhat%40oracle.com@alm.oraclecorp.com/fusionapps_fusionapps-qa_25331/fusionapps-qa.git c:\Code\fusionapps-qa --progress
	1. git clone --branch v2mib ssh://datha.krishnabhat%40oracle.com@alm.oraclecorp.com/fusionapps_fusionapps-qa_25331/fusionapps-qa.git c:\Code\fusionapps-qa --progress

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

1. Check out with commit id
git checkout -b <new_branch_name> <SHA1>

1. git move
git mv sample-data/APMTest/SASTestImplicitGrant1 sample-data/APMTest/SASTestImplicitGrant

1. Stash
git stash push -m my-stash
git stash -->  saves uncommitted changes to stash
git stash list --> list of stashes
git stash pop stash@{0} --> where 'stash@{0}' is name that git gave to my-stash