# CLAUDE.md — platonic-fathers

## Git policy (differs from my work repos!)
- You MAY run git: add, commit, push, pull --rebase, status, diff, log
- Commit style: conventional commits (feat:/fix:/chore:/revert:), no ticket refs
- ALWAYS `git pull --rebase` before push (GitHub bots commit to main: CNAME, future Librarian PRs)
- NEVER: force-push, amend already-pushed commits, rewrite history, change git config
- Only `git add` specific named files — never `git add -A` or `git add .`
- After pushing, report the commit hash and one-line summary

## Project facts
- Deploys automatically: push to main → GitHub Pages → live at rhizomeoftheascent.com in ~30s
- rhizome/index.html and timeline artifacts come from a separate Claude thread;
  when replacing them, overwrite the whole file — do not hand-edit their internals
- Exception — surgical fixes: when a fix is scoped to one mode or section and a full
  regeneration would risk the parts that already work, edit that section in place instead.
  Say so in the report, keep the untouched parts byte-identical, and flag to the
  originating thread that the file has diverged from its generated version.
- quotes.json: the (VERIFY) flags in translation fields are intentional — never remove
  one unless explicitly told the quote has been verified
- .github/workflows/librarian.yml is a stub — do not enable the cron
