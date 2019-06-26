# Week 2

Directory with the outputs: `/nfs_scratch/skkwan/`.
Important directories:
`PUAnalysis/Condor/submit_FastMTT.sh`

## Friday (06/21/19)

### Learning how to make control plots
See the corresponding Procedures file. Example: [http://www.hep.wisc.edu/~skkwan/test/] using `/hdfs/store/user/shigginb/2018_tt_pm_weighted_corr_svfit/` (turned off systematics because that's overkill for a demo).

### To-do

- Run FastMTT on 2018 data and MC files here:

  '''/hdfs/store/user/shigginb/2019_June_15_2018_tt/''' [Done]

  '''/hdfs/store/user/shigginb/2019_June_15_2018_Data_tt/'''
- 2016 data and MC are not ready yet, but as a heads up because the FastMTT submit script must be edited to reflect a different naming scheme:

  '''/hdfs/store/user/shigginb/2019_June_18_2016_tt''' [Submitted]

  '''/hdfs/store/user/shigginb/2019_June_18_2016_Data_tt/'''


## Tuesday (06/25/19)

- FastMTT on 2018 MonteCarlo submitted - need validation plots.
- Made `submit_FastMTT_2016MC.sh`.
- FastMTT on 2016 MonteCarlo submitted.

## Wednesday (06/26/19)

### To-do
- Trace through `https://github.com/samhiggie/PUAnalysis/blob/htt_2018_sam/StatTools/interface/DataCardCreatorHThTh_2016_QCD_FF.h` and understand how the histograms are filled.