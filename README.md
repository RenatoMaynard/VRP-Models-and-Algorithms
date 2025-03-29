# Vehicle Routing Problem (VRP) Formulations

This repository contains four classical formulations for the Vehicle Routing Problem, along with Gurobi + Python (NetworkX) examples. Each formulation includes:

1. **Mathematical Models** in LaTeX (ready to copy-paste).
2. **Python Code** to demonstrate how to:
   - Build and solve the MIP model in Gurobi.
   - Plot resulting routes using NetworkX and Matplotlib.

## 1. Classical VRP (MTZ Formulation)
- **File**: `VRP (MTZ Formulation).ipynb`  
- **Description**: Uses the Miller–Tucker–Zemlin (MTZ) constraints to eliminate subtours.  
- **Key Variables**: 
  - `x[i,j]` (binary) indicating route arcs. 
  - `u[i]` (continuous) for subtour elimination.  
- **Pros**: Simpler to implement.  
- **Cons**: Weaker LP bounds for large instances.

## 2. Flow-Based VRP
- **File**: `VRP Flow-Based Formulation.ipynb`  
- **Description**: Uses a single flow variable `f[i,j]` to ensure connectivity and capacity constraints.  
- **Key Variables**: 
  - `x[i,j]` (binary) for arcs, 
  - `f[i,j]` (continuous) representing the flow on each arc.  
- **Pros**: Stronger LP relaxation.  
- **Cons**: Larger model (more variables).

## 3. Set Partitioning Formulation (Branch-and-Price Perspective)
- **File**: `VRP Set Partitioning Formulation.ipynb`  
- **Description**: Each variable `y_r` represents an entire feasible route. The model partitions the set of customers among a chosen subset of routes.  
- **Key Variables**:
  - `y_r` (binary) indicates whether route `r` is used.  
- **Usage**: Often used with branch-and-price or column generation, especially for large-scale VRPs.

## 4. Multi-Commodity Flow Formulation
- **File**: `VRP Multi-Commodity Flow Formulation.ipynb`
- **Description**: One flow variable per commodity (often one commodity per customer) to model capacity in more granular detail.  
- **Key Variables**:
  - `x[i,j]` (binary), 
  - `f[i,j,k]` (continuous) for commodity k on edge (i,j).  
- **Pros**: Very flexible, can handle multiple demand types.  
- **Cons**: Potentially huge model.

## How to Run
1. Make sure you have [Gurobi](https://www.gurobi.com/) installed and licensed.
2. Install [networkx](https://networkx.org/) and [matplotlib](https://matplotlib.org/).
   ```bash
   pip install networkx matplotlib
   
## References
1. G. B. Dantzig and J. H. Ramser. The truck dispatching problem. Management Science, 6(1): 80–91, 1959.
2. P. Toth and D. Vigo. Vehicle Routing: Problems, Methods, and Applications, 2nd ed. SIAM, 2014.
3. G. Laporte. Fifty Years of Vehicle Routing. Transportation Science, 43(4): 408–416, 2009.
4. R. Baldacci, A. Mingozzi, and R. Roberti. Recent exact algorithms for solving the vehicle routing problem under capacity and time window constraints. EJOR, 218(1): 1–6, 2012.
