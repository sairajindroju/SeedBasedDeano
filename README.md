# De-Anonymization Algorithm

## Overview

De-anonymization, also known as data re-identification, is a privacy technique that aims to identify individuals, groups, or transactions by cross-referencing anonymized information with other available data. In this project, we present an algorithm for de-anonymization that operates on two graphs: G1(V, E) and G2(V, E).

- **G1(V, E)**: The original graph containing privacy information.
- **G2(V, E)**: An auxiliary graph containing identity information, with some nodes already mapped (seed pair nodes).

The goal of the algorithm is to leverage the topological structure of the network and feedback from earlier mapping iterations to find new mappings.

## Getting Started

To use the De-Anonymization Algorithm, follow these steps:

1. Import G1 and G2 graphs using the `networkx` package by reading edge list data.

2. Import the seed-pairs data, which can be in either a text file or JSON format.

   - When importing the JSON file, it will be converted directly into a dictionary.

3. Split the seed-pair dictionary into two separate nodes lists:
   - One containing nodes in the seed-pair list corresponding to G1 nodes.
   - The other containing nodes in the seed-pair list corresponding to G2 nodes.

## Algorithm Description

The algorithm iterates through each node in G1, calculates its degree, and finds the degree of the corresponding node in G2. It considers the neighbors of these nodes and checks if they are already mapped and if their pairs exist in the seed pair list. Unmapped nodes are identified, and their similarity is measured by calculating a Score.

All scores are stored in a set, and eccentricity is computed for each iteration using the formula:

Ecce = (Score(max1) - Score(max2)) / Standard Deviation


The standard deviation is calculated for the set of scores, and the first and second maximum scores are found. If `ECCE` (eccentricity) is greater than 0.5, `Score(max1)`'s node is mapped to the node in G1 being iterated. This iteration continues until convergence, mapping seed pair nodes using the specified algorithm.

## Final Output

After all iterations, all seed pair nodes are appended to the initial seed-pair dictionary imported. The final result is this dictionary, which can be loaded into a text file for further analysis.


