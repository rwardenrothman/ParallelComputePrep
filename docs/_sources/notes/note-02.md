# {fa}`square-check fa-regular` High Performance Computing Lens (AWS Well-Architected Framework)
This AWS Documentation will inform me on the differences between tightly and loosely coupled HPC architectures.

## Link
https://docs.aws.amazon.com/wellarchitected/latest/high-performance-computing-lens/scenarios.html

## Highlights - Overview
- HPC is divided into two categories based on the degree of interaction between the concurrently running parallel processes: loosely coupled and tightly coupled workloads
- Loosely coupled HPC cases are those where the multiple or parallel processes don’t strongly interact with each other in the course of the entire simulation
- Tightly coupled HPC cases are those where the parallel processes are simultaneously running and regularly exchanging information between each other at each iteration or step of the simulation.
- With loosely coupled workloads, the completion of an entire calculation or simulation often requires hundreds to millions of parallel processes. These processes occur in any order and at any speed through the course of the simulation.
- Tightly coupled workloads have processes that regularly exchange information at each iteration of the simulation.

## Highlights - Loosely Coupled
- A loosely coupled workload entails the processing of a large number of smaller jobs. Generally, the smaller job runs on one node, either consuming one process or multiple processes with shared memory parallelization (SMP) for parallelization within that node.
- Loosely coupled applications are found in many areas, including Monte Carlo simulations, image processing, genomics analysis, and Electronic Design Automation (EDA)
- The loss of one node or job in a loosely coupled workload usually doesn’t delay the entire calculation. The lost work can be picked up later or omitted altogether. The nodes involved in the calculation can vary in specification and power.

## Highlights - Tightly Coupled
- Tightly coupled applications consist of parallel processes that are dependent on each other to carry out the calculation.
- The failure of one node usually leads to the failure of the entire calculation.
- Examples of tightly coupled HPC workloads include: computational fluid dynamics, weather prediction, and reservoir simulation.


