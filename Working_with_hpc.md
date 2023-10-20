---
title: "Working with the hpc clusters"
author: "Amnah Siddiqa"
date: "2023-10-19"
---




## High Performance Computing Cluster (HPCC)

CCHMC [HPCC](https://bmi.cchmc.org/resources/clusters/computational-cluster) employs LSF resource manager and scheduler. 

#### Some useful references:

- [CCHMC HPCC talk @ sharepoint ](to allow some flexibility in interactive sessions for development and testing.)

- Bioinformatics and R Users Group (BUG and RUG). You can reach `bug-announce@mailman.cchmc.org` to get invitation for the mailing list. 

- [Introduction to HPC from the HPC Carpentry](https://hpc-carpentry.github.io/hpc-intro/)  

- [Pawsey Center SC workshop](https://pawseysc.github.io/sc19-containers/)


## Get VPN setup 

- Call IT @ 64100 depart to get yourself `anyconnect` downloaded and setup.

## Getting acquainted with your HPCC environment

If you are connected to VPN, log into HPCC from your terminal using:


```bash
$ ssh username@bmiclusterp.chmcres.cchmc.org
#example
$ ssh sid1df@bmiclusterp.chmcres.cchmc.org
```

Otherwise 

```bash
$ ssh username@research.cchmc.org
#example
$ ssh sid1df@research.cchmc.org

```

Lab work space from root is @ `./data/HaganLab` and scratch is @ `./scratch/yourusername`


```bash
# From your home it should be located as follows
[sid1df@bmiclusterp2 ~]$ cd ~
[sid1df@bmiclusterp2 ~]$ ls 
Desktop
[sid1df@bmiclusterp2 ~]$ cd ../../../data/HaganLab
[sid1df@bmiclusterp2 HaganLab]$ cd ../../../scratch/sid1df
[sid1df@bmiclusterp2 sid1df]$ 
```

Check available modules and load them as per your requirement using:


```bash
#Checking available modules
[sid1df@bmiclusterp2 /]$ module avail
#Loading appropriate modules
[sid1df@bmiclusterp2 /]$ module load nextflow
[sid1df@bmiclusterp2 /]$ module load singularity/3.7.0

```

### Handling  batch jobs on HPCC

Two ways to work with the HPCC: through interactive sessions and batch job submission. Use scratch space for computing and submit batch jobs as follows: 



```bash
#submit
$ bsub <runscript.sh (make sure to include < followed immediately by filename)
#check the status of current jobs 
$ bjobs
# kill specific job 
$ bkill jobid 
# kill all jobs 
$ bkill 0 

```

### Reference genome/file locations (not all there, may need to download)

Supporting databases and some related files that we use are under `/HaganLab/databases/`

### Transferring files to and from  HPC 

- Trailing slash on sending side transfers only contents of the directory, without slash it transfers directory itself and contents: `rsync -rvtP local/files/location/ yourusername@bmiclusterp.chmcres.cchmc.org:/scratch/yourusername/HPC/location`


```bash

# Usage: Run these command from your local terminal.
# Example: Copying files from the cluster to your local machine
$ rsync -rvtP  sid1df@bmiclusterp.chmcres.cchmc.org:/data/HaganLab/irene_dc/samplesheet.csv /Users/amnahsiddiqa/Documents/CCHMC_Projects/Kiana_Pasare/

# Command for copying a file from your local machine to the remote server:
$ rsync -rvtP  /Users/amnahsiddiqa/Documents/CCHMC_Projects/Kiana_Pasare/nfcore_RNAseq_prj0002.sh sid1df@bmiclusterp.chmcres.cchmc.org:/scratch/sid1df

```

- Filezilla Instructions: use ` bmiclusterp2.chmcres.cchmc.org` as target and `22` as port together with your CCHMC credentials (your username, password)


### Working interactively on the cluster

- in progress

### From your local terminal/RStudio

**These R packages may also be useful for connecting to a remote server from your local environment:**

- [SSH](https://cran.r-project.org/web/packages/ssh/)  
- [remoter](https://cran.r-project.org/web/packages/remoter/)  
- [rmote](https://github.com/cloudyr/rmote)  
- [ssh-utils](https://cran.r-project.org/web/packages/ssh.utils/index.html)  


## Remote RStudio
You can run Rstudio on the HPCC and access it from a local browser, as explained (In progress).
