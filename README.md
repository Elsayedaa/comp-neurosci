
# Computational Neuroscience

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/melizalab/comp-neurosci.git/master)

This repository contains instructional materials for PSYC 5270, a course I teach on computational systems neuroscience at the University of Virginia. Students in this course learn how to process neuroscience data and model the way the brain processes, stores, and generates information. They also gain expertise in using scientific programming (specifically Python and its ecosystem of numerical and graphics libraries) to perform analyses and build models.

The current syllabus is [here](resources/syllabus.pdf).

## Getting started

### Cloud

The easiest way to run the exercises is to use [mybinder](https://mybinder.org). This will ensure that you have the latest version of the notebooks, all the data files, and the correct versions of required libraries. Click the badge at the top of this page to start a session. Note that this site does not save your work, so you have to be careful to download your `ipynb` files after you finish a session.

### Local: Anaconda

These instructions should work on any operating system to give you a working Python environment with all the required packages.

Install the Python 3.x version of [anaconda](https://www.anaconda.com/distribution/) (or [miniconda](https://conda.io/en/latest/miniconda.html) if you are comfortable using the shell). Run the following commands in a terminal, **one at a time** so that you can stop and fix any errors.

``` shell
conda create -n comp-neurosci python=3.9.7 numpy scipy pandas matplotlib notebook cython ipywidgets ipykernel
conda activate comp-neurosci
pip install -e .
python -m ipykernel install --user --name comp-neurosci --display-name "comp-neurosci"
```

When you run Jupyter, you will have the option of selecting the `comp-neurosci` kernel, which should have all of your software dependencies.

Make sure you work on a copy of the notebook (go to `File/Make a Copy...` in the notebook) that you name with your UVA computing ID; otherwise you may run into conflicts if you try to pull updates to the notebooks from the github repository.

### Local: docker

A [Docker](https://docker.com) image is provided for running the exercises locally. These instructions should work on Windows as well as Linux or OS X.  After installing Docker, run the following commands in your shell (bash for Linux and OS X; PowerShell for Windows):

``` shell
docker pull dmeliza/comp-neurosci:latest
docker run --rm --name comp-neurosci -p 8888:8888 -v "$PWD":/home/jovyan/work dmeliza/comp-neurosci:latest
```

(In PowerShell, replace `"$PWD"` with `${pwd}`. If this is your first time using Docker you may be asked to give permission to access the hard drive and network.)

The last command will start the docker container and the jupyter server. Copy the URL at the bottom of the output into your browser and you should have access to the notebook server. Note: files saved in the `work` subdirectory of the server will appear in your current working directory. Any other files or changes will be lost. Conversely, if you edit a file in the current directory it will show up in the `work` directory.

## Shared installation

Instructors may wish to have a single installation of the code and data to be shared by multiple users.

By default, the notebooks will load pregenerated data from files in the `data` subdirectory of this repository. If you are running a course and
