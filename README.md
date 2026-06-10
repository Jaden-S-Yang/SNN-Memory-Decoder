# SNN-Memory-Decoder
# Biologically Constrained Spiking Neural Network & Spatial Memory Bayesian Decoder

This repository contains a complete computational neuroscience pipeline written in Python. The project constructs a "Digital Twin" of a rodent hippocampus to simulate, implant, and decode synthetic spatial memories using a Leaky Integrate-and-Fire (LIF) Spiking Neural Network (SNN) and a Poisson Naive Bayes Decoder.

## Project Architecture & Pipeline

The pipeline is executed across four distinct phases:

1. **Phase A: Passive Listening & Data Processing** - Processed raw extracellular spike times and continuous trajectory data from a simulated rodent navigating a linear track.
2. **Phase B: Bayesian Decoding** - Built a Poisson Naive Bayes Decoder utilizing neural tuning curves to map raw neural firing rates back into probabilistic physical locations.
3. **Phase C: SNN Physics Modeling** - Constructed a 16-neuron Spiking Neural Network from scratch utilizing Leaky Integrate-and-Fire (LIF) biological physics, incorporating a custom 16x16 Synaptic Weight Matrix ($W$) and exponential synaptic decay ($\tau_{syn} = 5.0\text{ ms}$).
4. **Phase D: Targeted Active Retrieval** - Injected a sub-threshold targeted electrical ping into the network to initiate a cascade of neural pattern completion, forcing a latent "silent" memory to echo back and undergo spatial reconstruction.

## Key Findings

### 1. The Synaptic Weight Matrix (The Latent Memory)
By structurally modifying the asymmetric synaptic weight matrix, a sequential "Reverse Run" memory (from 100cm back to 0cm) was silently embedded into the network's physical architecture without active electrical currents.
<img width="634" height="547" alt="image" src="https://github.com/user-attachments/assets/dbd1b2e0-19cd-4842-b29f-cee509e66e86" />


### 2. Decoded Memory Recall
Upon delivering a targeted electrical stimulus to the initiating neuron, the network successfully executed autonomous pattern completion. Feeding the resulting raw spike train into the Bayesian Decoder yielded a perfect spatial reconstruction of the latent memory trajectory.
<img width="817" height="547" alt="image" src="https://github.com/user-attachments/assets/c75d6eb5-d70e-438f-882e-ca191c4b9186" />


## How to Run
Open and execute the `BNC_Project_Notebook.ipynb` (or your notebook name) in a Jupyter Notebook environment. All biological physics parameters, SNN network architectures, and decoding algorithms are self-contained.

## Data Prerequisites
This notebook utilizes public neurophysiology datasets provided by the **Collaborative Research in Computational Neuroscience (CRCNS)** data sharing repository. 

To run this notebook, you must register for a free account at [crcns.org](https://crcns.org) and download the **hc-3 dataset** (Hippocampus data from rats performing linear track behavior and sleep). Specifically, you will need:
* `crcns-hc3-metadata-tables.zip` (Metadata tables)
* `ec012ec.187.tar.gz` (Active linear track session)
* `ec012ec.188.tar.gz` (Post-behavior sleep session)

Place these files in your Google Drive or local working directory as specified in the notebook configuration cell.

* **Note on Session Flexibility:** While this pipeline defaults to session files `ec012ec.187` (linear track) and `ec012ec.188` (post-behavior sleep), the code is built as a generalized pipeline. It can accept other sessions from the `ec012` animal or similar experimental blocks within the hc-3 dataset, provided the underlying file structure (metadata tables, spike times, and positional tracking files) remains consistent.

## Dependencies
* NumPy
* Matplotlib

## License
This project is licensed under the MIT License - see the LICENSE file for details.
