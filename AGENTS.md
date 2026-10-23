# Rules for coding agents in this repository

You are working with a FacMed Hack team (6–7 November 2026, Campus Biotech, Geneva). The people you work with are researchers, clinicians and students; many have never used git. You run git for them, following the rules below. When a rule stops you, explain why to the human in one sentence.

## Git

1. **Start of a task:** `git pull` on `main`, then create a branch `<firstname>/<short-topic>`.
2. **Commit small and often:** each meaningful step, and at least every 30 minutes of work. Write the message in plain English and end it with `Co-authored-by: <agent name>`. When two humans pair, add the second human as co-author too. The contribution history is how each person's work is recognised (ECTS credits), so commit under the human's own git identity.
3. **Never commit data**, notebook outputs with participant-level values, secrets or keys. The pre-commit hooks block files over 1 MB, data formats (`.csv`, `.edf`, `.mp4`, `.wav`, `.parquet`, `.nii`…) outside `examples/`, and secret patterns. If a commit is blocked, do not work around the hook: tell the human what was blocked and why.
4. **Merge through a pull request:** push the branch, open a PR with `gh pr create`, fill in the template (what changed, how it was checked), add an entry to `NOTES.md`, then squash-merge and delete the branch.
5. **Conflicts:** merge `main` into the branch. Resolve automatically only when the changes do not overlap; otherwise explain the conflict in plain language and ask the human which version to keep.
6. **Never** force-push, rewrite history, change repository settings, or delete other people's branches.
7. **Before the final presentation:** tag the version shown at the finals: `git tag demo && git push origin demo`.

## Data

- Real data never enters this repository. `data/sources.yaml` says where each dataset lives and how to get it; read it before loading anything.
- Downloaded data goes to `data/raw/` (ignored by git). On the HPE environment, team data is mounted read-only at `/data/<challenge>`.
- `examples/` holds a small **synthetic** sample so the code runs on any laptop. Generate it; never copy rows from real data into it.
- No identifiable clinical data is used during the event.

## Work

- Plan before acting on anything non-trivial: say what you will do and wait for the human's OK.
- Heavy computation (training, video processing) runs as a job on the GPUs (`sbatch` where the HPE environment provides it), never in a notebook on a laptop.
- Put code in `src/`, exploration in `notebooks/`, and figures meant for the README or the pitch in `results/figures/` (small PNG or SVG).
- After each change, say in plain language what you changed and how the human can check it.
