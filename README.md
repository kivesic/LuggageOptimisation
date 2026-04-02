# Flying Home for Christmas: An Unexpected Optimisation Problem

> What do Christmas presents and mobile network congestion have in common?  
> More than you'd think — and the answer involves NP-hard combinatorial optimisation.

## Overview

This project frames a relatable holiday puzzle — *which presents should I pack in my checked luggage to make my family happiest?* — as a rigorous constrained optimisation problem. The mathematical structure is identical to resource allocation problems in telecommunications networks, a topic I researched during my PhD and published on at IEEE PIMRC 2010.

The goal: select exactly one present per family member (10 people, 5 options each = **~10 million combinations**) such that total utility is maximised without exceeding luggage weight and volume limits. Simple on the surface; computationally non-trivial at scale.

## The Problem

Given a set of candidate presents, each described by:

- **Utility** — how much the recipient will love it (0–10)
- **Volume** (litres)
- **Weight** (kg)
- **Price** (CHF)

...find the combination that maximises total utility while respecting the luggage constraints. One present per person; no splitting.

This is a variant of the **Multi-choice multi-dimensional 0-1 knapsack problem (MMKP)** — a generalisation of the classic 0/1 knapsack problem — and is proven NP-hard.

## Approach

The notebook walks through three stages:

1. **Brute-force baseline** — enumerate all combinations exhaustively; demonstrates the combinatorial explosion and why naive approaches fail at scale
2. **Integer Linear Programming (SciPy MILP)** — formulate the problem mathematically and solve it exactly using an ILP solver; compares runtime and solution quality against brute force: 16 min vs. 10 ms
3. **Analysis and reflection** — discuss when exact solvers are sufficient and when heuristic or approximate methods become necessary for real-time applications

## Connection to Research

During my PhD in Information and Communication Technology (University of Zagreb), I worked on adaptive multimedia resource allocation in mobile networks. One of the core challenges: under congestion, pick a quality configuration for each active session to maximise aggregate utility without exceeding available bandwidth. Same mathematical structure, very different domain.

My first paper on this problem: [IEEE PIMRC 2010](https://doi.org/10.1109/PIMRC.2010.5671784) ([full text](https://www.ieee.hr/images/50010415/PIMRC_2010.pdf)).

This project is a deliberate callback to that work — demonstrating that the same abstractions that appear in research settings emerge naturally in everyday life, and that a well-trained analytical instinct travels across domains.

## Stack

- Python 3
- pandas, matplotlib, numpy
- SciPy MILP solver (Python wrapper for HiGHS)
- Jupyter Notebook

## Repository Contents

| File | Description |
|---|---|
| `Luggage.ipynb` | Full annotated notebook: problem formulation, data, brute-force, ILP solution, analysis |
| `presents.csv` | A list of presents used in the notebook, their volumes, weights, prices and estimated utilities. |

## About Me

I'm a software developer and data analytics consultant (specialising in Splunk, Cribl, and Elasticsearch) with a PhD in telecommunications and a genuine interest in research — prototyping, experimenting, and applying rigorous methods to real problems.

This project is one example of how I think when I'm not investigating log pipelines.

- [LinkedIn](https://www.linkedin.com/in/krunoslavivesic/)
- [GitHub](https://github.com/kivesic)