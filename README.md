# Release-notes-from-changelog

Release-notes-from-changelog is a GitHub action for extracting release notes from a changelog formatted according to https://keepachangelog.com/en/1.0.0/.

By default, the release message starts with the first-level heading and first paragraph of the file `README.md`.
If you want to customize this, you need a file in your repository called `RELEASE_HEAD.md` that contains any header text that you want to add to all your releases.
This can be, for example, a short sentence explaining the general purpose of the project, or simply a note that the following text was extracted from a changelog.

The version number so search for is given using the `version` parameter and stored in the variable `RELEASE_VERSION`.
If you use tags of the form `X.Y.Z` or `vX.Y.Z` to trigger your releases, you don't need to set that parameter, since the action will just use the tag name instead.
To be specific, this will work as long as you use the same string for the headings in `CHANGELOG.md` as you use for git tags, with the only exception that a leading `v` will be stripped from the tag if it is there.

The action can be used as follows:

```yaml
jobs:
  build:
    name: "My fancy build"
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: CSchoel/release-notes-from-changelog@v1
      - name: Create Release using GitHub CLI
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: >
          gh release create
          -d
          -F RELEASE.md
          -t "Version $RELEASE_VERSION"
          ${GITHUB_REF#refs/*/}
```

## Input variables

```yaml
- uses: CSchoel/release-notes-from-changelog@v1
  with:
    version: version string to search in the changelog (default to tag without leading v)
    begin-pattern: begin pattern used in sed command (default '/^## \\[${RELEASE_VERSION}\\]/')
    end-pattern: end pattern used in sed command (default '/^## /')
    link-pattern: pattern used in grep command to find footnote-style link for version (default '^\\[${RELEASE_VERSION}\\]:')
    chop: number of lines to cut from end of matched region
    working-directory: path where RELEASE_HEAD.md and CHANGELOG.md are found and where RELEASE.md is placed
```

## Known issues

The default settings do not work for the very first version in the changelog, as we use `^## ` as the end pattern, which will not be found by sed.
To circumvent this, you can do one of the following:

* Add a dummy level 2 heading at the end of your changelog for the first release. Starting from the second release, you can safely remove it.
* Set the `end-pattern` to `$` and `chop` to `0`. You *have* to change this for future versions, of course. An example for this can be seen in the [test workflow](.github/workflows/test.yml) for this project.
* Make the first entry in the changelog a pre-release that will not actually be release, but still look sensible in the changelog.