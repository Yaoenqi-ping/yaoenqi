---
name: submit-github
description: Use when submitting, committing, or pushing the current project to GitHub at https://github.com/Yaoenqi-ping/yaoenqi. Triggers on "提交到 github", "提交到github", "推送到 github", "上传到 github", "github commit", "github push", or any request to publish local changes to the GitHub repository.
---

# Submit to GitHub (提交到 GitHub)

Commit the whole project and push the current branch to the GitHub repository:

```
https://github.com/Yaoenqi-ping/yaoenqi
```

## Remote

The project may already use `origin` for Gitee. Do NOT overwrite it. Use a dedicated remote named `github`:

```
git remote get-url github
# if missing:
git remote add github https://github.com/Yaoenqi-ping/yaoenqi.git
```

If a `github` remote exists with a different URL, update it:

```
git remote set-url github https://github.com/Yaoenqi-ping/yaoenqi.git
```

## Workflow

1. Inspect state before doing anything:

```
git status
git diff
git log --oneline -5
```

2. Ensure the GitHub remote exists as described above.

3. Stage everything and commit:

```
git add -A
git commit -m "<concise message describing the change>"
```

If there is nothing to commit, skip the commit and continue to push.

4. Push the current branch (`master`) to GitHub. On the first push, set upstream:

```
git push -u github master
```

For subsequent pushes:

```
git push github master
```

5. Verify the result:

```
git status
git log --oneline -1
```

## Notes

- Default branch here is `master`.
- If the push is rejected because the remote has commits, fetch and rebase first:
  `git pull --rebase github master`, then push again.
- If the remote repository is empty, pushing directly works.
- Never force-push unless explicitly asked.
- Never commit secrets or credentials; inspect staged files if unsure.
- If authentication fails, report the error and ask the user to log in to GitHub (e.g. `gh auth login` or configure a credential helper).
- If `git` is blocked by a permission rule, ask the user to allow the command.
