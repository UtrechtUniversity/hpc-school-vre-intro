## RStudio:
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

The GitHub repository of the project that we are going to reproduce in this exercise can be viewed [here](https://github.com/bu-ma415/reproducibility-example)
Copy the following command in the terminal of your RStudio workspace:
```
git clone 
```

### Step 4: Open the R project file
In the file navigator in Rstudio (bottom right panel), navigate to the cloned repository (data > storage > cloned project folder) and click the project file.

### Step 5: Install `renv`

Open the R console window (bottom left panel) and type:
```
install.packages('renv')
```

### Step 6: Use `renv` to install packages from `renv.lock` file

```
renv::restore()
```

### Step 7: Now open the R script and run file


