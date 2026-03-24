# commit

Create a well-formatted git commit for the current changes.

## When to use

Invoke `/commit` when you have staged or unstaged changes and want Claude to:
- Review what changed
- Write a concise, meaningful commit message
- Stage relevant files and create the commit

## Prompt

```
Review the current git diff (staged and unstaged). Then:

1. Run `git status` and `git diff` to understand what changed
2. Check recent `git log --oneline -5` to match the repo's commit message style
3. Stage relevant files (prefer specific file names over `git add -A`)
4. Write a commit message that:
   - Uses imperative mood ("Add", "Fix", "Update", not "Added" or "Adding")
   - Summarizes the *why*, not just the *what*
   - Keeps the subject line under 72 characters
   - Does not end the subject line with a period
5. Create the commit using a HEREDOC for the message

Do not push. Do not amend existing commits. If there is nothing to commit, say so.
```

## Example usage

```
/commit
/commit -m "Add dark mode toggle"
```

## Notes

- Works best after you've made a focused set of related changes
- If changes span multiple concerns, ask Claude to split into separate commits before running
