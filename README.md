# Bioinformatics Project Setup Guide

This guide walks through setting up R, Jupyter notebooks with R kernel, and connecting to the GitHub repository for the Arabidopsis stress integrative omics project.

## Prerequisites

- Linux system (tested on Pop!_OS 22.04)
- Python and pip installed
- Git installed
- Internet connection

## Step 1: Install or Upgrade R

Check if R is installed:

```bash
R --version
```

If R is not installed or version is below 4.4, upgrade to the latest version.

### Add R Repository

```bash
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc > /dev/null
sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/"
sudo apt update
sudo apt install r-base
```

Verify R version (should be 4.5.x):

```bash
R --version
```

## Step 2: Install IRkernel for Jupyter Notebooks

Install IRkernel package:

```bash
sudo R -e 'install.packages("IRkernel", repos="https://cran.rstudio.com/")'
```

Register the kernel with Jupyter:

```bash
R -e 'IRkernel::installspec()'
```

Verify kernels:

```bash
jupyter kernelspec list
```

You should see `ir` in the list.

## Step 3: Install BiocManager

In R console or script:

```r
install.packages("BiocManager")
```

## Step 4: Set Up Jupyter Notebook

Create a new notebook or open an existing `.ipynb` file in VS Code.

Select the R kernel from the kernel picker (top-right corner).

Run R code in cells.

## Step 5: Clone or Connect to Repository

If starting fresh:

```bash
git clone git@github.com:FedericoGritti/at_stress_integrative_omics.git
cd at_stress_integrative_omics
```

If connecting existing folder:

```bash
git init
git remote add origin git@github.com:FedericoGritti/at_stress_integrative_omics.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

## Usage

- Use R cells for data analysis with Bioconductor packages.
- Use Python cells if needed (reticulate or separate notebooks).
- Commit and push changes regularly.

## Troubleshooting

- If R kernel not showing: Re-run `IRkernel::installspec()`
- Permission issues: Use `sudo` for system-wide installs
- BiocManager version conflicts: Ensure R >= 4.4

## Project Structure

- `test_r.ipynb`: Example notebook with R and Python cells
- Other files: Add your analysis scripts and data