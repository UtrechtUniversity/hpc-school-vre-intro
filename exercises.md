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

Working with reproducible environments makes your life easier and your project more robust and reproducible. There are many advantages for working with environments, but if we just focus on SURF Research cloud: the benefit of working with GitHub and an environment manager for Python or R is that you can setup your project with all its dependencies with very little effort. This makes it easier to delete workspaces and start new ones in case of problems, or because the [maximum recommended lifetime of 4 weeks](https://utrechtuniversity.github.io/vre-docs/docs/responsible-use.html#vre-lifetime-and-security-updates) has been reached. If you would like to learn more about setting up a reproducible project, the workshop [Best Practices for Writing Reproducible code](https://www.uu.nl/en/research/research-data-management/training-workshops/best-practices-for-writing-reproducible-code) might be interesting for you.

These exercises live in different repositories that also contain example code. Choose the one that corresponds to the catalog item you created above:

- Python Workbench: [exercise repo](https://github.com/UtrechtUniversity/src-python-example/)
- RStudio: [exercise](r-environment.md)
- Jupyter Notebook: [exercise repo](https://github.com/UtrechtUniversity/src-python-example/blob/main/README.md#scenario-2-workspace-jupyter-notebook)

# Exercise 3: customizing Catalog Items

ResearchCloud gives you the ability to customize the Catalog Items (=workspace types) that you use to create workspaces. This lets you, for instance, add different Components (installation scripts) to a Catalog Item, allowing you to control what software gets installed on a workspace. Or you can tweak the *parameters* for certain Components to change their behavior.

In this exercise, we will modify a simple Catalog Item to automate the installation of a virtual environment in Jupyter Notebooks. This means that your workspace will automatically contain your dependencies when it has started up, so there's no need for the kind of manual steps you performed in Exercise 2.

**Note**: although the method outlined in this exercise is powerful, it is no replacement for understanding the kinds of environment and dependency managers you practiced with in Exercise 2! We primarily offer this exercise as a way of better understanding ResearchCloud.

## Clone the Catalog Item

You can only edit Catalog Items of which you are the owner. If you want to edit an existing Catalog Item of which you are not the owner, you'll first have to *clone* it.

1. In the ResearchCloud portal, go to *Development* and then *Catalog Items*.
2. Find the *Jupyter Notebook* item and click it.
3. If you scroll down, you will see a *Clone* button. Click it.

## Edit the Catalog Item

You are now taken to a selection screen which allows you to edit your (cloned) Catalog Item.

### Step 1. Select and order components.

Don't change anything in this step, but observe: the Catalog Item exists of a number or (ordered) *Components*. These are installation scripts that perform various tasks, e.g:

- installing the operating system, 
- installing Jupyter
- installing Custom Packages (! we're going to use this)

For now, just press the yellow 'Continue' button.

### Step 2. Name & description

Change the name to something descriptive such as: '[DEV] Jupyter <firstname> <first letter of lastname>'.

Press the yellow 'Continue' button.

### Step 3. Owner & support

Make sure the 'ITS VRE Demo' collaboration is selected as the owner for your Catalog Item. (This should be the default if you have only one collaboration.)

Press the yellow 'Continue' button.

### Step 4. Access

**Do not make the Catalog Item visible** (default.)

Press the yellow 'Continue' button.

### Step 5. Cloud settings

Don't change anything, but observe that you can choose which hardware is available for a workspace in your Catalog Item.

Press the yellow 'Continue' button.

### Step 6. Parameters

This is where interesting things happen!

The Catalog Item's Components have configurable settings that lets you tweak their behaviour. In this step, you see all the parameters defined by each different component. The component is listed under the "Source" column. Scroll down until you see the parameters defined by "Custom Packages":

- `requirements_file_repo_url`
- `requirements_file_path`
- `requirements_file_tag`

Together, these parameters allow you to designate a git repository that contains a file specifiying requirements for a Jupyter environment (called a kernel). These requirements will be installed on the workspace when it is created!

As you can see, the default is that the following file is installed:

* repository: https://gitlab.com/rsc-surf-nl/plugins/plugin-custom-packages.git
* tag (= git branch): `main`
* file: the file `files/sample-requirements.yml` inside the repository ([link](https://gitlab.com/rsc-surf-nl/plugins/plugin-custom-packages/-/blob/main/files/sample-requirements.yml?ref_type=heads)).

We can override these defaults to point to our own requirements file!

1. Take the `requirements_file_repo_url` parameter. In the rightmost column, change 'Keep value' to 'Overwrite'. 
    * Fill in this URL: `https://github.com/UtrechtUniversity/src-python-example.git`
1. Also overwrite the `requirements_file_path` parameter. Set it to: `rsc/requirements.yml`
1. The steps above will configure the component to install the dependencies we have outlined in [this file](https://github.com/UtrechtUniversity/src-python-example/blob/main/rsc/requirements.yml) on the workspace. 

Now scroll down and press the yellow 'Continue' button.

### Step 7. Workspace settings

Don't change anything. Press the yellow 'Submit' button.

### Create a workspace

Time to launch a new workspace based on your new Catalog Item!

**Watch out**: if you made a typo when overwriting the parameters above, it is possible that creation of your workspace will fail. That's because the Custom Packages component will then be unable to locate the necessary requirements file.

If everything goes well, your workspace will be created. When you login to it, you'll see that the custom environment `geo-kernel` is available. No need to install dependencies manually!

If in exercise 2 you worked with the Python example, you should be able to run the Notebook from that exercise without having to install dependencies. You can test this as follows:

- Select the `geo-kernel` environment
- Open a terminal and clone the example repo: `git clone https://github.com/UtrechtUniversity/src-python-example.git`
- Open the Notebook in `src-python-example/notebooks/Vectors.ipynb`
- Run it!


