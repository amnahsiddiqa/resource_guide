---
title: "Acquiring and Sharing Data"
author: "Amnah Siddiqa"
date: "2023-10-19"
---



## Goals

* Keep shared data (including processed data and results) in a stable shared location
* Link to data instead of copying/moving data
* Incorporate data linking in your script  
* Treat processed data and results as "raw" data objects for sharing purposes
* Describe data: origin, what's been done with it, what the columns/rows mean, etc.
* keep data files together with their metadata and any processing scripts when applicable, either physically or with a reliable link between them.

A good way to interact with data objects is in a manner similar to working with git for developing code: "pushing" and "pulling" data objects to and from remote repositories from within your working directory, scripting everything, instead of copying data manually into the project folder. This not only makes work easier, but also helps maintain data provenance and promotes transparency and reproducibility. Github repositories, however, are (currently) limited in size and are therefore not optimal for sharing large data objects and research projects. Instead we can use services such as Synapse and RStudio Connect and tools such as [Globus CLI](https://docs.globus.org) and the R [`pins` package](http://pins.rstudio.com). In addition to providing a way to incorporate data transfer in the script, these tools also manage the caching and check for updates beforing re-downloading data. The caching ensures that we still have the latest version available in our system in the case that the original becomes unavailable for whatever reason.     

Sharing data between "native" projects on the same file system can be done using the R package `pins` (see below). Sharing data among file systems can be done either directly with Globus or via servers such as Synapse and RStudio Connect. Interacting with servers such as Synapse and RStudio Connect can be done using either their own clients (see below) or with `pins`.  

To read more about data provenance and management:  
https://old.dataone.org/sites/all/documents/DataONE_BP_Primer_020212.pdf  
https://www.w3.org/2005/Incubator/prov/wiki/What_Is_Provenance  
https://docs.synapse.org/articles/provenance.html  

An example for a resource sharing plan to include in NIH grants:   https://github.com/lab-carpentry/blueprint-resourcesharing/blob/master/examples/NIH-example.md  

## From Synapse
https://docs.synapse.org/articles/  
Often the best way to work with data that live on Synapse is to download/upload them directly from Synapse using its [R](https://r-docs.synapse.org/articles/synapser.html), [pyhton](https://python-docs.synapse.org/build/html/index.html), or [CLI](https://python-docs.synapse.org/build/html/CommandLineClient.html) clients.  
See [here](https://docs.synapse.org/articles/provenance.html) for how provenance works on Synapse.  

For example, using the R package `synapser`:  
The function `synGet()` downloads the data into a cache folder in your home directory (`~/.synapseCache`) in whichever file system you're on. Every time you run the code, it checks your cached copy against the original on Synapse and re-downloads it only if there has been changes since the last download. The cache location is specified in `~/.synapseConfig`.  
