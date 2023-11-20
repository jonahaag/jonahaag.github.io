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

## TODO

- Add TLDR boxes for each section

## Overview

A short motivation highlighting the need for data-driven modelling in general, specifically physically sound learning (which is why we are all here) and surrogate modelling (which will be the focus of this blog post).

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

- general dynamical systems described by either ODE or PDE
- formulation as time series problem via discretization

## Two stage learning

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

Consider the two main training steps separately as they fulfill different needs and carried out one after another

### Embedding pretraining

- Note on the rise of AE architectures in general (VAE,...)
- Description of the proposed Koopman AE architecture
- loss function

#### A little detour to Koopman theory
- Connection of this approach to SINDy, eDMD etc.
- maybe short hint at relation to NLP

### Self attention and the transformer decoder

- Positional encoding
- Loss as standard time-series Markov model log-likelihodd
- Connection to numerical solvers/NODES, theoretical result
- Comparison to LSTM/RNN in terms of efficiency (MPC paper)

## Example results for the Lorentz system

<details>
<summary>TLDR</summary>
<br>
wip.
</details>

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


