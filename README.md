<!---
{
  "id": "474307f2-a30c-4639-9379-298bf1a4c00b",
  "depends_on": [],
  "author": "Stephan Bökelmann",
  "first_used": "2025-03-26",
  "keywords": ["learning", "exercises", "education", "practice"]
}
--->

# Using Git on Your Local Machine

## 1) Introduction

Git is a distributed version control system originally developed by Linus Torvalds to support the development of the Linux kernel. Since then, it has become one of the most widely used tools for managing source code in software projects of all sizes.

When working with software—especially in teams—it quickly becomes clear that keeping track of changes, coordinating contributions, and avoiding conflicting edits are non-trivial challenges. Git was designed to help address these issues, offering developers a robust way to track the history of a project, experiment safely, and collaborate effectively.

But what *is* Git, really? While we often talk about Git in terms of versioning and collaboration, at its core, Git is a tool for managing files within a directory over time. It records snapshots of your project and allows you to move back and forth between them, compare changes, and decide what should be included or excluded from the official record.

Learning the entirety of Git’s feature set can take years, and even seasoned developers continue to discover new uses and workflows. However, for now, we will focus on the essentials of working with a local Git repository.

A Git repository is essentially a hidden storage area—created by Git—inside your project directory. When you run `git init`, Git creates a `.git` folder in the root of your project. This folder holds all the internal data Git needs to manage your code history, but you won't normally interact with it directly. Instead, you’ll use Git commands to manage your files and history.

In this guide, you will learn about:

- the *working directory* (where you edit files),
- the *staging area* (where you prepare changes),
- and *commits* (snapshots of your project).

You’ll also gain experience with:

- creating a repository,
- tracking and reviewing changes,
- navigating commit history,
- and discarding unwanted edits.

By the end of this introduction, you’ll have a solid grasp of Git’s basic operations and how to use it confidently on your local machine.

**Note:** Before getting started, make sure Git is installed on your system. Open your terminal and run:

```bash
git --version
```

If Git is installed, you’ll see a version number. If not, you can install it using your package manager. For example, on Ubuntu:

```bash
sudo apt install git
```

Once installed, you're ready to begin managing your projects with Git.


### 1.1) Further Readings and Other Sources
- [Pro Git – Chapters 1 & 2](https://git-scm.com/book/en/v2)  
  The official Git book by Scott Chacon and Ben Straub. A comprehensive and free resource to understand local Git workflows.
- [Git: The Simple Guide](https://rogerdudler.github.io/git-guide/)  
  A concise and practical walkthrough of basic Git usage, great for beginners and quick reference.
- [Learn Git Branching](https://learngitbranching.js.org/)  
  An interactive visual tutorial that helps you master Git’s commit model and branching through exercises and visualizations.


## 2) Tasks

1. **Configure Git**: Run the following commands to configure Git globally on your system:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "Your Email"
   git config --global core.editor "vim"
   git config --global init.defaultBranch master
   ```

2. **Initialize a Repository**:
   - Create a new directory named `my-git-project` in your home directory.
   - Navigate into it and run `git status`.
   - Initialize it with `git init` and observe how `git status` output changes.
   - Create a file `file.txt`, write some content, and run `git status` again.
   - Stage it with `git add file.txt`, then run `git status`.
   - Commit the file using `git commit`.
   - Write the message `Initial commit` in the editor that opens, then save and close it with `:wq` in `vim`.

<details>
  <summary>Note on `git status`</summary>
  `git status` will help you track the current state of your working directory and staging area. Run it after each step and try to predict its output.
</details>

3. **Understand the Three Areas**:
   Git manages your project in three simultaneous areas:
   - **Working Tree**: The files you're actively editing.
   - **Staging Area**: Files marked to be included in the next commit.
   - **Repository**: The committed history stored in Git.

   Steps:
   - Modify `file.txt` (but don’t stage it).
   - Run `git status`.
   - Stage with `git add file.txt` and run `git status`.
   - Commit with message `"Added more content to file.txt"`.
   - Modify the file again, stage it, then commit with `git commit -m "Quick commit"`.

4. **Inspect Commit History**:
   - Run `git log --oneline` to see past commits.
   - Copy the hash of the initial commit and checkout with `git checkout <hash>`.
   - Observe the detached HEAD state using `git status`.
   - Open `file.txt` to compare with newer versions.
   - Return to the latest version using `git checkout master`.

5. **Discard Changes**:
   - Modify `file.txt` but don’t stage.
   - Check file status using `git status`.
   - Discard changes using `git restore file.txt`.
   - Modify again, stage, and then unstage using `git restore --staged file.txt`.
   - Use `git restore .` to discard *all* changes.

## 3) Questions

1. What does the command `git init` do?
2. How can you check which files have been staged for the next commit?
3. What is the purpose of the commit message, and why is it important?
4. What does `git add` do, and how does it move changes from the working tree to the staging area?
5. Why is it useful to have a staging area separate from the working tree?
6. How does providing a commit message inline with `-m` differ from using a text editor?
7. What information does `git log --oneline` provide compared to `git log`?
8. What does the detached HEAD state mean, and why is it important to return to the master branch after checking out an old commit?
9. How does Git ensure the safety of your current changes when navigating through the history?
10. How does `git restore` differ from `git checkout` when used to discard changes?
11. Why is it important to review your changes carefully with `git status` before discarding them?
12. What is the difference between restoring changes in the working tree and unstaging changes from the staging area?



## 4) Advice
Git is a powerful tool, but it can seem complex at first. Focus on understanding the basic workflow: modifying files in the working tree, staging changes, and committing them to the repository. Commands like git log, git checkout, and git restore are essential for navigating and managing your repository. Always review your changes carefully using git status before committing or discarding them. With practice, you will gain confidence and develop efficient habits for managing code with Git.

