# ACALM: Auction-Consensus Algorithm with Loss Mechanism for Decentralized Task Allocation

This repository contains the official implementation of the **Auction Consensus Algorithm with Loss Mechanism (ACALM)** — a novel decentralized task allocation algorithm for multi-robot systems — alongside baseline implementations and an optimal centralized benchmark.

---

## Overview

The **ACALM algorithm** introduces a *loss propagation mechanism* to enhance convergence and robustness in distributed auction-based coordination.  
Each agent participates in consensus-driven bidding rounds, but unlike classical Consensus-Based Auction Algorithms (CBAA), ACALM uses loss estimates for bidding during
the auction as opposed to expected rewards.

This repository includes:

- **ACALM Algorithm** (proposed method)
- **CBAA Algorithm** (baseline implementation)
- **Centralized Optimal Task Allocation** (MILP benchmark using PuLP)

---

## Citation

If you use this code in your work, please cite the following publication:

Jose Rodriguez, Wenjie Dong, Constantine Tarawneh, and Qi Lu.  
*Auction Consensus Algorithm with Loss Mechanism for Decentralized Task Allocation.*  
2025 IEEE International Symposium on Multi-Robot & Multi-Agent Systems (MRS). Singapore, December 2025.

```
@inproceedings{rodriguez2025acalm,
  author    = {Jose Rodriguez and Wenjie Dong and Constantine Tarawneh and Qi Lu},
  title     = {Auction Consensus Algorithm with Loss Mechanism for Decentralized Task Allocation},
  booktitle = {2025 IEEE International Symposium on Multi-Robot \& Multi-Agent Systems (MRS)},
  year      = {2025},
  address   = {Singapore},
  month     = {December}
}
```

---

## Repository Structure

```
├── ACALM_Algorithm_v2.ipynb
│   ├─ Implements the proposed ACALM algorithm.
│   ├─ Simulates decentralized auction-consensus task allocation.
│   ├─ Compares performance against the optimal benchmark and CBAA.
│
├── CBAA_Algorithm.ipynb
│   ├─ Implementation of the Consensus-Based Auction Algorithm (CBAA).
│   ├─ Based on the method described in Choi et al., “Consensus-Based Decentralized Auctions for Robust Task Allocation,” IEEE Transactions on Robotics.
│
├── Centralized_Optimal_Task_Allocation.ipynb
│   ├─ Solves the centralized optimal assignment using a MILP solver (PuLP).
│   ├─ Generates and stores environment configurations:
│       - `drone_starts` (robot initial positions)
│       - `task_locations` (task coordinates)
│   ├─ Provides reference optimal total distances for performance benchmarking.
│
├── data/
│   ├─ (optional) JSON or CSV files with saved world configurations and results.
│
└── README.md
```

---

## Requirements

All scripts are written in Python (tested on Python 3.10+).  
You can install dependencies using:

```bash
pip install pulp numpy matplotlib
```

Optional (for faster numerical operations):
```bash
pip install pandas scipy
```

---

## Usage

### 1. Generate Benchmark Configurations

Run the MILP-based centralized solver first to create environment data:
```bash
jupyter notebook Centralized_Optimal_Task_Allocation.ipynb
```
This notebook:
- Generates random drone and task positions.
- Solves for the optimal task assignment using PuLP.
- Saves configuration data (`drone_starts`, `task_locations`).

### 2. Run Baseline (CBAA)

Execute the decentralized baseline:
```bash
jupyter notebook CBAA_Algorithm.ipynb
```
This will:
- Load the generated configurations.
- Perform decentralized auction-consensus task allocation.
- Log total distance and iteration statistics.

### 3. Run Proposed Algorithm (ACALM)

Finally, run:
```bash
jupyter notebook ACALM_Algorithm_v2.ipynb
```
This notebook will:
- Load the same scenarios.
- Execute the ACALM algorithm.
- Log the same results for comparison against the centralized and CBAA benchmarks.

---

## Results

All results can be visualized directly in the notebooks (via Matplotlib plots).

---

## Methodology Summary

| Algorithm | Type | Description |
|------------|------|-------------|
| **ACALM** | Decentralized | Proposed method introducing a novel loss-mechanism for auction-consensus. |
| **CBAA** | Decentralized | Classic Consensus-Based Auction Algorithm implementation. |
| **Centralized MILP** | Centralized | Optimal benchmark solved using PuLP for single-task single-robot instantaneous assignment (ST–SR–IA). |

---

## Acknowledgments

This work was conducted as part of the **MARS (Multiple Autonomous Robot System) Lab** at  
**The University of Texas Rio Grande Valley (UTRGV)** under Prof. **Qi Lu**.  

The authors would like to acknowledge funding provided by the NSF (National Science Foundation) CREST Center for Multidisciplinary Research Excellence 
in Cyber-Physical Infrastructure Systems (No. 2112650), the NSF CISE Minority Serving Institute (MSI) program (No. 2318682 & 2434916), and NSF Expand AI 
program (NSF Award No. 2434916).

---

## License

This repository is released for academic and research use only.  
For commercial use or redistribution, please contact the authors.

---

## Contact

**Jose Rodriguez**  
MSE Student, Electrical Engineering  
The University of Texas Rio Grande Valley (UTRGV)  
Email: [jose.rodriguez53@utrgv.edu]  

For Research Opportunities:  
**Dr. Qi Lu**  
Assistant Professor, Computer Science  
The University of Texas Rio Grande Valley (UTRGV)  
Email: [qi.lu@utrgv.edu]  

