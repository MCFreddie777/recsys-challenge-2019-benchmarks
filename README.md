# RecSys Challenge 2019 - benchmark models

This repository contains code to reproduce the benchmarks calculated for the data from the [ACM RecSys Challenge 2019](http://www.recsyschallenge.com/2019/) organized by trivago, TU Wien, Politecnico di Milano, and Karlsruhe Institute of Technology.

## Installation and usage

Getting Started

- Make sure you have installed the NVIDIA driver installed on the host system
- [Docker](https://docs.docker.com/get-docker/)

## Spawning and running the container

```
docker compose up -d 
```

## Usage

```
docker compose exec python /bin/bash
```


### Producing example data
Before running any models you can create a small example data set to test the execution of the models before running them with the bigger RecSysChallenge data sets.

    produce-example-data --data-path <target-location-for-csv-files>

### Running a single model
To run an individual model, run:

    run-single-model --data-path <path-to-csv-files-directory> --train-file <training-data-file> --test-file <test-data-file> --subm-file <submission-file-to-be-created> --model-name <name-of-model>

E.g.:

    run-single-model --data-path data --train-file train_example.csv --test-file test_example.csv --subm-file subm_example.csv --model-name random

To see what models are available, run:

    run-single-model --help

Note, that some models need a different set of training data. For example, the nn-item model relies on the item_metadata.csv as input.

### Running all models
You can run all models at once. This might take a while and the name of the submission files will be inferred from the model names. To do so, run:

    run-all-models --data-path <path-to-csv-files-directory> --train-file <training-data-file> --test-file <test-data-file> --meta-file <item-metadata-file>

E.g.:

    run-all-models --data-path data --train-file train_example.csv --test-file test_example.csv --meta-file item_metadata_example.csv 

