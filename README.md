# gh-actions-demo
Github Actions PoC demo repo for several programming languages and associated linters in one repo simultaneously:

1. Bash (Shellcheck)
1. Python (flake)
1. Perl (perl -c and prove)
1. Ruby (ruby -wc)

See `.github/workflows/` for the build scripts.

Github Actions work by starting Docker containers for each OS or programming language version you specify. If you're using Github anyway for source control, and
your automation is amenable to Github Actions, then it's a very useful option compared to Jenkins, etc., and reduces administration.

When there's multiple workflow scripts, all are executed in parallel. The workflow script has to decide by directory or file extension what the run actions are.

Only push events (not pull) are specified in this repo to avoid reported security problems with cloned repos used in unauthorized bitcoin mining via pull requests.

Note that as of July 2021, workflow scripts do not know which specific files were changed in a git commit, so it's up to you to
either process all files new and old, or calculate the change list if necessary. Two different techniques are:

1. https://dev.to/scienta/get-changed-files-in-github-actions-1p36
1. https://github.community/t/is-it-possible-to-run-the-job-only-when-a-specific-file-changes

## PoC Results

The motivation for this PoC was to evaluate basic functionality for a multi-language REST API SDK repo.

The positive results are that:

1. The functionality meets the basic requirements for linting files by language for multiple languages.
1. The matrix-style permutation of Docker containers by OS and language version is remarkably powerful and easy to use.

The remaining concerns are:

1. It should be easier to enumerate the file changes list in a commit, but there are workarounds (see above.)
1. Github Actions is Github-specific, so there's lock-in for complex workflow scripts.
1. There are costs/limits for using Github Actions, so either the duration of tests and matrix options need to be limited, or the cost budgeted.
