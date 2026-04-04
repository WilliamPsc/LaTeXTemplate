ROOTDIR = .
SRC = $(wildcard *.tex)
TARGETS = $(subst .tex,.pdf,$(SRC))
CLEAN_SUFFIXES = .aux .bbl .blg .log .nav .out .snm .toc .bcf .run.xml .vrb .fdb_latexmk .fls .synctex.gz
CLEAN_FILES = $(foreach s,$(CLEAN_SUFFIXES),$(subst .tex,$(s),$(SRC)))

PDFLATEX = pdflatex

all: $(TARGETS)

%.pdf: %.tex
	$(PDFLATEX) $< -o $@
	biber $(basename $<)
	$(PDFLATEX) $< -o $@
	$(PDFLATEX) $< -o $@

.PHONY: clean scratch force

force: scratch
	make

clean: 
	rm -f $(CLEAN_FILES)

scratch: clean
	rm -f $(TARGETS)