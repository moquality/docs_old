all: serve

build:
	mkdocs build

serve:
	mkdocs serve

publish:
	git branch -D gh-pages
	git push origin
	mkdocs gh-deploy
	git checkout gh-pages
	@echo docs.moquality.com >> CNAME
	git add CNAME
	git commit -a -m "Adds CNAME"
	git push origin gh-pages
	git checkout master
