EXEC = pop
ifeq ($(SAFE),TRUE)
	DIST = ../src/
else
	DIST = ../src/
endif
ARGS = -nox -iprint 150 

ifdef ComSpec
    RM=del /F /Q
else
    RM=rm -rf
endif

all: mpd

$(EXEC): $(DIST)$(EXEC).tpl
	ln -sf $(DIST)$(EXEC) $@
	ln -sf $(DIST)$(EXEC).tpl $@.tpl


mpd: $(EXEC)
	$(MAKE) --directory=../src
	./$(EXEC) $(ARGS)
	@$(RM) $(EXEC).*[0123456789] *.rpt *.log variance gradient.* *tmp admodel.* *.eva

mcmc: $(EXEC)
	./$(EXEC) $(ARGS) -mcmc 3000000 -mcsave 600 -hbf 1
	./$(EXEC) -mceval 
	

debug: $(EXEC)
	./$(EXEC) $(ARGS)

plot:
	R CMD BATCH plot.R

clean:
	@$(RM) $(EXEC)
	@$(RM) $(EXEC)  $(EXEC).[brces]* $(EXEC).*[0123456789] *.rpt *.log variance gradient.* *tmp
	@$(RM) admodel.*
	@$(RM) checkfile.rep
	@$(RM) mcout.rep
	@$(RM) plot.Rout
	@$(RM) Rplots.pdf
	@$(RM) *.rep
	@$(RM) Fprof.yld
	@$(RM) *.prj
	@$(RM) pop.par
	@$(RM) SIS_out.rep
	@$(RM) mceval.dat


