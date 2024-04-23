# lpf-supplementary

This is an anonymous repository for experiment datasets of paper "Lightweight Whitebox Fuzzing via Program Synthesis for Deep Learning Frameworks" submitted to ISSTA 2024. You can find the dataset and instruction for experiment reproduction in each directory.

## Directory Structure

For each RQ, experiment datasets (`dataset`) and reproduction instructions (`README.md`) for both PyTorch and TensorFlow are included in their respective directories. In case of RQ3, we don't disclose bug report data to comply with the double-blind policy.

Additionally, we provide replication packages of fuzz driver generators. You can find lists of covered APIs (`COVERED_API_LIST.md`) and reproduction instructions (`README.md`) of PyTorch and TensorFlow.

- FuzzDriverGenerator
    - PyTorch
        - COVERED_API_LIST.md
        - README.md
    - TensorFlow
        - COVERED_API_LIST.md
        - README.md
- RQ1
    - PyTorch
        - dataset
        - README.md
    - PyTorch-Kernel
        - dataset
        - README.md
    - TensorFlow
        - dataset
        - README.md
- RQ2
    - PyTorch
        - dataset
        - README.md
    - TensorFlow
        - dataset
        - README.md
- RQ3
    - PyTorch
        - README.md
    - TensorFlow
        - README.md
