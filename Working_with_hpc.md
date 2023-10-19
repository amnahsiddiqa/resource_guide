---
title: "Working with the hpc clusters"
author: "Amnah Siddiqa"
date: "2023-10-19"
---




## High Performance Computing Cluster (HPCC)
Two ways to work with the HPCC: interactive sessions and job submission. 
#### Other useful references:

- [CCHMC HPCC talk @ sharepoint ](to allow some flexibility in interactive sessions for development and testing.)

- Bioinformatics and R Users Group (BUG and RUG). You can reach `bug-announce@mailman.cchmc.org` to get invited for the mailing list. 


- [Introduction to HPC from the HPC Carpentry](https://hpc-carpentry.github.io/hpc-intro/)  

- [Pawsey Center SC workshop](https://pawseysc.github.io/sc19-containers/)


## Get VPN setup 

- Call IT @ 64100 depart to get you `anyconnect` downloaded.

## Getting acquainted with your HPCC environment

If you are connected to VPN, log into HPCC from your terminal 


```bash
ssh username@bmiclusterp.chmcres.cchmc.org
#example
ssh sid1df@bmiclusterp.chmcres.cchmc.org
```

Otherwise 

```bash
ssh username@research.cchmc.org
#example
sid1df@research.cchmc.org

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
[sid1df@bmiclusterp2 /]$ module avail
#Loading appropriate modules
[sid1df@bmiclusterp2 /]$ module load nextflow
[sid1df@bmiclusterp2 /]$ module load singularity/3.7.0

```

### Handling  batch jobs on HPCC


```bash
#submit
bsub <runscript.sh (make sure to include < followed immediately by filename)
#check the status of current jobs 
bjobs
# kill specific jon 
bkill jobid 
# kill all jobs 
bkill 0 

```

### Reference genome/file locations (not all there, may need to download)

Supporting databases that we use are under `/HaganLab/databases/`

### Transferring files to and from  HPC 

- Trailing slash on sending side transfers only contents of the directory, without slash it transfers directory itself and contents


```bash
rsync -rvtP local/files/location/ hagjl2@bmiclusterp.chmcres.cchmc.org:/scratch/hagjl2/HPC/location
# Example 
rsync -rvtP /Users/tlhagan/Downloads/Genes hagjl2@bmiclusterp.chmcres.cchmc.org:/scratch/hagjl2/igenomes/Macaca_mulatta/Ensembl/Mmul_1/Annotation/Genes
#Run this from your local terminal 
#look at the order as well for to and from
#Example moving files from cluster to local 
(base) ➜  Documents rsync -rvtP /Users/amnahsiddiqa/Documents/CCHMC_Projects/Kiana_Pasare/01.RawDatacopy2 sid1df@bmiclusterp.chmcres.cchmc.org:/data/HaganLab/projects_data/0002_prj_bcapko_pasare#Example moving file from local to cluster 
(base) ➜  Documents rsync -rvtP  sid1df@bmiclusterp.chmcres.cchmc.org:/data/HaganLab/irene_dc/samplesheet.csv /Users/amnahsiddiqa/Documents/CCHMC_Projects/Kiana_Pasare/
```


- Filezilla Instructions: use ` bmiclusterp2.chmcres.cchmc.org` as target and `22` as port together with your CCHMC credentials (your username, password)


## Working interactively on the cluster

### From your local terminal/RStudio

**These R packages may also be useful for connecting to a remote server from your local environment:**
[SSH](https://cran.r-project.org/web/packages/ssh/)  
[remoter](https://cran.r-project.org/web/packages/remoter/)  
[rmote](https://github.com/cloudyr/rmote)  
[ssh-utils](https://cran.r-project.org/web/packages/ssh.utils/index.html)  


## Remote RStudio
You can run Rstudio on the hpc and access it from a local browser, as explained (In progress)
