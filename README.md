# Merge Conflicts
- When merging two branches that modify the same line of a file, a conflict arises if it's unclear whether to take changes from branch 1 or branch 2. Both authors have the same intentions, and merging both changes would conflict with their individual goals. This is when Git cannot decide which change to adopt.
- `git branch conflict1`, check whether the new branch is created or not:`git log --all --graph`.
- Switch to conflict branch
`git checkout conflict1`, create a file named `conflict.js` with the content `console.log('conflict');` and pick up the changes: `git add .`.
- commit: `git commit -m "conflict 1"`, check whether the conflict branch has the recent commit with:`git log --all --graph`.
- Now switch back to the master branch with `git checkout master`, create `conflict.js` file and change the content to `console.log('conflict+');`, save changes `git add .`, commit changes `git commit -m "conflict2"` , check the commits: `git log --all --graph`, here we have a `conflict1` commit from the `conflict1` branch and `conflict2` commit from the master branch, they both made changes to the same file and the same line of code. Now this is when we will have a merge conflict. 
- We're gonna merge `conflict1` branch into master, and save the results on master. `git merge conflict1 -m "Merge conflict"`.
- We will get this error: 
```bash
CONFLICT (add/add): Merge conflict in conflict.js
Automatic merge failed; fix conflicts and then commit the result.
```
- Now we need to go back to our code and git gives an option to let us choose the line from the current branch, or the conflict branch, we need to choose one of them. 
- We just need to delete the part that we don't want in the code, we delete everything else and keep the line of code from the `conflict1` branch.
- We need to pick the changes, `git add .`, commit the code, `git commit -m "merge conflict resolved"`
Now we successfully merged the `conflict1` branch to master.
