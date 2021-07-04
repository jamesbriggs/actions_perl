# gh-actions-demo
Github Actions demo repo for several programming languages and associated linters in one repo simultaneously:

1. Bash (Shellcheck)
1. Python (flake)
1. Perl (perl -c and prove)
1. Ruby

See `.github/workflows/` for build scripts.

When there's multiple workflow scripts, all are executed in parallel. The workflow script has to decide by directory or file extension what the run actions are.

Note that workflow scripts do not know which specific files were changed in a git commit, so it's up to you to
either process all files new and old, or calculate the change list if necessary. Two different techniques are:

1. https://dev.to/scienta/get-changed-files-in-github-actions-1p36
1. https://github.community/t/is-it-possible-to-run-the-job-only-when-a-specific-file-changes
