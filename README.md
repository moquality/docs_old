Docs
=====

## Installation

Create the docs enviornment with
```
conda env create -f environment.yml
```

Activate the enviornment with
```
source activate docs
```

## Editing and Publishing Docs

Find the folder with Makefile.

To serve docs locally,
```
make serve
```
or 
```
mkdocs serve
```

To publish to github,
```
make publish
```
or
```
mkdocs build
mkdocs gh-deploy
```