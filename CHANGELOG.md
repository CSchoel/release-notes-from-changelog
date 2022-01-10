# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

### Added

nothing

### Changed

nothing

### Fixed

nothing

## [1.2.0] - 2022-01-10

### Added

* Test case for missing URL for footnote-style markdown link in CHANGELOG.md

### Changed

* Split main script into multiple steps and added more output for better debugging.
* Final `grep` step is now only run if the link pattern can actually be found in the changelog.
    If not, a warning is printed.
* Switches to `uses: ./` to use local version of action in all CI/CD scripts.
    This avoids the need to specify the action version within the CI/CD scripts and ensures that the current version is used.
* Uses [GitHub CLI](https://cli.github.com/manual/gh_release_create) instead of [unmaintained `actions/create-release`](https://github.com/actions/create-release) both in README example and release script.

## [1.1.0] - 2022-01-04

### Added

* input variable `working-directory` to work with repositories checked out in a subfolder

### Changed

* CI tests are now also run on the branch `dev` in addition to `main`

### Fixed

* Makes YAML files fully conform to GitHub Action schema

## [1.0.0] - 2021-05-25

### Changed

* adds shorthand tag v1 for use in GitHub action workflows
* otherwise same as 0.2.1

## [0.2.1]

### Added

* parameter `link-pattern` that allows to extract footnote-style link for version from changelog

### Changed

* changelog now also contains links that allow to compare versions on github

## [0.2.0]

### Changed

* renames `start-pattern` to `begin-pattern` for better naming consistency (begin/end instead of start/end)
* adds surrounding slashes to `begin-pattern` and `end-pattern`, so that other sed patterns like `$` can be used

## [0.1.9]

### Added

* input variable `chop` to control how many lines are removed from the end of the matching part of `CHANGELOG.md`

### Changed

* the variables `startPattern` and `endPattern` are now called `start-pattern` and `end-pattern` instead

## [0.1.8]

### Fixed

* turns out that inputs are not actually saved as `$INPUT_VARNAME` for composite actions => use `${{ input.varname }}` instead

## [0.1.7]

### Fixed

* accidentally switched cases in if 🤦

## [0.1.6]

### Added

* GitHub actions test script for testing different scenarios
* echo of sed pattern for debugging

## [0.1.5]

### Fixed

- bash if syntax was wrong (need `=` instead of `==` and quotes around variable)
- adds missing checkout action to test script

## [0.1.4]

### Fixed

- uses folded block (`<`) instead of literal block (`|`) for bash if

## [0.1.3]

### Fixed

- adds `inputs.` prefix to access input variables

## [0.1.2]

### Changed

- uses $INPUT_VERSION instead of $version
- renames start and end pattern to not use dash

## [0.1.1]

### Fixed

- since `if:` is not supported in composite actions, we now use the bash for the if statement
- added missing parameters to action.yml (`shell:`)

## [0.1.0]

### Added

* first version of `action.yml`
* changelog, readme and `RELEASE_HEAD.md`


[Unreleased]: https://github.com/CSchoel/release-notes-from-changelog/compare/v1.1.0..HEAD
[1.1.0]: https://github.com/CSchoel/release-notes-from-changelog/compare/v1.0.0..v1.1.0
[1.0.0]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.2.1..v1.0.0
[0.2.1]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.2.0..v0.2.1
[0.2.0]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.9..v0.2.0
[0.1.9]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.8..v0.1.9
[0.1.8]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.7..v0.1.8
[0.1.7]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.6..v0.1.7
[0.1.6]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.5..v0.1.6
[0.1.5]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.4..v0.1.5
[0.1.4]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.3..v0.1.4
[0.1.3]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.2..v0.1.3
[0.1.2]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.1..v0.1.2
[0.1.1]: https://github.com/CSchoel/release-notes-from-changelog/compare/v0.1.0..v0.1.1
[0.1.0]: https://github.com/CSchoel/release-notes-from-changelog/releases/tag/v0.1.0