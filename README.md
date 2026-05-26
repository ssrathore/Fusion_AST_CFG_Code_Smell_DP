## Overview

This repository contains the code and resources for the research paper "Evaluating the Impact of Source Code Representation and Traversal Methods on Software Fault Prediction and Code Smell Detection". The study investigates and compares multiple code representation techniques—both traditional and pre-trained models—applied to two key software engineering tasks: software fault prediction and code smell detection.

We evaluate the effectiveness of Abstract Syntax Trees (ASTs), Control Flow Graphs (CFGs), their combination (AST+CFG), and pre-trained models (CodeBERT and Code2Vec). The experiments were conducted using publicly available datasets:

- PROMISE Dataset (for software fault prediction)
- MLCQ Dataset (for code smell detection)

## Approach

### 1. Code Representation Techniques
We compare the following code representations:

- **AST (Abstract Syntax Tree)**: Captures syntactic structure by parsing source code into a hierarchical tree representation.
- **CFG (Control Flow Graph)**: Models the control-flow relationships of the program, highlighting execution paths.
- **AST+CFG**: Combines AST and CFG to provide a holistic view of both syntax and execution flow.
- **CodeBERT**: A transformer-based pre-trained model for learning semantic representations from source code.
- **Code2Vec**: A path-based embedding technique that extracts AST traversal paths to generate code representations.

### 2. Dataset Preprocessing
- Extracting, cleaning, and normalizing source code files from the PROMISE and MLCQ datasets.
- Generating ASTs and CFGs using parsing tools (Eclipse JDT)
- Computing embeddings for pre-trained models (CodeBERT and Code2Vec).

### 3. Feature Extraction & Traversal Methods
To analyze the effectiveness of different structural and behavioral aspects of source code, we examine multiple traversal methods:

- **Root-to-Leaf (RL)**: Captures hierarchical relationships from the root node to leaf nodes in ASTs and CFGs.
- **Leaf-to-Leaf (LL)**: Focuses on terminal node interactions, highlighting relationships between different structural components.

### 4. Machine Learning Models
- Traditional representations (AST, CFG, AST+CFG) are used with **Random Forest classifiers**.
- CodeBERT embeddings are fine-tuned and used in **deep learning models (LSTMs & transformers)**.
- Code2Vec embeddings are used in **ML-based classifiers**.

### 5. Evaluation Metrics
The models are evaluated based on:
- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**

The best-performing approach is determined based on a balance of **performance, interpretability, and computational cost**.

## Key Findings

1. **AST+CFG consistently outperforms individual AST or CFG representations** by integrating structural and execution flow insights.
2. **CodeBERT achieves the highest accuracy in software defect prediction and code smell detection** but requires significant computational resources.
3. **Code2Vec is a practical alternative** that balances performance and efficiency, making it suitable for structural analysis.
4. **Traversal methods impact effectiveness**: Leaf-to-Leaf paths generally provide more informative embeddings than Root-to-Leaf traversals.


## Computational Resources

Most of the experiments were conducted on **Google Colab Pro**, utilizing both **GPU and TPU accelerators** for efficient training and evaluation of models:

- **Google Colab Pro** provided access to **high-performance compute resources**, ensuring smooth execution of deep learning models and large-scale computations.
- **GPU Setup**: We used an **NVIDIA A100 GPU** available on Colab Pro, which offers **80GB of high-bandwidth memory**, allowing for efficient model training and fine-tuning of CodeBERT embeddings.
- **TPU Setup**: We leveraged a **v2-8 TPU instance**, which significantly accelerated computations, especially for transformer-based models like CodeBERT, reducing training time by nearly **4x** compared to traditional GPUs.

By leveraging **Google Colab Pro's dynamic hardware allocation**, we efficiently managed the **feature extraction, embedding generation, and model training** processes, ensuring optimal performance without requiring local computational resources.




