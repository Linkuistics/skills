# skills — moved to Linkuistics/grove

**This repository is archived.** Its contents — the `linkuistics` and
`testanyware` skill plugins, and the `linkuistics` plugin marketplace — now live
in **<https://github.com/Linkuistics/grove>**, alongside the `grove` workstream
CLI they change in lockstep with. The full history was grafted in, so `git blame`
on the skill files still traces past the move.

## If you use the Claude Code marketplace

Run both of these:

```
/plugin marketplace remove linkuistics
/plugin marketplace add Linkuistics/grove
```

**Do this even though nothing looks broken.** An archived GitHub repo stays
readable, so Claude Code's marketplace auto-update keeps *succeeding* against
this repo — the skills simply freeze at the last commit before the archive, with
no error surfaced.

Nothing else changes. The marketplace keeps the name `linkuistics` — its identity
is the `name` field in `marketplace.json`, never the repo URL — so
`linkuistics@linkuistics`, `testanyware@linkuistics` and every
`linkuistics:<skill>` reference keep working untouched.

## If you use `install.sh` (Codex, Gemini CLI, other SKILL.md harnesses)

Re-clone from the new repo and re-run the script:

```
git clone https://github.com/Linkuistics/grove.git
cd grove
./install.sh
```

The symlinks this script writes point into the clone, so the old clone must be
replaced rather than pulled.

## Why

The two components change together: most `grove` changes need a matching skill
change, and while they lived in separate repos no single commit could carry both
— this repo's history contains three commits whose entire content was a pointer
at the other one. The reasoning and the rejected alternatives are in
[`docs/adr/skills-monorepo.md`](https://github.com/Linkuistics/grove/blob/main/docs/adr/skills-monorepo.md).
