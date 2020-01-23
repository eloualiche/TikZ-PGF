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

options.source = \
	./src/options_forward.tex ./src/tikz_forward.tex

entry.source = \
	./src/entry_hopenhayn.tex ./src/tikz_hopenhayn.tex	

investments.source = \
	./src/investment_portfolio.tex ./src/tikz_portfolio.tex \
	./src/investment_frontier.tex  ./src/tikz_frontier.tex  \
	./src/investment_MVEP.tex      ./src/tikz_MVEP.tex  \
	./src/investment_SML.tex       ./src/tikz_SML.tex  \
	./src/investment_CML_SML.tex   ./src/tikz_CML_SML.tex  \
	./src/investment_CML1.tex      ./src/tikz_CML1.tex  \

international.source = \
	./src/cip_contract.tex
# --------------------------------------------------------------------------------------------------------


# --------------------------------------------------------------------------------------------------------
## ALL TARGET
all: bubbles entry options investments international
# --------------------------------------------------------------------------------------------------------



## --------------------------------------------------------------------------------------------------------
## 
bubbles: $(bubbles.source)
	$(call colorecho,"Compiling Bubbles Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	pdflatex -interaction=batchmode -output-directory output src/bubbles.tex
	convert -density 600x600 output/bubbles.pdf -quality 90 -resize 800x600 output/bubbles.png
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo

entry: $(entry.source)
	$(call colorecho,"Compiling Extensive Margin Pictures ...")
# 	pdflatex -interaction=batchmode -output-directory output src/entry_hopenhayn.tex
# 	pdflatex -interaction=batchmode -output-directory output src/entry_hopenhayn.tex
# 	pdflatex -interaction=batchmode -output-directory output src/entry_hopenhayn_bw.tex
# 	pdflatex -interaction=batchmode -output-directory output src/entry_hopenhayn_bw.tex
# 	pdf2svg output/entry_hopenhayn.pdf output/entry_hopenhayn.svg
# 	pdflatex -interaction=batchmode -output-directory output src/entry_salop.tex
# 	pdflatex -interaction=batchmode -output-directory output src/entry_salop.tex
# 	pdf2svg output/entry_salop.pdf output/entry_salop.svg
	pdflatex -interaction=batchmode -output-directory output src/entry_elasticity.tex
	pdflatex -interaction=batchmode -output-directory output src/entry_elasticity.tex
	pdf2svg output/entry_elasticity.pdf output/entry_elasticity.svg
	$(TIME-END)
	@echo


options: $(options.source)
	$(call colorecho,"Compiling Options Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/options_forward.tex
	pdflatex -interaction=batchmode -output-directory output src/options_forward.tex
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo

investments: $(investments.source)
	$(call colorecho,"Compiling Investments Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/investment_portfolio.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_portfolio.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_frontier.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_frontier.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_MVEP.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_MVEP.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_SML.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_SML.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_CML_SML.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_CML_SML.tex
	pdflatex -interaction=batchmode -output-directory output src/investment_CML1.tex
	rm -f output/*.aux output/*.log output/*.out
	$(TIME-END)
	@echo

international: $(international.source)
	$(call colorecho,"Compiling International Pictures ...")
	pdflatex -interaction=batchmode -output-directory output src/cip_contract.tex
	pdf2svg output/cip_contract.pdf output/cip_contract.svg
	$(TIME-END)
	@echo

current: 
	$(call colorecho,"Compiling Current Picture ...")
	pdflatex -interaction=batchmode -output-directory output src/investment_CAL.tex
	$(TIME-END)
	@echo


# --------------------------------------------------------------------------------------------------------
## Generate graph for this task
graph:
	$(call colorecho,"Building dependency graph...")
	make -Bnd | make2graph | dot -Tpng -o ./log/graph-TikZ-dag.png
	make -Bnd | make2graph | dot -Tsvg -o ./docs/graph/graph-TikZ-dag.svg
