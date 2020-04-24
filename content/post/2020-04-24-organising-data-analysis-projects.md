---
title: Organising data analysis projects
author: ~
date: '2020-04-24'
slug: organising-data-analysis-projects
categories:
    - project-organisation
draft: true
---

## The idea

Organise a project to minimise complexity and redundancy while maximising ease-of-use, extensibility and portability.

## Overview

Folders contain one part of the project (e.g., data). Scripts within folders generate the content of those folders (e.g., csv files ready for analysis). These scripts may depend on the content of other folders.

Reusable functions (e.g., for data reading) are placed in R files in the folders corresponding to that part of the project (e.g., data reading functions would be in the data folder).

Each script should be able to run when its dependencies are present and the working directory is that of the project.

## Snakemake

[Snakemake](https://snakemake.readthedocs.io/) can be used to automate running scripts in the right order. Note that for `.Rprofile` to work, execution should be done as `shell: Rscript path/to/script.R` rather than `script: path/to/script.R`.

## Example
