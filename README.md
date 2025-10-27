# ⚛️ Quantum Protein Folding: A VQE Approach

**Project for the KY Quantum Hackathon**

[cite_start]This project demonstrates a hybrid quantum-classical workflow to predict the three-dimensional structure of proteins, one of the most complex challenges in computational biology[cite: 4, 24]. [cite_start]We use the Variational Quantum Eigensolver (VQE) algorithm to find the lowest energy state (ground state) of a protein, which corresponds to its most stable folded form[cite: 5, 29]. [cite_start]This demonstration focuses on the glycine molecule as its model[cite: 7].

## 🎯 Project Overview

[cite_start]Proteins fold into specific 3D structures to function, a process driven by finding their lowest energy state[cite: 28, 29]. [cite_start]Classical methods to simulate this are computationally massive[cite: 25, 30]. [cite_start]Quantum computing, specifically VQE, offers a path to model molecular energies more efficiently[cite: 31].

[cite_start]Our project implements a full pipeline[cite: 6]:
1.  [cite_start]**Classical Pre-processing:** We start with Cryo-EM data, which is then clustered using DBSCAN and broken into manageable fragments[cite: 6, 61, 62, 63].
2.  [cite_start]**Quantum Hamiltonian:** The molecular energy is encoded into a qubit Hamiltonian[cite: 6, 64]. Our notebook, `Protein-folding-glycine.ipynb`, demonstrates this crucial step by using PySCF to generate the molecular integrals and Qiskit to construct the necessary operators.
3.  [cite_start]**Quantum Simulation:** We use the **VQE** algorithm to iteratively find the ground state energy of the Hamiltonian[cite: 6, 65].
4.  [cite_start]**Error Mitigation:** We apply Probabilistic Error Mitigation (PEM) to reduce readout errors and improve the accuracy of the quantum simulation[cite: 7, 66].
5.  [cite_start]**Classical Post-processing:** The results are decoded and reassembled to model the final protein structure[cite: 67].

## 🔬 Our Methodology

The project follows a sequential, hybrid workflow:

1.  [cite_start]**Cryo-EM Data Processing:** Extracts molecular details from `.cif` or `.pdb` files[cite: 61, 81].
2.  [cite_start]**DBSCAN Clustering:** Groups nearby atoms to simplify the structure for analysis[cite: 62, 53].
3.  [cite_start]**Fragmentation:** Divides the large protein structure into smaller, manageable fragments that can be simulated[cite: 63, 57].
4.  [cite_start]**Hamiltonian Construction:** Represents the total energy of each fragment as a qubit Hamiltonian, using encoding strategies like parity and tapering to reduce the number of required qubits[cite: 64, 32, 85].
5.  [cite_start]**VQE Optimization:** A classical optimizer (like COBYLA) iteratively adjusts the parameters of a quantum circuit (an Ansatz) to find the set of parameters that minimizes the energy[cite: 65, 33, 86].
6.  [cite_start]**Probabilistic Error Mitigation (PEM):** Corrects for readout errors, a common source of noise in quantum simulations, to produce more reliable results[cite: 66, 34, 89].
7.  [cite_start]**Decoding & Reassembly:** Combines the low-energy solutions for each fragment to reconstruct the final, stable folded model of the entire protein[cite: 67, 57].

## 💻 Tech Stack

This project integrates classical data science libraries with quantum computing frameworks.

* [cite_start]**Quantum Simulation:** Qiskit [cite: 45, 49]
* **Classical Chemistry:** PySCF (used in the notebook for generating molecular integrals)
* [cite_start]**Data & Math:** NumPy, SciPy, Pandas [cite: 46, 50, 51]
* [cite_start]**Clustering:** Scikit-learn (for DBSCAN) [cite: 46, 53]
* [cite_start]**Plotting:** Matplotlib [cite: 46, 52]

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/PavanSuryaChintada/Protein-folding-glycine.git](https://github.com/PavanSuryaChintada/Protein-folding-glycine.git)
    cd Protein-folding-glycine
    ```

2.  **Create a Python environment and install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    *(You will need to create a `requirements.txt` file containing all the libraries listed above, e.g., `qiskit`, `pyscf`, `numpy`, `scipy`, `pandas`, `scikit-learn`, `matplotlib`, `qiskit-aer`)*

3.  **Run the simulation:**
    The core logic for Hamiltonian generation and VQE setup is in the Jupyter Notebook.
    ```bash
    jupyter notebook Protein-folding-glycine.ipynb
    ```

### Code Structure

[cite_start]The project is organized into the following modules as described in our plan [cite: 74-79]:
├── Protein-folding-glycine.ipynb # Main notebook for VQE simulation 
├── data_preprocessing.py # Handles Cryo-EM input and DBSCAN clustering 
├── fragmentation.py # Divides and reassembles molecular fragments 
├── hamiltonian_encoder.py # Builds the encoded Hamiltonian
├── vqe_solver.py # Executes the VQE algorithm 
├── mem_correction.py # Applies error mitigation 
├── decode_results.py # Generates the final structure 
## 📈 Results & Key Findings

[cite_start]Our experiments, run using the Qiskit simulator on the glycine molecule[cite: 91], led to several key takeaways:
* [cite_start]**Successful Convergence:** The VQE algorithm consistently converged to a stable, low-energy ground state, validating the hybrid model[cite: 93, 99].
* [cite_start]**Resource Optimization:** Using parity and tapering encoding strategies proved effective in reducing the number of qubits needed for the simulation[cite: 100, 85].
* [cite_start]**Improved Accuracy:** Probabilistic Error Mitigation (PEM) demonstrably enhanced the precision of our results by mitigating simulation noise effects[cite: 95, 101].

## 🔮 Future Scope

[cite_start]This project serves as a strong foundation[cite: 108]. Future work will focus on:
* [cite_start]**Scaling:** Extending the workflow to more complex protein chains[cite: 115].
* [cite_start]**Hardware Execution:** Testing the model directly on real quantum hardware[cite: 116].
* [cite_start]**Hybrid AI-Quantum:** Exploring hybrid AI-quantum models to further enhance prediction accuracy and efficiency[cite: 117].

## 👥 Team

* [cite_start]**Tanuja:** Project Lead [cite: 9]
* [cite_start]**Pavan Surya:** Algorithm Developer (Hamiltonian & Encoding) [cite: 10]
* [cite_start]**Ravi Teja:** Quantum Simulation Engineer (VQE) [cite: 11]
* [cite_start]**Bhavya sai:** Research Analyst (Theory) [cite: 12]
* [cite_start]**Rishitha:** Data Specialist (Preprocessing) [cite: 13]
