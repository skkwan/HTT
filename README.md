# Higgs to TauTau

## Only do once:
1. Follow Sam's [checkout instructions](https://github.com/samhiggie/PUAnalysis/blob/1b1a642064e113742fe84c22e672e6f3234ca4f0/README.md) to get the CMSSW installation and repository. So my working directory is `/afs/hep.wisc.edu/home/skkwan/public/CMSSW_10_2_14/src/PUAnalysis`.



## Locally running FastMTT
The FastMTT wrapper adds a branch to the n-tuple that has an estimate of the di-tau mass for each event.
1. At the terminal line: `cmsenv`.
1. Get grid certificate: ```voms-proxy-init --rfc --voms cms```
1. At the terminal line, generate an n-tuple (you can `Ctrl+C` at any point to make a smaller, incomplete test file).

    ```cmsRun TT-MC-Sync.py```
  
1. At the terminal line, call the FastMTT executable with the command-line arguments. The exact executable depends on the type of data file.

    ```FastMTTStandAlonePUATauDM newFile="fastone.root" inputFile="analysis_TauTau.root" newOutputFile=1.0```
  (`newOutPutFile` is set to 1.0 to indicate that you want an output file.)
1. Examine the outputs
 - At terminal: ```root -l fastone.root```
 
 - In ROOT: ```.ls```
 
 - Change into diTauEventTree directory:
    ```diTauEventTree->cd()```
 - Check the name of the tree:
    ```.ls```
 - Print the branches:
    ```eventTree->Print()```
 - Check to see if the svFit di-tau masses are reasonable:
    ```eventTree->Scan("m_sv")```
    
