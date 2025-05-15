## RStudio:

This example uses the R package [`renv`](https://docs.posit.co/ide/user/ide/guide/environments/r/renv.html) for reproducing R environments. When using `renv` in a project, `renv` creates a lock file with a list of packages and version numbers of those packages that are used. This makes it possible to install exactly those packages on a new computer (e.g. a Research Cloud workspace) with one command. If you would like to learn more about setting up a reproducible project, the workshop [Best Practices for Writing Reproducible code](https://www.uu.nl/en/research/research-data-management/training-workshops/best-practices-for-writing-reproducible-code) might be interesting for you.

### Prerequisites
The steps below assuming that you have created an RStudio workspace in [exercise 1](./exercises.md#exercise-1) and are logged in to it.

### Step 1: Open the 'terminal' window
In the bottom left panel, click the ‘terminal’ tab.

### Step 2: Navigate to the storage volume

In the terminal window, type:
```
cd data
ls
```
Check the exact name of your storage volume in the output in the terminl

```
cd <the name of your storage volume>
```

### Step 3: Clone the reproducible project example

The GitHub repository of the project that we are going to reproduce in this exercise can be viewed [here](https://github.com/MindTheGap-ERC/StratPal_ms_supp).

- Get the HTTPS clone url from the github repository (green button with '<> Code') . 
- Copy the following command in the terminal of your RStudio workspace together with the clone url:
  
```
git clone 
```

### Step 4: Create R environment and run the code

Follow the 'Usage' instructions from the [README](https://github.com/MindTheGap-ERC/StratPal_ms_supp) of the project on GitHub.

### (Optional) Step 5: Run this script as a job

The script in this project is executed very fast. Imagine that you have a script that takes hours to run. While it should be able to do this exactly as described above, the more robust and recommended way is to run such a script as a 'background job' with `nohup`. Find instructions on how to do this in [Method 2 in this manual](https://utrechtuniversity.github.io/vre-docs/docs/manuals/long-jobs.html#method-2-using-nohup).

### (Optional) Step 6: Transfer your output data to cloud storage directly
If you have a [Surfdrive](surfdrive.surf.nl)-, Researchdrive- of Yoda account, you can transfer your output data there directly. Use the [manuals on our documentation website](https://utrechtuniversity.github.io/vre-docs/docs/manuals.html) to transfer your data there directly. 
> In theory this is also possible for OneDrive but this is not straightforward because you need web browser to login to Onedrive. The easiest way is to download data to your laptop first and then upload it to Onedrive.




