# Caravel User Project

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![UPRJ_CI](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml) [![Caravel Build](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml)

# kws-pyamnihc
## Repo for efabless KWS design challenge
### High level abstract

The idea is to develop a general CNN accelerator using Winograd convolution, this will be targeted for Keyword Spotting (KWS) detection using MFCC matrix. This will have a Wishbone interface and will need MFC coeffients to be calculated and available from Caravel harness.

I plan to have a systolic/bit-serial architecture inspired by bit serial processors like SERV. Evaluating one CNN layer at a time on a small footprint and then serializing for the entire network. An FSM control will manage the workflow, orchestrating the loading of weights and storing intermediate results to a buffer.

## Architecture
### May 7, '24 Update

The NN architecture, training and inference flow is followed from the following papers,

[Streaming keyword spotting on mobile devices](https://arxiv.org/pdf/2005.06720)

[Hello Edge: Keyword Spotting on Microcontrollers](https://arxiv.org/pdf/1711.07128)

## Design choices
1. DS-CNN with exact hyperparameters to be decided upon experiments and iterations
2. Parallel Convolution Execution unit to calculate 'n' 2D Convolutions in parallel
3. FSM to serialize 'n' parallel convolution blocks over all features
4. INT8 arithmetic
5. Wishbone bus to the Caravel SoC
6. The MFC Coefficients will be streamed from Caravel SoC

The starting point of development is exactly from the referenced papers, the optimizations to NN models (pruning and quantization) will be done based on results of training, inference performance and resource requirements obtained during experiments.

| :exclamation: Important Note            |
|-----------------------------------------|

## Please fill in your project documentation in this README.md file 

Refer to [README](docs/source/index.rst#section-quickstart) for a quickstart of how to use caravel_user_project

Refer to [README](docs/source/index.rst) for this sample project documentation. 

Refer to the following [readthedocs](https://caravel-sim-infrastructure.readthedocs.io/en/latest/index.html) for how to add cocotb tests to your project. 
