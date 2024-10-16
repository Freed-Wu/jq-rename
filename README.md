# jq-rename

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/Freed-Wu/jq-rename/main.svg)](https://results.pre-commit.ci/latest/github/Freed-Wu/jq-rename/main)
[![github/workflow](https://github.com/Freed-Wu/jq-rename/actions/workflows/main.yml/badge.svg)](https://github.com/Freed-Wu/jq-rename/actions)

[![github/downloads](https://shields.io/github/downloads/Freed-Wu/jq-rename/total)](https://github.com/Freed-Wu/jq-rename/releases)
[![github/downloads/latest](https://shields.io/github/downloads/Freed-Wu/jq-rename/latest/total)](https://github.com/Freed-Wu/jq-rename/releases/latest)
[![github/issues](https://shields.io/github/issues/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/issues)
[![github/issues-closed](https://shields.io/github/issues-closed/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/issues?q=is%3Aissue+is%3Aclosed)
[![github/issues-pr](https://shields.io/github/issues-pr/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/pulls)
[![github/issues-pr-closed](https://shields.io/github/issues-pr-closed/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/pulls?q=is%3Apr+is%3Aclosed)
[![github/discussions](https://shields.io/github/discussions/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/discussions)
[![github/milestones](https://shields.io/github/milestones/all/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/milestones)
[![github/forks](https://shields.io/github/forks/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/network/members)
[![github/stars](https://shields.io/github/stars/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/stargazers)
[![github/watchers](https://shields.io/github/watchers/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/watchers)
[![github/contributors](https://shields.io/github/contributors/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/graphs/contributors)
[![github/commit-activity](https://shields.io/github/commit-activity/w/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/graphs/commit-activity)
[![github/last-commit](https://shields.io/github/last-commit/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/commits)
[![github/release-date](https://shields.io/github/release-date/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/releases/latest)

[![github/license](https://shields.io/github/license/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename/blob/main/LICENSE)
[![github/languages](https://shields.io/github/languages/count/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)
[![github/languages/top](https://shields.io/github/languages/top/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)
[![github/directory-file-count](https://shields.io/github/directory-file-count/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)
[![github/code-size](https://shields.io/github/languages/code-size/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)
[![github/repo-size](https://shields.io/github/repo-size/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)
[![github/v](https://shields.io/github/v/release/Freed-Wu/jq-rename)](https://github.com/Freed-Wu/jq-rename)

Like [perl-rename](https://github.com/subogero/rename), However, it uses jq
expression.

```sh
$ jq-rename --help
usage: jq-rename [OPTION]... [--] JQEXPR FILE...
Rename FILE(s) using JQEXPR on each filename.

options:
  -b, --backup                 make backup before removal
  -c, --copy                   show program's version number and exit
  -f, --force                  remove existing destinations, never prompt
  -i, --interactive            prompt before overwrite
  -l, --link-only              link file instead of rename
  -n, --just-print, --dry-run  don't rename, implies --verbose
  -v, --verbose                explain what is being done
  -z, -S, --suffix=SUFFIX      set backup filename suffix
  -h, --help                   display this help and exit
  -V, --version                output version information and exit
$ jq-rename -c -n 'gsub("foo"; "bar")' foo1.txt foo2.txt
cp foo1.txt bar1.txt
cp foo2.txt bar2.txt
$ jq-rename -n 'split(".") | . as $arr | .[0] | tonumber | . + 1 | tostring |
"\(.).\($arr[1])"' 1.txt 2.txt
mv 1.txt 2.txt
mv 2.txt 3.txt
```

## Dependencies

- [jqjq](https://github.com/wader/jqjq): provide `eval`, which is
  [a feature request](https://github.com/jqlang/jq/issues/384) of official `jq`
- coreutils: `cp`, `mv`, `ln`
- findutils: `xargs`

## Install

## AUR

```sh
paru -S jq-rename
```

## Manual

Copy `jqjq.jq` to `/usr/lib/jq/`.

## Todo

- combined short options
- more command line options of perl-rename
- return exit code
- `--help` and `--version` output to stdout not stderr
