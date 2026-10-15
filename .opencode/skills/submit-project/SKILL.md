---
name: submit-project
description: Use when submitting, committing, or pushing the current project to its Gitee (码云) remote. Triggers on "提交项目", "提交代码", "push", "git commit", "推送到 gitee", or any request to publish local changes to the remote repository.
---

# Submit Project (提交项目)

Commit all current changes and push the branch to the configured Gitee remote.

## Remote

This project pushes to Gitee:

```
https://gitee.com/medicine-grace-prayer/yeq
```

## Workflow

1. Inspect state before doing anything:

```
git status
git diff
```

2. Ensure the Gitee remote exists (add it only if missing):

```
git remote get-url origin 2>$null
# if missing:
git remote add origin https://gitee.com/medicine-grace-prayer/yeq.git
```

3. Stage and commit. Stage only intended files; never commit secrets.

```
git add -A
git commit -m "<concise message describing the change>"
```

4. Push the current branch to the remote. On the first push, set upstream:

```
git push -u origin master
```

For subsequent pushes:

```
git push
```

## Notes

- Default branch here is `master`.
- If the remote already has commits, pull/rebase before pushing:
  `git pull --rebase origin master` then `git push`.
- Never force-push unless explicitly asked.
- If `git` is blocked by a permission rule, ask the user to allow the command.
