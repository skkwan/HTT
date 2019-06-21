# Making Control Plots and Data Cards

## Control Plots

Control plots show comparisons of variable distributions in data vs. Monte Carlo , for different categorization regions. They are often used in data analysis notes to show variable distributions, but less commonly in final analyses because they do not use systematics.

To plot something like the di-tau mass spectrum:
1. Go to `PUAnalysis/ROOT/plotMacros/makeControlPlots_tt.C`.
1. Each `makeDiTauStack` command plots one variable. e.g. for the di-tau mass spectrum VBF, it is `tt_vbf`.
1. `/afs/hep.wisc.edu/home/skkwan/public_html/test/diTau_m_sv.png has been created`. Plots will also appear at the URL `http://www.hep.wisc.edu/~skkwan/`.

n.b.: The way the control plot script is set up is that it accesses all N files for each variable, instead of opening a file and making a vector of variables to fill X histograms with (if you wanted to plot X variables using N files). But it would take a long time to restructure the ploting script.

## Data Cards
Data cards consist of histograms with the yield and systematics for different cuts.

Working directory:
'''CMSSW_10_2_14/src/PUAnalysis/StatTools/bin'''

For example, `MakeDataCardHThTh_2016.cc`
- includes the header file `PUAnalysis/StatTools/interface/DataCardCreatorHThTh_2016.h`
- creates a `DataCardCreatorHThTh_2016` object called `creator` with the argument `parser` at line 107.
- uses a preselection `inclSel`
- calls `creator.runOSLSMT` and `creator.makeHiggsShape` methods.
- If we go to the abovementioned header file, we see a 1300-line header file wihch declares the struct `BkgOutput` and the class `DataCardCreatorHTT`.

`makeTauTauPlots_Published` makes ROOT files into data cards:

