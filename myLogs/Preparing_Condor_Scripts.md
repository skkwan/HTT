# Preparing Condor Scripts

Directory:
'''/afs/hep.wisc.edu/home/skkwan/public/CMSSW_10_2_14/src/PUAnalysis/Condor'''

## submit_FastMTT.sh
- This calls `fastmttSubmitter.py` on each dataset corresponding to a physics model in Monte Carlo.
- To submit jobs on 2018 pre-merged n-tuples, make sure it runs locally first by running
one line at the command line.
- Change `$jobname` environmental variable to something more descriptive like `${jobname}_W1Jets` for `W1JetsToLNu_TuneCP5_13TeV-madgraphMLM-pythia8`.

### fastmttSubmitter.py
- This creates a bash script that has multiple calls to `farmoutAnalysisJobs --fwklite` to submit jobs to execute the SVFit standalone.
-- At line 100, it specifies which executable to use, along with its command-line arguments, e.g. ''' '$CMSSW_BASE/bin/$SCRAM_ARCH/FastMTTStandAlonePUATauDM inputfile=$value newOutputFile=1.0 newFile=\'$OUTPUT\'' '''
-- It uses shell environmental variables; be careful of instances where the output has the same name as the input save a new branch, for example, because that will cause the environmental variables to be set/used incorrectly.

- There is a parser; inspect the list of arguments, such as `-dr` (short for `-dryrun`) which simply prints out the command (called `farmoutString` here) string to the command line (extremely useful for testing).




