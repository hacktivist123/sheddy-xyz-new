---
title: 'Fixup Commit in Git'
draft: false
date: '2025-01-27'
lastmod: '2024-03-06'
summary: "Learn how to update a commit with a local file change using a fixup commit"
tags: ['Git']
---



You can ammend a remote commit with a file change in your local repo by running this command:

```bash

git --no-pager add <local-file-you-want-to-add-to-a-commit> && git --no-pager commit --fixup=<commit-hash-you-want-to update> && git --no-pager rebase -i --autosquash <commit-hash>

```

This command sequence will:
1. Stage the specific file you want to add to the target commit
2. Create a fixup commit that will be merged into the target commit
3. Start an interactive rebase that will automatically squash the fixup commit into the target commit

Save the changes and force push.

```bash
git push <branch-name> --force-with-lease

```

If you have local changes you haven't committed yet, the rebase will fail. You can solve this by temporarily stashing your local changes and then running the rebase command like this:

```bash
git stash -u && \
git rebase -i --autosquash <commit-hash-you-edited-earlier> && \
git stash pop
```
