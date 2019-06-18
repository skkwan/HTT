# Week 1

## Tuesday (06/18/19)

### Running FastMTT interactively

*Goal:* Check to see how long it takes to run fastMtt interactively using Nohup.

  SubmitSVfit script used to take 2 seconds per event -- fastMTT is ~10x-100x faster, so it would be worthwhile to see how many days it takes to run the larger n-tuples interactively.

1. Created n-tuple with `cmsRun TT-MC-Sync.py`.
1. [to-do] Called FastMTT standalone executable; letting it run all the way through. 

### Preparing scripts for Condor submission

If I'm interpreting Sam's corrections right:

1. In `PUAnalysis/Condor/fastmttSubmitter.py`, changed l.100: `inputfile` to `inputFile`.
1. 
