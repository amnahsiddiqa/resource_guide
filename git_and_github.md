---
title: "Git and Github"
author: "Amnah Siddiqa"
date: "2023-10-19"
---



## Set up Git and Github 
### For Mac
Use this command to download git 👉 `brew install git`
`Git --version`
### For Linux (Ubuntu)
Use this command to download git 👉 `sudo apt-get install git`

## Create an account on GitHub and create a new repo 

https://github.com/

- create a new repo by clicking on new repo 

![Screenshot 2023-10-18 at 5 46 29 AM](https://github.com/amnahsiddiqa/Docker_Singularity_HPC_Stuffs/assets/28387956/bacf34a6-81be-4285-8dff-327bb431d509)
## Clone it 

```
mkdir projectname 

git clone <repo-url>
```
## Configure Git 

```
git config --global user.name "amnahsiddiqa"
git config --global user.email "amnahsiddiqa@gmail.com"

# check your config worked or not 
git config -l
```





## make changes 

```
git add . 
git add filename.tsv
git commit -m "analysis for figure1"
git pull
git push 
```

see more beginners tips [here](https://render.com/blog/git-organized-a-better-git-flow)
 
## How do I go back from my current state to a snapshot made on a certain commit?
there are two types of commands and you should be careful in making selection to any one of them based on their purpose. 
`git revert and git reset` 

- I will explain reset as a rewind call. so you make a call to back to a place in your whole branch timeline to a certain commit and everything (all the changes you made after that)will be gone from that point onwards.

- Git revert on the other hand  undoes changes made in a given commit, creating a commit which is reverse (well, reciprocal) of a given commit. 

```
(base) ➜  test_demo2 git:(main) ✗ git reset 3bbe6d4 --hard
#HEAD is now at `sha key of commit` Initial commit
(base) ➜  test_demo2 git:(main) ✗ git reset --soft "HEAD@{1}"
(base) ➜  test_demo2 git:(main) ✗ git commit -m "Revert to 3bbe6d4 "

```



## Add issues and  commits for better collaboration  

- use the number of issue to close or fix the issue or get help
- use issues to get help from somebody else 

## A commit SHA (Secure Hash Algorithm) key:

- Commonly referred to as a "commit hash" or "commit SHA-1," is a unique identifier for a specific commit in a version control system, such as Git. It's a cryptographic hash value that's generated from the contents of the commit and the commit's metadata. The commit SHA key is used to uniquely identify and reference a particular state or snapshot of a repository at a specific point in time.
