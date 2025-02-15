<div style="display: flex; align-items: center; justify-content: space-between;">
    <!-- First Image (Left) -->
    <img src="logos/qnexus-logo.png" style="width: 100px;">
    <img src="logos/logo blue+blue.png" style="width: 350px;">
    <div style="text-align: center; flex-grow: 1;">
        <h1 style="margin: 0;">Quantum Key Distribution Workshop</h1>
        <h2 style="margin: 0; font-weight: normal; color: gray;">CQTraining 3 | QNexus, February 2025</h2>
    </div>
    <!-- Second Image (Right) -->
</div>
<br>
<hr>
Welcome to the second edition of the CQTraining workshop! We are excited to have you join us at QNexus on February 15, 16, and 17'th, 2025. This workshop is designed to review and deepen your knowledge of Quantum Key Distribution (QKD).

## Table of Contents
- [CQTraining 2: Quantum Key Distribution Workshop](#cqtraining-2-quantum-key-distribution)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
    - [Using Conda](#using-conda)
    - [Directly from PyPi](#directly-from-pypi)
    - [Check Installation](#check-installation)
  - [Introduction](#Introduction)
  - [Tasks](#Tasks)
  - [Notes](#Notes)

## Installation

To ensure you have all the necessary tools and packages installed, please follow the instructions below:

### Using Conda
To create the environment with all required dependencies, run:
```bash
conda env create -f qnexus-qkd.yml --name [env_name]
conda activate [env_name]
```

### Directly from PyPi
Alternatively, you can install the necessary packages directly using pip:

```bash
pip install 'qiskit[visualization]' qiskit-aer qiskit-ibm-runtime --upgrade
```

### Check Installation
Check that you have everything correctly installed by running:
```bash
python -c "import qiskit; import qiskit_aer; import qiskit_ibm_runtime; print(qiskit.__version__); print(qiskit_aer.__version__); print(qiskit_ibm_runtime.__version__)"
``` 

You should get an output that ressembles (with potentially slighly different versions):
```
1.3.2
0.16.1
0.35.0
```
## Introduction
In the BB84 protocol, Alice sends Bob a series of single photons/states through a quantum channel. If Eve measures these photons before they reach Bob, then her measurement can be detected, and Alice and Bob will know that an eavesdropper is spying on them.
However, in practice, Alice will most likely send multiple photons with the same state; it is indeed not an easy task to create only single photons 100% of the time. Therefor, Eve will intercept one of the photons and let the others pass to Bob. She will store the quantum state of her photon in a quantum memory and wait for the bases reveal. After Alice and Bob reveal their bases, Eve can then measure her stored states and get valuable information on the shared key.

To deal with this weakness, the BBM92 protocol uses a source of entangled photons which are received by both Alice and Bob, instead of relying on Alice to send a quantum message to Bob. The rest of the protocol remains the same as with BB84. This renders the technique used by Eve in the BB84 case (photon number splitting attack, or PNS attack) completely ineffective.

## Tasks
In this challenge, you are asked to:
1. Simulate a PNS attack in the case of BB84 with Qiskit. In this case, and for the sake of simplicity, Alice will always send 2 photons/states to Bob, making Eve's attack 100% effective.
2. Implement the BBM92 protocol.
3. Demonstrate the effectiveness of BBM92 against the PNS attack scheme which was described in the case of BB84. We will consider the case where two pairs of photons are emitted each time, instead of one.

**Notes**:
- You can use the BB84 codes from the workshop. (it is provided in the template notebook for the challenge)
- To simulate Alice and Bob measuring their entangled photons (in BBM92), you must perform both measurements before running the qiskit job to ensure the correctness of the results, i.e., you cannot measure Alice's qubit and run the job and then measure Bob's qubit afterwards.
- If you cannot implement your code in time, or if you want to further explain your solution, you can write down additional explanations where mentioned in the challenge's template notebook.
