---
title: '01. Conda basics'
date: '2025-12-20'
draft: false
toc: true
---

## 0. Resources
1. Good tutorial: https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/
2. Official user guide to conda: https://docs.conda.io/projects/conda/en/latest/user-guide/index.html

## 1. Working with environments

### 1.1. Creating and activating an environment
In the following commands, I create a new virtual environment and install some basic packages related to data management and visualization.

```powershell
conda create --name project_name --channel conda-forge python=3.12 pip=25.1 ipython=9.4 jupyter=1.1.1 numpy=2.3.2 scipy=1.16 pandas=2.3.1 polars=1.32.0 matplotlib=3.10.5 seaborn=0.13.2 plotnine=0.15.0

conda activate project_name 

conda deactivate
```

In the following commands, I specify a location (the env subfolder to the current working directory) for a new virtual environment.

```powershell
conda create --prefix ./env --channel conda-forge python=3.12 pip=25.1 ipython=9.4 jupyter=1.1.1 numpy=2.3.2 scipy=1.16 pandas=2.3.1 polars=1.32.0 matplotlib=3.10.5 seaborn=0.13.2 plotnine=0.15.0

conda activate ./env
```

It is often a good idea to specify a path to a sub-directory of your project directory when creating an environment. 
- This makes it easy to tell if your project utilizes an isolated environment by including the environment as a sub-directory.
- This makes your project more self-contained as everything including the required software is contained in a single project directory.
- You can then use the same name for all your environments; if you keep all of your environments in the default `~/miniconda3/env/` folder, you’ll have to give each of them a different name.

### 1.2. Listing existing environments and the contents of an environment

```powershell
conda env list
conda list --name project_name
conda list --prefix ./env
```

### 1.3. Deleting entire environments

```powershell
conda remove --name project_name --all
conda remove --prefix /path/to/env --all
```

### 1.4. Sharing environments

Step 1. Automatically generate an `environmen.yml` file.
- The `--from-history` argument makes sure that only the final packages will be listed in the file.
- **If the `--from-history` argument is not included, this exported environment file will however not consistently produce environments that are reproducible across Mac OS, Windows, and Linux.** 
- The reason is, that it may include operating system specific low-level packages which cannot be used by other operating systems.

```powershell
conda env export --name project_name --from-history --file environment.yml
```

Step 2. Manually change the `environment.yml` file:
- Change the name of resulting environment.
- Change the channels of the packages.
- Add packages that should be installed using `pip` in the file.

```yml
name: P4DA
channels:
  - conda-forge
dependencies:
  - ipython=9.4
  - plotnine=0.15.0
  - python=3.12
  - polars=1.32.0
  - jupyter=1.1.1
  - pandas=2.3.1
  - seaborn=0.13.2
  - numpy=2.3.2
  - pip=25.1
  - pip:
    - pyfixest==0.30.2
  - matplotlib=3.10.5
```

### 1.5. Creating a new environment from an `environment.yml` file

Rebuilding an environment from scratch.

```powershell
conda env create --prefix ./env --file environment.yml

conda env create --file environment.yml
```

## 2. Installing packages

### 2.1 .From the `conda-forge` channel

- It is always a good idea to install packages from the `conda-forge` channel. Make this explicitly in the commands.
- It is always a good idea to explicitly specify the version of the packages.
- To search whether the required package exists in the channel, check the following website: https://conda-forge.org/packages/

```powershell
conda activate project_name 
conda install --channel conda-forge scipy=1.6
```

### 2.2. Using `pip`

- Important notes:
  - Pip is included in the Miniconda installer where it is used to install and manage OS specific Python packages required to setup your base Conda environment. You do not want to use this `pip` to install Python packages when using Conda environments.
  - If you find yourself needing to install a Python package that is only available via Pip, then **you should first install `pip` into your Conda environment and then use that `pip` to install the desired package**.
- Instructions:
  - Always explicitly install `pip` in every Python-based Conda environment.
  - Always be sure your desired environment is active before installing anything using `pip`.
  - Prefer `python -m pip install` over `pip install`; never use `pip` with the `--user` argument.