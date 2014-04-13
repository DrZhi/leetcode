# set file to the name of the main file without the .tex
target	= leetcode-cpp
gabbage	= *~ $(target).{out,log,aux,lot,toc,bbl,blg,xdv,log,idx} *.aux
files	= $(shell ls *.*)
tmp     = $(target).test

VIEWER	= Skim
TEX 	= xelatex
BIBTEX  = bibtex
DVI		= xdvipdfmx

#===============================================

default: pdf

all: tarball show

pdf:	
	$(TEX) -no-pdf $(target)
	#$(BIBTEX) $(target)
	$(TEX) $(target)
	$(TEX) $(target)
	make clean
	
$(target).tar.gz : $(files)
	tar -czvf $(target).tar.gz $(files)

tarball: $(target).tar.gz

show: pdf
	$(VIEWER) $(target).pdf &

clean:
	rm -f $(gabbage)

test:
	cp $(target).tex $(tmp).tex
	#sed 's|^\(.*usepackage.*\)|\1\n\\usepackage{syntonly}\n\\syntaxonly|' \
	#			$(target).tex > $(tmp).tex
	$(TEX) -no-pdf $(tmp).tex || echo " :: TeX compile failed!!" ;
	@echo " :: Syntax test finish."
	-@rm -f $(tmp).*


