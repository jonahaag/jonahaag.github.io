---
title: 'Transformers for Modeling Physical Systems'
date: 2023-11-17
permalink: /posts/2023/11/transformers/
tags:
  - Scientific ML
  - Transformer
  - Koopman
---

This is a very rough first draft for my blog post based on the Paper "Transformers for modeling physical systems" by Geneva and Zabaras published in Neural Networks in 2022.
This work is part of the seminar "Machine Learning in the Sciences" in the winter term 23/24 at the University of Stuttgart.

## Overview

A short motivation highlighting the need for data-driven modelling in general, specifically physically sound learning (which is why we are all here) and surrogate modelling (which will be the focus of this blog post).

Main points:
- need to go beyond pure black-box ML methods
- establish a nice set of tools to integrate existing and verified (or at least widely accepted) theory into state-of-the-art ML/DL techniques
- surrogate modeling: replace existing model with similar, but much faster one, e.g. for prototyping, controller design (MPC) and other optimization related tasks that need to simulate/evaluate a model many times

What are the key findings and results (abstract-like fashion)
- using the self attention mechanism to model physical dynamics
- relation of the self attention mechanism to numerical integration methods
- Koopman dynamics and its connection to the encoder-decoder architecture

## The setup and problem formulation

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

- general dynamical systems described by either ODE or PDE, i.e., wide range of application domains (fluid mechanics, transport, materical science, MD)
- other papers to mention maybe: Brandstetter et al., Markus Bühler, ...
- formulation applies to initial value, boundary value, and stochastic problems
- formulation as time series problem via discretization, this sets the stage for the rest of the paper as we do not consider derivatives of any form -> is this a limitation for particular problems? dependence on step size?

## Two stage learning

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

Consider the two main training steps separately as they fulfill different needs and carried out one after another

The basic idea is to split finding a suitable embedding/latent space and actually modeling the dynamics, where the former is still guided by some concept of dynamics to ensure that the found space is suitable.
This is also where the hybrid/physics-informed notion comes in.

### Embedding pretraining

- Note on the rise of AE architectures in general (VAE,...)
  - Basic AE is a rather intuitive approach to dim reduction/subspace identification
  - VAE as generative extension of the basic AE
  - Many application of AE architectures (and extensions/combinations with other concepts) can be found in the literature, e.g. SINDy
- maybe short hint at relation to NLP, although this applies to the entire method section
- Description of the proposed Koopman AE architecture
  - Koopman layer allows for prescription of some dynamical context
  - Also allows latent dim > state dim (see Lorentz example) without simply finding a trivial latent space
- loss function: sum of MSEs for reconstruction and prediction + regularization
- pretrained, then frozen

#### A little detour to Koopman theory
- But why does this even work? Main Koopman result: any nonlinear dynamical system can be estimated by linear dynamics in an infinite-dimensional representation
- This approach has been popping, see eDMD etc.

### Self attention and the transformer decoder

- Positional encoding as in the original transformer paper
- context length as hyperparameter
- offer some intuition on the self-attention mechanism, dot product as similarity measure, e.g. based on articles like https://medium.com/@geetkal67/attention-networks-a-simple-way-to-understand-self-attention-f5fb363c736d -> need to read up a bit more myself
- Loss as standard time-series Markov model log-likelihodd
- Connection to numerical solvers/NODES, theoretical result: self-attention is a superset of explicit Adam time-integration method -> don't show the full proff, but try to summarize effectively, while clearly highlighting the analogy between classical numerics and attention
- Comparison to LSTM/RNN in terms of efficiency (MPC paper), especially for surrogate modeling this is very interesting

- Figures of the training stages and architectures from the paper (Figures 1-3)
- embedd entire training sequence using the pretrained embedding, then train the transformer-decoder

## Example results for the Lorentz system

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

- introduce lorentz system as example for nonlinear, chaotic system
- they compare to one numerically integration and three ML methods for various predictive horizons
- shortly hint at other examples, mostly to hightlight some of the strenghts and weaknesses of the approach
- include figures 5-7

### Notes
How have transformers been used outside of this paper, what other architectures have emerged and how do they differ for this work? 

Maybe compare to related work which looked at the same example problem or alternative architectures in general:

- Temporal Fusion Transformers
- ...


## Conclusion

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

Maybe a short summary or just link back to the introduction

## Literature

- Geneva paper
- some Brunton/Kutz or other review paper on Koopman Theory, SINDy AE
- attention articles


