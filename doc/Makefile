# Plush doc Makefile
# $Id: $
# to build api documentation you need python docutils and epydoc
#
.PHONY: all epydoc clean distrib

TARGET := bertha:~/public_public_html/plush
HTML_DOCS := README.html CHANGES.html
CSS_FILE := plush.css
RST2HTML := rst2html.py -t --stylesheet-path=$(CSS_FILE) --embed-stylesheet

all: doc epydoc

doc: ${HTML_DOCS}

%.html: ../%.txt  $(CSS_FILE)
	${RST2HTML} $< $@

epydoc:
	epydoc --name Plush -u ../../ --html --output ./api/  ../plush/

distrib: doc
	scp -r ${HTML_DOCS} api $(TARGET)/


clean:
	-rm -rf ./api/* $(HTML_DOCS)
	-@find . "(" -name "*~" -or  -name ".#*" -or  -name "#*#" -or -name "*.pyc" ")" -print0 | xargs -0 rm -f
