# GOGGLE (Generative Modelling for Tabular Data by Learning Relational Structure, ICLR 2023) - A Short Summary

## Context

- Learning generative models for synthetic data is an important area in machine learning. Synthetic data can be used to simulate settings where real data is scarce or unavailable and support learning by increasing the quality of datasets and promoting fairness. Importantly, synthetic data is increasingly being used to overcome usage restrictions while preserving privacy.

- While generative models have achieved notable success in computer vision and natural language processing, similar advances have been less demonstrable in the tabular domain.


## Problem Statement

Given an input table, the framework should be able to generate synthetic data resembling the characteristics of the provided input while preserving statistical and structural properties.


## Lead to GOGGLE

Multiple notable works have been published to tackle this problem statement. A few of them are TGAN, CT-GAN etc. These were fundamentally using the fully connected layers as the building blocks.

**GOGGLE (ICLR 2023)** is a new paper in the literature that makes use of ideas from graph neural network  (GNN) literature, specifically the Message Passing Neural Network (MPNN) architecture, to capture the tabular data better.

## The Crux of the Paper

If we could "somehow" capture the "relational structure" in the tabular data and use this learned relational structure as an input to a generative modelling framework (Here, they used VAE), It could mitigate some of the challenges that arise during modelling tabular data.

- Why should we even capture the relational structure?
  - We hypothesise that the Data Generating Process of tabular data is better modelled using "sparse" relational structures than an all-to-all one.
  
- How do we capture the structure?
  - Use an adjacency matrix (and learn its parameters). 

## The Approach

The Naive approach incorporating the above idea will be a two-stage pipeline.

1. Learn the Relational structure (from the data), i.e. learn the parameters of the adjacency matrix. 
2. Use this "learned" relational structure as an input to an existing deep generative framework (say VAE). 

Instead of the two-stage pipeline, the paper proposes a unified framework:
- To learn the "adjacency matrix on the go", i.e. proposes a framework that "jointly" learns the relational structure and corresponding functional relationships to generate synthetic samples.
The authors use the Message Passing Neural Network (MPNN) architecture as the building block to carry out learning as described above.


## Experimental Validation

The authors support their idea with rigorous experiments using real-world datasets.

## Special Note

- GOGGLE is open-source and has been incorporated into the synthcity library for synthetic data generation.

**Implementation**: [Official GitHub Repository](https://github.com/tennisonliu/GOGGLE)

**Paper Link**: [GOGGLE Paper](https://openreview.net/forum?id=fPVRcJqspu)
