1. What is the difference between a working directory, the staging area, a commit, and a remote repository?

The working directory is where we can edit and create files. The staging area contains changes that have been selected for the next commit. A commit is just a view of staged changes saved in the repository's history. A remote repository is a version of the repository hosted elsewhere, like GitHub.

2. What do `HEAD`, `main`, and `origin` refer to in a normal repository?

HEAD refers to the current position in the repository. main is the primary branch, origin is the conventional name for the remote repository from which the project was cloned.

3. Why should you pull or fetch recent `main` changes before starting new work?

Fetching or pulling recent changes helps ensure that we start from an up-to-date version of main. This reduces the chance of conflicts

4. What is the difference between fetching and pulling?

Fetching downloads new commits and references from a remote repository without integrating them into the current branch.
Pulling fetches those updates and then integrates them into the current branch, usually through a merge or rebase.

5. What is the difference between merging and rebasing? When is rebasing a shared branch dangerous?

Merging combines the histories of two branches and may create a merge commit. Rebasing moves a branch's commits onto a new base, creating new commit IDs and a more linear history.
Rebasing a shared branch is dangerous because it rewrites history that other people may already have based their work on, so there's a chance of confusion

6. Why are pull requests useful even though they are not part of Git itself?

Because They allow teammates to review changes and discuss improvements. We can run automated tests, and check code before merging it into a shared branch.

7. In Task 4, Git created a new commit called `Merge branch 'can'`. Why was a new commit needed?

Git created the merge commit because changes from the can branch needed to be integrated into the current branch. The merge commit records the integration and connects the histories of both branches.

8. In Task 5, both branches changed `src/main.cpp`. Why did `can_id` merge by itself but `@version` and `loop()` did not?

Git can automatically merge changes when they affect separate parts of a file without conflicting. The can_id change did not conflict with the other branch's changes, so Git merged it automatically. The @version line and loop() contained competing changes in overlapping sections, so Git required me to resolve those conflicts manually.

9. In Task 6, which workflow ran when you pushed to `ci`, and which did not? Why? What does the CI workflow protect the team from?

The PlatformIO CI workflow ran when we pushed to the ci branch because it runs whenever there is a push to the repository. It installs PlatformIO and builds the code to check if it compiles properly. The Doxygen GitHub Pages workflow did not run because it only runs when changes are pushed to main. The CI workflow helps prevent code that does not compile from being merged into the project.

10. What does a .gitignore file do, and why does it not remove a file that was already committed? Why is `.pio` in `.gitignore`?

The gitignore file tells Git which untracked files and directories to ignore, such as generated files and build outputs. It does not remove files that Git is already tracking; those files must be explicitly removed from tracking if necessary.
The .pio directory contains generated PlatformIO build files and downloaded dependencies that can generally be recreated, so ignoring it avoids committing unnecessary files.
