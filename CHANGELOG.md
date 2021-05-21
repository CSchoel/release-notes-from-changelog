# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

### Added

[nothing]

### Changed

[nothing]

### Fixed

[nothing]

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