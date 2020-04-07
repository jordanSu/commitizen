[![Github Actions](https://github.com/commitizen-tools/commitizen/workflows/Python%20package/badge.svg?style=flat-square)](https://github.com/commitizen-tools/commitizen/actions)
[![Conventional
Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg?style=flat-square)](https://conventionalcommits.org)
[![PyPI Package latest
release](https://img.shields.io/pypi/v/commitizen.svg?style=flat-square)](https://pypi.org/project/commitizen/)
[![Supported
versions](https://img.shields.io/pypi/pyversions/commitizen.svg?style=flat-square)](https://pypi.org/project/commitizen/)
[![Codecov](https://img.shields.io/codecov/c/github/commitizen-tools/commitizen.svg?style=flat-square)](https://codecov.io/gh/commitizen-tools/commitizen)

![Using commitizen cli](images/demo.gif)

## About

Commitizen is a tool designed for teams.

Its main purpose is to define a standard way of committing rules
and communicating it (using the cli provided by commitizen).

The reasoning behind it is that it is easier to read, and enforces writing
descriptive commits.

Besides that, having a convention on your commits makes it possible to
parse them and use them for something else, like generating automatically
the version or a changelog.

### Commitizen features

- Command-line utility to create commits with your rules. Defaults: [Conventional commits][conventional_commits]
- Display information about your commit rules (commands: schema, example, info)
- Bump version automatically using [semantic verisoning][semver] based on the commits. [Read More](./bump.md)
- Generate a changelog using [Keep a changelog][keepchangelog] (Planned feature)

## Requirements

Python 3.6+

[Git][gitscm] `1.8.5.2`+

## Installation

Global installation

```bash
sudo pip3 install -U Commitizen
```

### Python project

You can add it to your local project using one of these:

```bash
pip install -U commitizen
```

```bash
poetry add commitizen --dev
```

## Usage

### Commiting

Run in your terminal

```bash
cz commit
```

or the shortcut

```bash
cz c
```

### Help

```bash
$ cz --help
usage: cz [-h] [--debug] [-n NAME] [--version]
        {ls,commit,c,example,info,schema,bump} ...

Commitizen is a cli tool to generate conventional commits.
For more information about the topic go to https://conventionalcommits.org/

optional arguments:
-h, --help            show this help message and exit
--debug               use debug mode
-n NAME, --name NAME  use the given commitizen
--version             get the version of the installed commitizen

commands:
{ls,commit,c,example,info,schema,bump}
    ls                  show available commitizens
    commit (c)          create new commit
    example             show commit example
    info                show information about the cz
    schema              show commit schema
    bump                bump semantic version based on the git log
    version             get the version of the installed commitizen or the
                        current project (default: installed commitizen)
    check               validates that a commit message matches the commitizen schema
    init                init commitizen configuration
```

## FAQ

### Why are `revert` and `chore` valid types in the check pattern of cz conventional_commits but not types we can select?

`revert` and `chore` are added to the "pattern" in `cz check` in order to prevent backward errors, but officially they are not part of conventional commits, we are using the latest [types from Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#type) (they used to but were removed). Using `chore` or `revert` would be part of a different custom rule.

However, you can always create a customized `cz` with those extra types (See [Customization](https://commitizen-tools.github.io/commitizen/customization/).

See more discussion in issue [#142](https://github.com/commitizen-tools/commitizen/issues/142) and [#36](https://github.com/commitizen-tools/commitizen/issues/36)

### How to handle revert commits?

```sh
git revert --no-commit <SHA>
git commit -m "revert: foo bar"
```

## Contributing

Feel free to create a PR.

1. Clone the repo.
2. Add your modifications
3. Create a virtualenv
4. Run `./scripts/test`

[conventional_commits]: https://www.conventionalcommits.org
[semver]: https://semver.org/
[keepchangelog]: https://keepachangelog.com/
[gitscm]: https://git-scm.com/downloads