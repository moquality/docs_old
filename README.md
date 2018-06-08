Docs
=====

## Installation

Create the docs environment with
```
conda env create -f environment.yml
```

Activate the environment with
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

To publish to GitHub,
```
make publish
```
or
```
mkdocs build
mkdocs gh-deploy
```
