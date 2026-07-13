# qexlibs
This is a meta repository that contains links to externally hosted libraries.


## List of libraries

| No.| Name         | URL                                                        | Documentation                                                    |
|--- |--------------|------------------------------------------------------------|------------------------------------------------------------------|
| 1. | QSE          | https://github.com/ICHEC/qse                               | https://ichec.github.io/qse                                      |
| 2. | QUEX         | https://github.com/ICHEC/quex                              | https://ichec.github.io/quex                                     |
| 3. | QCAP         | https://github.com/QCT-UEA-management/QCAP                 | https://munich-quantum-software-stack.github.io/MQSS-Interfaces/ |
| 4. | qc2          | https://github.com/qc2nl/qc2                               | https://qc2.readthedocs.io/en/latest/                            |
| 5. | QQuantLib    | https://github.com/NEASQC/FinancialApplications            | https://neasqc.github.io/FinancialApplications/dl.html           |
| 6. | wntr_quantum | https://github.com/Quantum4WaterDistribution/wntr-quantum  | https://quantum4waterdistribution.github.io/wntr-quantum/                                                        |
| 7. | qsvm4eo      | https://github.com.mcas.ms/ICHEC/qsvm4eo                   | https://github.com.mcas.ms/ICHEC/qsvm4eo/tree/main               |

## QSE

Quantum Simulation Environment (QSE) is developed at ICHEC, to explore analog quantum computing.

### Installation

QSE is available via `pip`, so one can install it by following commands in a python environment of one's choice -

```bash

pip install qse                   # basic installation
pip install "qse[pulser]"         # pulser backend
pip install "qse[myqlm]"          # myqlm backend
pip install "qse[myqlm,pulser]"   # both backends
```


## QUEX

Quantum Executor, provides classical simulated circuit runs, in a hardware agnostic way. It targets acceleration via `cupy` and `jax` and works on CPU, Nvidia GPUs and AMD GPUs.

```bash

pip install quex                # basic installation, Numpy
pip install "quex[nvidia]"       # nvidia backend, Cupy and Jax
pip install "quex[amd]"          # amd backend, Cupy and Jax
pip install "quex[metal]"        # apple-metal backend
```

## QCAP 

QCAP contains a catalog of foundational quantum computational chemistry algorithms running on simulators and real quantum hardware. It is not a framework as it introduces no abstraction layers, no base classes, and no hidden dependencies, but just readable, runnable code implemented in popular quantum SDKs.

### Environment setup

Dependencies are managed from the root `pyproject.toml` using [uv](https://github.com/astral-sh/uv). Install base dependencies plus your chosen SDK:

```bash
uv sync --extra qiskit
# or
uv sync --extra pennylane
# or both
uv sync --extra cudaq
```

Run any entry:

```bash
uv run python algorithms/vqe/h2_uccsd_qiskit/run_aer.py
```

## qc2

qc2 is a modular software designed to seamlessly integrate traditional computational chemistry codes and quantum computing frameworks. It is specifically crafted for hybrid quantum-classical workflows such as the variational quantum eigensolver (VQE) algorithm.

### Installation

To install qc2 from GitHub repository, do:

```console
git clone git@github.com:qc2nl/qc2.git
cd qc2
python3 -m pip install -e .
```

In this current version, qc2 can perform hybrid quantum-classical calculations using both [Qiskit Nature](https://qiskit.org/ecosystem/nature/) and [PennyLane](https://pennylane.ai/). However, the latter is an optional dependency. To install `Pennylane` and perform automatic testing with it, follow these steps:
```console
git clone git@github.com:qc2nl/qc2.git
cd qc2
python3 -m pip install -e .[pennylane] # (use ".[pennylane]" if you have zsh shell)
```

## QQuantLib

Quantum Quantitative Finance Library (QQuantLib) encompasses various state-of-the-art quantum algorithms and techniques tailored for the financial industry. It was programmed using the quantum software stack myQLM developed by EVIDEN.

### Installation

The mandatory Python libraries and packages for using the **QQuantLib** can be found into the *environment.yml* file.

## wntr_quantum

wntr_quantum builds on the python package [WNTR](https://github.com/USEPA/WNTR) to leverage quantum computing for the simulation and optimization of water networks. 

### Installation 

To install wntr_quantum from GitHub repository, do:

```console
git clone git@github.com:QuantumApplicationLab/wntr-quantum.git
cd wntr-quantum
python -m pip install .
```

WNTR Quantum can use a dedicated EPANET solver that allows to offload calculation to quantum linear solvers. This custom EPANET code can be found at : https://github.com/QuantumApplicationLab/EPANET. To install this sover follow the instructions below:

```
# clone EPANET
git clone https://github.com/QuantumApplicationLab/EPANET

# build EPANET
cd EPANET
mkdir build
cd build 
cmake .. 
cmake --build . --config Release

# copy the shared lib
cp lib/libepanet2.so <path to wntr-quantum>/wntr-quantum/wntr_quantum/epanet/Linux/libepanet22_amd64.so

# export environment variable
export EPANET_TMP=<path to tmp dir>/.epanet_quantum 
export EPANET_QUANTUM = <path to EPANET_QUANTUM>
```

## qsvm4eo

qsvm4eo is a package for running Support Vector Machines (SVMs) computed with a quantum kernel for Earth Observation data.

### Installation
Clone the repo and (making sure you’re in the directory where the `pyproject.toml` file is situated) install the package and its dependencies using `pip` (to install in editbale mode use the `-e` flag)
```
pip install .
```

## Exporting environment

The [pyproject.toml](./pyproject.toml) file can be used via `uv` package manager to maintain a cumulative dependencies of the libraries that we add.

If one needs a more traditional `requirements.txt` file to install the necessary libraries, one can export
on using -

```bash
uv export --format requirements.txt --no-hashes --output-file=requirements.txt 
```
