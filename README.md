# change_default_git_branch_to_master
# Change GitHub default branch from master to main

> 5 simple steps that I tested and used to make the change in under 1 minute.

1. Move the `master` branch to `main`

    ```bash
    git branch --move master main
    ```

2. Push `main` to remote repo

    ```bash
    git push --set-upstream origin main
    ```

3. Point `HEAD` to `main` branch

     ```bash
     git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
     ```

4. [Change default branch](https://docs.github.com/en/github/administering-a-repository/managing-branches-in-your-repository/changing-the-default-branch) to `main` on GitHub

    - Navigate in your browser to your [GitHub](https://github.com) repository.
    - From the left rail, click **Settings** -> **Branches** and change the default branch to `main`

5. Delete `master` branch on the remote repo

    ```bash
    git push origin --delete master
    ```

## Updating a local clone after a branch name changes

After you rename a branch in a repository on GitHub, any collaborator with a local clone of the repository will need to update the clone.

From the local clone of the repository on a computer, run the following commands to update the name of the default branch.

```bash
git branch -m OLD-BRANCH-NAME NEW-BRANCH-NAME
git fetch origin
git branch -u origin/NEW-BRANCH-NAME NEW-BRANCH-NAME
git remote set-head origin -a
```

Optionally, run the following command to remove tracking references to the old branch name.

```bash
git remote prune origin
```

> Source: [GitHub: Updating a local clone after a branch name changes](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch#updating-a-local-clone-after-a-branch-name-changes)

---

To [initialize](https://git-scm.com/docs/git-init#Documentation/git-init.txt---initial-branchltbranch-namegt) a new Git repository
and set the default branch to `main`:

```bash
git init --initial-branch=main
```

---

- Source: [Steven Mortimer, 5 steps to change GitHub default branch from master to main](https://stevenmortimer.com/5-steps-to-change-github-default-branch-from-master-to-main/)
- Snippet: <https://github.com/Guenbay/change_default_git_branch_to_master/>

