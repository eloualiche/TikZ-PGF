#
## Makefile for TIKZ PDFs
## 
#
#
## Created       August 09th  2019
## Last modified August 09th  2019
#
#
## ----------------------------------------------------


# --------------------------------------------------------------------------------------------------------
# For non recursive make
-include ./rules.mk
# --------------------------------------------------------------------------------------------------------


# --------------------------------------------------------------------------------------------------------
bubbles.source = \
	./src/bubbles.tex ./src/tikz_bubbles.tex ./src/tikzpeople.sty 
# --------------------------------------------------------------------------------------------------------


# --------------------------------------------------------------------------------------------------------
## ALL TARGET
all: bubbles
# --------------------------------------------------------------------------------------------------------



## --------------------------------------------------------------------------------------------------------
## 
bubbles: $(bubbles.source)
	$(call colorecho,"Compiling Bubble Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	convert -density 600x600 output/bubbles.pdf -quality 90 -resize 800x600 output/bubbles.png
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo



# --------------------------------------------------------------------------------------------------------
## Generate graph for this task
graph:
	$(call colorecho,"Building dependency graph...")
	make -Bnd | make2graph | dot -Tpng -o ./log/graph-TikZ-dag.png
	make -Bnd | make2graph | dot -Tsvg -o ./log/graph-TikZ-dag.svg
