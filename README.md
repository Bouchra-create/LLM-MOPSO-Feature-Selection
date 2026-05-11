# LLM-MOPSO-Feature-Selection
Hybrid LLM-guided Multi-Objective PSO for Feature Selection in Medical Diagnosis
# LLM-MOPSO Feature Selection for Medical Diagnosis

Overview

This repository presents a hybrid feature selection framework that integrates **Multi-Objective Particle Swarm Optimization (MOPSO)** with **Large Language Models (LLMs)** to improve feature selection in high-dimensional medical datasets.

The proposed approach leverages semantic knowledge from LLMs to guide the initialization of the search process, enhancing convergence and solution quality.

---

Contributions

* A **hybrid LLM-guided MOPSO** framework for feature selection
* Integration of **semantic feature importance** derived from LLMs
* A **multi-objective formulation** balancing:

  * Feature reduction
  * Classification performance
* Comprehensive comparison with a **baseline (no-LLM) MOPSO**
* Evaluation using **cross-validation and test-set performance**

---

Methodology

### 1. Problem Formulation

Feature selection is modeled as a **multi-objective optimization problem**:

* Minimize the number of selected features
* Maximize classification performance (F1-score)

This is implemented as:

* Objective 1: ( \min |S| )
* Objective 2: ( \min (-F1) )

---

### 2. Optimization Algorithm

A binary **Multi-Objective Particle Swarm Optimization (MOPSO)** is used:

* Particle encoding: binary feature mask
* Archive: Pareto-optimal solutions
* Leader selection: random from archive
* Update: sigmoid-based binary PSO

---

### 3. LLM Integration

A Large Language Model is used to assign **importance scores** to features:

* Input: feature names
* Output: normalized importance scores in [0,1]
* Role:

  * Guides population initialization
  * Biases search toward relevant features

---

Evaluation Protocol

* Classifier: Random Forest
* Validation: Stratified 10-fold cross-validation
* Metrics:

  * F1-score (weighted)
  * Hypervolume (HV)
* Final evaluation on independent **test set**

---

 
 

 
 

---

Usage

Run the full experiment:

```bash
python main.py
```

This will:

* Execute both variants (No LLM vs LLM)
* Display convergence curves
* Generate Pareto fronts
* Output selected features

---

Results

The LLM-guided approach demonstrates:

* Faster convergence
* Improved exploration of the Pareto front
* Better trade-off between feature reduction and performance

Typical outputs include:

* Convergence curves
* Pareto front visualization
* Selected feature subsets

---

LLM Configuration

The framework uses a local LLM via API (Ollama):

* Model: `llama3.2:3b`
* Endpoint: `http://localhost:11434/api/generate`
 

Dataset

Experiments are conducted on a Parkinson’s disease dataset with high-dimensional acoustic features.

 

- 

Author

Bouchra Zekraoui

---

License

This project is licensed under the MIT License.

 
