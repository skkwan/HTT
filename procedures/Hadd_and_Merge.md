# Hadd and Merging files

## Applying weights


Taking a look at `weight80x.sh` and deducing what it does:
- Command line options:

    -   `weightH`: if set to 1, runs `EventWeightsIterativeGen`, outputting one file for each Higgs production mechanism (ggH, VBF, WpH, WmH, ZH, and ttH) for Higgs mass 120, 125, and 130 GeV, calling the summed histogram `sumweights/genWeights`. Each process has its own weight. (I should look at what `EventWeightsIterativeGen` is)

    -   `weightZ`: if set to 1, runs `EventWeightsIterativeZJets` with `weight = 1` and histogram name `TT/results`. Calls `hadd` utility on all `Z` samples with 1 to 4 jets.

    -   `weightW`: if set to 1, runs `EventWeightsIterativeWJets` with `weight = 1` and histogram name `TT/results`. Calls `hadd` utility on all `W` samples with 1 to 4 jets.

    -   `weight`:  if set to 1, runs `EventWeightsIterativeGen` on all processes to be weighted (all with different weights of course), caling the summed histogram `sumweights/genWeights`. Then uses `hadd` utility like so:

    ```hadd -f DiBoson.root WWTo*root WZTo*root ZZTo*.root St_*.root t*tW.root VVTo*root WWW.root ZZZ.root```

    *Need to clarify: are these different initial states?*