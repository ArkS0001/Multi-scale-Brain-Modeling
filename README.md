# Multi-scale-Brain-Modeling
multi-scale differentiable brain modeling workflow utilizing BrainPy, a unique differentiable brain simulator that combines accurate brain simulation with powerful gradient-based optimization.

# Illustration to the Differentiable Approach for Multi-scale Brain Modeling

Here, we illustrate to implement a differentiable approach for multi-scale brain modeling.
See our paper for more details:

## Requirements

In general, several Python packages related to the brainpy ecosystem are required to run the code:

- [brainstate](https://github.com/chaoming0625/brainstate)
- [brainunit](https://github.com/chaoming0625/brainunit)
- [brainscale](https://github.com/chaoming0625/brainscale)
- [braintools](https://github.com/chaoming0625/braintools)
- [brainpy-datasets](https://github.com/chaoming0625/braindata)

## Neuron fitting

We provide a simple example to illustrate the differentiable neuron fitting process.
    
- To fit the GIF model based on the membrane potential or spike trains, run the following command:

```bash
python neuron_fitting_of_gif_model.py
```

- To fit the HH model based on the membrane potential or spike trains, run the following command:

```bash 
python neuron_fitting_of_hh_model.py
```

## Training conductance-based EI spiking networks on cognitive tasks

We provide a simple example to illustrate the training process of conductance-based EI 
spiking networks based on the cognitive task of Evidence Accumulation.

The following arguments are used to control the model configuration and training:

- ``--conn_method``: The method to generate the connection matrix. It can be ``dense`` (dense connection), ``gaussian`` (sparse connection), or ``rand`` (random and sparse connection).
- ``--n_rec``: The number of recurrent neurons. Then, the excitatory and inhibitory neurons are divided by a 4:1 ratio.
- ``--w_ei_ratio``: The E/I weight ratio.
- ``--mode``: It can be ``train`` (train the network) or ``sim`` (simulate the network).
- ``--method``: The training method. Can be ``bptt`` (back-propagation through time) or ``expsm_diag`` or ``diag`` (if [brainscale](https://github.com/brainpy/brainscale) is available).


For example, to train a conductance-based EI spiking network, run the following command:

```bash

# Training with BPTT
python task-coba-ei-rsnn.py --method bptt

# Training with online learning methods in BrainScale
python task-coba-ei-rsnn.py --method diag
python task-coba-ei-rsnn.py --method expsm_diag --etrace_decay 0.98
```
