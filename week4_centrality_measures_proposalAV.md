# Centrality Measures Proposal

### DATA 620 | Week 4 Assignment
### Author: Alina Vikhnevich


## Introduction
This assignment proposes a network-based study using publicly available movie metadata from The Movie Database (TMDb) API. The goal is to define a feasible data source and analysis plan for comparing centrality measures across categorical groups. No data collection or analysis is reported here.

## Proposed Data Source
The proposed data source is The Movie Database (TMDb) API, which provides structured metadata about films, cast members, and individual actors. The API allows developers to retrieve information about movie credits and person-level attributes that can be used to construct a collaboration network.

Official TMDb developer documentation: [TMDb API Developer Documentation](https://developer.themoviedb.org/docs/getting-started)

Using this API, it is possible to retrieve movie credit records that list all actors appearing in a film, as well as person-level metadata such as gender. These endpoints make it possible to construct a network where actors are connected when they appear in the same movie.

## Network Structure
The proposed network is an actor co-appearance graph.

- Nodes: individual actors  
- Edges: an undirected edge between two actors when both appear in the same film  

This structure represents a natural social network because co-appearance reflects professional collaboration and shared participation in film projects.

## Categorical Variable
A categorical node variable is available from TMDb person details: gender. This variable allows grouping actors into categories and comparing node-level centrality measures across those groups.

## High-Level Data Loading Plan
The project would follow a staged workflow using Python tools at a high level.

1. Use `requests` to query selected TMDb API endpoints for a defined set of films and associated cast lists.  
2. Normalize and organize returned JSON records into tabular form with `pandas`.  
3. Extract actor identifiers and co-appearance pairs from cast lists.  
4. Build an undirected graph with `NetworkX`, where actors are nodes and co-appearances are edges.  
5. Attach categorical metadata, including gender, to each node.  
6. Compute degree centrality for all nodes and prepare grouped summaries by gender category.

This plan is presented as a proposal only.

## Centrality Measure Focus
The primary measure of interest is degree centrality. In this context, degree centrality captures how many distinct co-appearance ties an actor has in the constructed network. Comparing degree centrality across gender groups can support an initial assessment of whether network connectivity differs by category.

## Hypothetical Predictive Outcome
A potential predictive question is whether actors with higher degree centrality are more likely to appear in future high-visibility films, and whether this pattern differs across gender groups. Under this hypothesis, greater network connectedness may be associated with later access to prominent projects, while the strength or direction of that relationship could vary by gender category.

## Conclusion
TMDb provides a practical API-based foundation for an actor co-appearance network with a categorical node variable. The proposed workflow outlines how degree centrality could be compared across gender groups and linked to a future visibility outcome in a subsequent analysis.