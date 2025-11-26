## Optimizing Robustness and Label Efficiency in Hybrid Quantum Binary Classifiers via Active Learning Strategy Proportion

This repository contains the code, data, and results for the research project **"Optimizing Robustness and Label Efficiency in Hybrid Quantum Binary Classifiers via Active Learning Strategy Proportion"**.

The project investigates how the balance between **Active Learning (AL)** and Passive Learning impacts the stability and cost-efficiency of Quantum Neural Networks (QNNs) in the **NISQ (Noisy Intermediate-Scale Quantum)** era.

---

## Project Overview

Quantum computing in the NISQ era faces two major hurdles: **high hardware noise** and **prohibitive computational costs** for training variational algorithms.

This work addresses these challenges by systematically varying the proportion of active vs. passive samples during training. We define **Robustness** as the stability of the training process (low standard deviation, $\sigma$) and **Efficiency** as the minimum number of labels required to reach a target precision.

---

##  Key Findings

Our empirical analysis (N=6 simulations per strategy) reveals a statistically significant trade-off between efficiency and robustness, defining two optimal regimes:

| Regime | Strategy | Outcome | Scientific Insight |
| :--- | :--- | :--- | :--- |
| **Maximum Efficiency** | **$(2P+8A)$** <br> *(20% Passive, 80% Active)* | **40% fewer samples** required vs. baseline. | Ideal for rapid prototyping or scenarios where data labeling is the primary bottleneck. |
| **Superior Robustness** | **$(8P+2A)$** <br> *(80% Passive, 20% Active)* | **Lowest Instability ($\sigma=25.4$)**. | Essential for deployment on noisy hardware. Acts as a "buffer" against gradient outliers caused by uncertainty sampling. |

---

##  HCAI Alignment (Human-Centered AI)

This project aligns Quantum AI with HCAI principles by transforming "black box" quantum training into a **controllable and trustworthy** process:

1.  **Trustworthiness:** By quantifying and optimizing for **Robustness**, we ensure the system behaves predictably despite inherent quantum noise.
2.  **Control & Viability:** By maximizing **Efficiency**, we reduce computational barriers, transitioning Quantum ML from elite research to a viable tool for broader human application.
3.  **Stability:** Active Learning is utilized not just for speed, but as a control mechanism to mitigate optimization divergence.

---

##  Methodology & Architecture

* **Model:** Hybrid Quantum-Classical Classifier (PyTorch + Qiskit).
* **Quantum Circuit:** `EfficientSU2` ansatz with `ZFeatureMap`.
* **Strategy:** Uncertainty Sampling (Active Learning).
* **Dimensionality Reduction:** **PCA** (784 $\to$ 4 dimensions).
    * *Note:* PCA was mandatory to fit the MNIST dataset onto a 4-qubit circuit (due to hardware constraints). This aggressive reduction introduces noise, further justifying the need for the robust AL strategies developed in this work.

---

##  Installation & Usage

### Prerequisites
* **Python 3.9** (Mandatory: The code relies on the `qiskit-aer` `Estimator` primitive which has specific version constraints).

### Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/guilhermemalves03/Active-Learning-Strategies-in-QNNs.git
    cd your-repo-name
    ```

2.  **Install dependencies:**
    ```bash
    pip install qiskit qiskit-aer qiskit-machine-learning torch numpy pandas matplotlib seaborn
    ```

3.  **Run the Simulation:**
    To reproduce the experimental results comparing all 11 strategies:
    ```bash
    python main_simulation.py
    ```
    *Warning: The full simulation suite (11 strategies times 6 seeds) is computationally intensive and may take several hours depending on your CPU.*

---

## 📂 Repository Structure

* `main_simulation.py`: Core script containing the Hybrid QNN loop and AL strategies.
* `results/`: Directory where CSV logs and metrics are stored.
* `plots/`: Generated visualizations (Efficiency and Robustness graphs).
* `paper/`: PDF version of the scientific paper describing this work.

---

## Citation

If you use this work or methodology, please cite:

```bibtex
@article{alves2025optimizing,
  title={Optimizing Robustness and Label Efficiency in Hybrid Quantum Binary Classifiers via Active Learning Strategy Proportion},
  author={Alves, Guilherme and Silva, Luis},
  journal={HCAI Lab Project},
  institution={University of Coimbra},
  year={2025}
}
