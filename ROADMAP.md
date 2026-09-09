# Adelaide University Research Collaboration & Network Analysis (AU-SNA)

## Project Overview
This repository contains a comprehensive Social Network Analysis (SNA) of Adelaide University's research publications. Utilizing a dataset of over 3,200 research papers, this project maps the structural, semantic, and temporal dimensions of academic collaboration. The overarching goal is to apply advanced mathematical graph theory and predictive analytics to uncover how interdisciplinary teams form, how knowledge bridges are built, and how network positioning correlates with high-impact (Q1) academic and policy (Overton) success.

## Project Architecture & Roadmap

The project is structured into six distinct analytical phases, documented across sequential Jupyter Notebooks:

### 🟢 Phase 1: Micro-Level Analysis (Completed)
* **`Network_01_Data_Prep_and_EDA.ipynb`**
  * **Status:** Completed
  * **Focus:** Data ingestion, metadata cleaning, and combinatorial edge list generation. Transformed raw publication strings into a foundational undirected graph of 5,581 authors and 23,085 collaborative ties.
* **`Network_02_CoAuthorship_Micro.ipynb`**
  * **Status:** Completed
  * **Focus:** Mathematical extraction of influence and clustering. Calculated Degree, Eigenvector, and Betweenness centralities. Deployed the Louvain algorithm, successfully detecting 137 organic research communities and mapping the C3L "Powerhouse" cluster using interactive PyVis physics simulations.

### 🟡 Phase 2: Macro-Level & Semantic Analysis (Upcoming)
* **`Network_03_Institutional_Macro.ipynb`**
  * **Focus:** Aggregating collaborative edges at the `School or Department` level to calculate institutional Betweenness Centrality, identifying which departments act as interdisciplinary bridges.
* **`Network_04_Bipartite_Projections.ipynb`**
  * **Focus:** Constructing two-mode networks (Author-to-SDG and Author-to-Journal). Projecting these bipartite graphs to uncover thematic alignments and journal competition pools.

### 🔵 Phase 3: Temporal Evolution & Predictive Modeling (Upcoming)
* **`Network_05_Temporal_Evolution.ipynb`**
  * **Focus:** Slicing the graph by `Publication-Year` to measure network densification over time and track the evolutionary trajectory of specific research categories (e.g., AI in Education).
* **`Network_06_Impact_and_Performance.ipynb`**
  * **Focus:** Correlating structural network metrics (like Eigenvector Centrality) with external success metrics (`Scopus Citation Count` and `Overton` policy impact). Developing a machine learning pipeline to predict the probability of Q1 journal publication based on an author's network embedding.

## Tech Stack
* **Data Processing:** `pandas`, `itertools`, `collections`
* **Graph Algorithms:** `networkx`, `community` (Louvain)
* **Visualization:** `pyvis.network`, `matplotlib`