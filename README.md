# The RODEM HEP project starter

## Using this template
This repository defines a cookiecutter template for quickly building new base repositories.
To use this you first need to run 
```
pip install cookiecutter
```
On baobab you will need to do this in a virtualenv.
You can then run
```
cookiecutter git@github.com:sambklein/rodem_starter.git
```
Follow the prompts to create your new project.

## Introduction

The code in this repository demonstrates best practice when structuring a new project in the RODEM group.

This repository is built around using 
- `hydra`: to configure scripts
- `wandb`: for experiment tracking and hyperparameter optimization
- `pytorch lightning`: for handling boilerplate code in the training of neural networks

## Typical workflow
1) Research and development:
    * Collect data.
    * Get data loader.
    * Develop models.
    * Test models.
1) Start writing paper: 
    * Settle on models and evaluation. 
    * Run pipeline.
1) New requests: 
    * Update models.
    * Extend evaluation. 
    * Rerun models.
    * Rerun evaluation.
    * Update paper.    
9) Iterate 3. until done.

In the above workflow by far the most exhausting, time consuming, and boring, is step 4.
We should aim to cut down on this by building flexible automated workflows such that once the code has been fixed the full model training, model evaluation and result plotting can be done easily (ideally with a single command that launches all of the jobs straight to slurm).
Further, everything is ideally packaged such that our workflows can be easily reproduced by other groups.

### Orchestration
Note that at present this workflow does not make use of any workflow manager to orchestrate the full suite of jobs.
This is a missing piece, but not suitable tool has been found that can be installed on the UNIGE cluster and does not add overhead when working with SLURM and hydra.
