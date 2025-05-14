# Exercise 1

In this exercise you will create your first two cloud resources on ResearchCloud:

1. Storage volume
1. Workspace

## 1. Create a storage volume

First create a storage volume.

Why create a storage volume? Data stored on the workspace will be deleted when the workspace is deleted, unless it lives on a permanent storage volume. Storage volumes can be *attached* to (and detached from) a workspace. Data stored on the storage will still exist after the workspace is deleted!

Follow the steps in the [documentation](https://utrechtuniversity.github.io/vre-docs/docs/first-steps.html#create-storage-volume) to create your storage unit, **but please take care to**:

- Choose a a unique name that will allow you to re-identify the storage unit, e.g. `test_firstname_firstletteroflastname`.
- Choose the smallest possible size for your storage volume.

## 2. Create a workspace

Now create your workspace! Follow the steps in the [documentation](https://utrechtuniversity.github.io/vre-docs/docs/manuals/creating.html), but please **first read the instructions below**.

**In the 'Catalog Item' step, make sure to select one of the following options:**

- Python Workbench Desktop
- R-Studio - R4
- Jupyter Notebook

**In the 'Cloud provider' step, make sure to choose the following options:**

- SURF HPC Cloud
- Latest version of the operating system
- 1 Core - 8 GB RAM

**In the 'Options' step, make sure to select the storage volume you created earlier!**

# Exercise 2: reproducible environments

These exercises live in different repositories that also contain example code. Choose the one that corresponds to the catalog item you created above:

- Python Workbench: [exercise repo](https://github.com/UtrechtUniversity/src-python-example/)
- RStudio: [exercise repo]()
- Jupyter Notebook: [exercise repo]()

