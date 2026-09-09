# Network 01: Data Preparation and Exploratory Data Analysis

## Objective
The goal of this notebook is to ingest the raw Adelaide University research publication dataset (Aurora Scimago), clean the unstructured metadata, and generate a mathematically rigorous edge list to serve as the foundation for our co-authorship network graphs.

## Libraries Used
* `pandas`: For data manipulation and cleaning.
* `networkx`: For initial graph validation and node/edge counting.
* `itertools`: To mathematically generate all possible pairs of co-authors per paper.
* `collections.Counter`: To aggregate frequencies and calculate edge weights.

## Process & Theory
In a co-authorship network, researchers are represented as **Nodes**, and their joint publications are represented as **Edges**. The strength of their collaborative tie is represented by the **Weight** of the edge (the frequency of co-authorship). 

Because the raw dataset stores authors as a single semicolon-separated string (e.g., `Prentice S; Dorstyn D; Benson J`), this notebook performs the following:
1. **Data Cleaning:** Drops missing values and explodes the string into iterable Python lists.
2. **Combinatorics:** Uses `itertools.combinations` to generate complete undirected subgraphs (cliques) for every paper. If a paper has 3 authors, it generates 3 distinct edges connecting them all.
3. **Aggregation:** Counts the occurrences of each unique pair to assign the final edge weight.

## Results
* **Total Unique Authors (Nodes):** 5,581
* **Total Collaborative Ties (Edges):** 23,085
* **Outputs:** The processed data was successfully exported to `coauthorship_edge_list.csv` and `cleaned_aurora_data.csv` to ensure efficient loading in subsequent analytical pipelines.