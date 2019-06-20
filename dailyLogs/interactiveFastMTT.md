# Week 1

## Tuesday (06/18/19)

### Running FastMTT interactively

*Goal:* Check to see how long it takes to run fastMtt interactively using Nohup.

  SubmitSVfit script used to take 2 seconds per event -- fastMTT is ~10x-100x faster, so it would be worthwhile to see how many days it takes to run the larger n-tuples interactively.

1. Created n-tuple with `cmsRun TT-MC-Sync.py`. Output: `analysis_TauTau.root`. (736 events)
1. Called FastMTT standalone executable; ran in a few minutes: produced `fastone.root`.

### Preparing scripts for Condor submission

Debugging (thanks Sam):

1. In `PUAnalysis/Condor/fastmttSubmitter.py`, changed l.100: `inputfile` to `inputFile`.
1. Changed line 81 to: `output_dir = '/store/user/%s/%s/%s/'\
        % (pwd.getpwuid(os.getuid())[0], jobName, sample_name)`.


Submitting jobs to Condor:
1. In `PUAnalysis/Condor/submit_FastMTT.sh`, appended descriptive phrases to each job-name.
1. In `PUAnalysis/Condor/submit_FastMTT.sh`, copy-pasted one Python command, replaced `-s` with `-dr` to do a dryrun, and replaced `${jobname}` with some phrase. Must remove the directory `/nfs_scratch/skkwan/[that phrase]` afterwards.
1. Dryrun produces a long `farmOutAnalysisJobs` command: tried running that command:
   Need to remove trailing `/` from the sample path, like so:

   '''python fastmttSubmitter.py -s -sd /hdfs/store/user/shigginb/2018_MC_tt/W1JetsToLNu_Tu\
neCP5_13TeV-madgraphMLM-pythia8/*/*/* --jobName FastMTT2018_W1Jets -es -iswj'''
1. In `PUAnalysis/Condor/fastmttSubmitter.py`, added `--max-usercode-size=350` in-between `--fwklite` and `--input-file-list` as prompted by the error message.
1. Success! Submitted jobs for one MC dataset.

   '''You can monitor your workflow's progess by watching /nfs_scratch/skkwan/FastMTT2018_W1Jets/0000/dags/dag.dagman.out
A summary of the status of all of the jobs in your workflow will be
written to the following file every 60 seconds:
  /nfs_scratch/skkwan/FastMTT2018_W1Jets/0000/dags/dag.status

Your jobs should show up in ~6 minutes
at the NEW job monitoring web page :
    http://www.hep.wisc.edu/cms/comp/jobs/
Jobs for FastMTT2018_W1Jets are created in /nfs_scratch/skkwan/FastMTT2018_W1Jets/0000/submit'''

  Submitted at 06/18/19 10:10:15, exited with status 0 (i.e. successful) at 06/18/19 11:00:41.

## Wednesday (06/19/19)

### CMS Induction Course
Introduction to CMS organization, how the CMS experiment is organized, major components of the detector (incl. focus talks on tracking and calorimetry), Visit to Point 5 and the detector cavern, and reception.

### Using bash script to submit FastMTT samples.

1. In `PUAnalysis/Condor/submit_FastMTT.sh`, removed trailing `/` from sample directories as per yesterday's test run.
1. At terminal, `chmod +x submit_FastMTT.sh` to make it an executable.
1. At terminal, `./submit_FastMTT.sh`.
1. 