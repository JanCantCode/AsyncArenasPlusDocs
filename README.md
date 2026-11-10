# AsyncArenasPlus documentation

Public site: https://jancantcode.github.io/AsyncArenasPlusDocs/

The editable MkDocs source is in `_source/`. The HTML at the repository root
is the generated GitHub Pages site. Edit the Markdown and configuration in
`_source/`, then rebuild; do not edit the generated HTML directly.

## Preview locally

```powershell
python -m pip install -r _source/requirements.txt
python -m mkdocs serve --config-file _source/mkdocs.yml
```

## Rebuild for GitHub Pages

Run from the repository root:

```powershell
python -m mkdocs build --strict --config-file _source/mkdocs.yml --site-dir ../work/docs-build
Get-ChildItem -LiteralPath 'work/docs-build' -Force | ForEach-Object {
    Copy-Item -LiteralPath $_.FullName -Destination '.' -Recurse -Force
}
git diff --check
```

The staging directory is inside this repository's ignored `work/` folder.
Copying the build preserves the Google verification file and repository metadata.
Review and commit both the source and generated changes before pushing `master`.

The unchanged operational guides were recovered from the plugin repository's
`86d249b` source revision and checked against the published HTML. This source
does not include unfinished changes from newer plugin development branches.
