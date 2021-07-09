# IFOSS Law Book

This repository contains the source files (in Markdown format) of the second edition of the IFOSS Law Book.

Any pull request will be authorized only by the copyright holders of the individual contributions.

> **NOTE**: **_if you see this note you are working on the `master` branch_** please always work on the `bugfix` branch and make a pull request from there, so that the original version is untouched until we merge all the changes. On your local filesystem, you can do
>
>        git -b bugfix
>        git branch --set-upstream-to=origin/bugfix bugfix
>
> and work from there

The `bugfix` branch is intended as the working and testing branch.

The `master` branch is intended as the stable up-to-date branch, from which the book is being generated.


## Files

This are the working parts:

- `src/` contains the current sources in MarkDown
- `IFOSSLB.pdf` is the PDF of the whole book
- `README.markdown` is this file


## Naming convention

The individual source files are named according to the following convention:

```
10-Intro.markdown
20-History.markdown
50-Belgium.markdown
50-China.markdown
50-...

```

The position of the chapters Intro, History and is predetermined and the country chapters can simply be added as `50-$country_name.markdown` and they will be generated in the right order without the need to manually keep track of the order in a separate file. This also leaves space to introduce new groups of chapters before or after, as well.


## Generating the PDF with Pandoc

Generating a full-book PDF now works by running (requires Pandoc 2.0 or later):

```
pandoc --top-level-division=chapter --number-sections --latex-engine=xelatex -s -f markdown_strict+footnotes+auto_identifiers+implicit_header_references+header_attributes+yaml_metadata_block metadata.yaml src/*markdown -o IFOSSLB.pdf
```

Useful explanations:

- `--top-level-division=chapter` treats the top level headings as separate chapters and makes them start on a new page.
- `--number-sections` adds number to the sections so it is possible to determine the level of each heading


## Generating the ePub with Pandoc

Generating a full-book ePub now works by running (requires Pandoc 2.0 or later):

```
pandoc --top-level-division=chapter --number-sections -s -f markdown_strict+footnotes+auto_identifiers+implicit_header_references+header_attributes+yaml_metadata_block metadata.yaml --epub-cover-image='cover.png' src/*markdown -o IFOSSLB.epub
```

