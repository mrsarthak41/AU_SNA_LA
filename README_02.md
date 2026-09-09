# Network 02: Micro-Level Co-Authorship Centralities & Community Detection

## Objective
This notebook applies advanced spectral and structural graph algorithms to the foundational edge list. The goal is to calculate the mathematical influence of individual researchers and algorithmically detect organic research laboratories and academic clusters without relying on formal departmental labels.

## Theoretical Background
This analysis relies on four core mathematical indicators:
1. **Node Strength (Weighted Degree):** Measures the absolute volume of bilateral collaborative ties an author possesses.
2. **Eigenvector Centrality:** Measures "influence." A high score indicates that an author collaborates frequently with *other* highly connected authors (identifying senior hubs/lab directors).
3. **Betweenness Centrality:** Measures "brokerage." A high score indicates an author acts as a critical bridge connecting different, isolated research groups on the shortest paths through the network.
4. **Louvain Community Detection:** A heuristic algorithm that extracts communities from large networks by optimizing "modularity"—mathematically grouping nodes that are more densely connected to each other than to the rest of the network.

## Process & Methodology
1. **Graph Reconstruction:** Rebuilt the undirected, weighted graph from `coauthorship_edge_list.csv`.
2. **Centrality Computation:** Calculated Degree, Strength, Eigenvector (max_iter=1000), and Betweenness.
3. **Community Detection:** Executed the Louvain algorithm to partition the 5,581 authors into distinct clusters.
4. **Interactive Visualization:** Used PyVis to render a physics-based, interactive HTML network map explicitly filtering for the most prominent research cluster.

## Libraries Used
* `pandas` & `networkx`: For data structuring and core graph algorithms.
* `networkx.algorithms.community`: For executing the Louvain modularity algorithm.
* `pyvis.network`: For rendering interactive, physics-based network visualizations.

## Key Results & Insights

* **Organic Clustering:** The Louvain algorithm successfully partitioned the 5,581 authors into **137 distinct organic research communities**.

### 🌟 Insight 1: The "Powerhouse" Community (Community 6)
The algorithm identified Community 6 as a massive, highly active research powerhouse (heavily focused on Education, EdTech, and AI). It contains the university's most frequent collaborators, including Gabriel F and Marrone R (42 shared publications), as well as the entire C3L leadership team.

### 🌟 Insight 2: The Structural Roles of the C3L Leadership
Filtering the centralities for the C3L directors reveals distinct, mathematically proven roles within the network architecture:
* **Professor Dawson (The "Godfather/Hub"):** Holds the highest Eigenvector Score (`0.161077`). This mathematical signature indicates he serves as a highly influential senior hub, connected to the most well-connected individuals in the network.
* **Professor Joksimovic (The "Bridge"):** Holds the highest Betweenness Score (`0.004114`). This proves his role as a primary broker, acting as the structural bridge that connects disparate research sub-groups (e.g., bridging education researchers with computer science/AI researchers).
* **Professor Kovanovic (The "Core Anchor"):** With `152` collaborative ties and a strong eigenvector score, he is deeply and densely embedded within the core of this powerhouse research cluster.

* **Visual Output:** Generated `c3l_community_network.html`, an interactive physics-simulated map of the Community 6 topology.