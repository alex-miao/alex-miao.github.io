---
layout: post
title: "Time-Lock Encryption"
date: 2020-11-07
categories: cryptography
tags: [cryptography]
---

In the design of cryptographic encryption schemes, a core tenent is to ensure that the key space is large enough so that an exhaustive search over the keys is computationally infeasible. However, early on, cryptographers realized that perhaps there are instances when we do want a "bad" encryption scheme, one in which it is possible to decrypt, but only after an extensive search over the possible keys.

# Merkle Puzzles

One of the first applications of this was by Ralph Merkle in 1974, for his eponymous Merkle Puzzles. Merkle Puzzles were an attempt at creating a public key encryption scheme, in which there is no worry regarding key distribution, as there is with symmetric encryption schemes.

Say that Alice has some message $$m$$ that she wants to send to Bob. The idea is to first pick some symmetric encryption scheme $$(E,D)$$ that has a large key space, say 128-bit binary strings. Bob first picks $$2^{32}$$ possible keys for our symmetric encryption scheme, $$k_1,\dots,k_{2^{32}}$$ with $$k_i\in \{0,1\}^{128}$$. Bob then selects $$2^{32}$$ 32-bit binary strings $$k_1',\dots,k_{2^{32}}'$$, and a random permutation $$\sigma:\{0,1\}^{32}\to \{0,1\}^{32}$$. Using the $$k_i$$ and $$k_i'$$, Bob prepares $$2^{32}$$ puzzles $$p_1\,\dots,p_{2^{32}}$$, where puzzle $$p_i=E(0^{96} \| k_i', \sigma(i)\| k_i)$$. Bob sends all of these puzzles to Alice over a public channel.

Alice randomly picks a puzzle $$p_j$$, and does a exhaustive search over the $$2^{32}$$ possible values for $$k_j'$$ to decrypt $$D(0^{96}\| k_j', p_j)$$. Alice has to try $$2^{31}$$ combinations in expectation, but it can be done in a reasonable amount of computation. Alice then gets $$\sigma(j)$$ and $$k_j$$. She sends to Bob $$c=\sigma(j)\| E(k_j,m)$$. Bob knows which key $$k_j$$ corresponds to $$\sigma(j)$$, and so can decrypt $$m=D(k_j,c)$$.

An eavesdropper would see the $$2^{32}$$ puzzles, but would not know which $$j$$ Alice picked. Therefore, in order to be able to decrypt the ciphertext $$c$$, the eavesdropper would have to try decrypting all of the puzzles until finding the one with the key corresponding to $$\sigma(j)$$. In expectation the eavesdropper has to brute force $$2^{31}$$ puzzles, each requiring on average $$2^{31}$$ attempts to solve, which is $$2^{62}$$ attempts in total, which is much harder than what Alice had to do. With this scheme, there is a quadratic gap in computational difficulty between what Alice does and what an eavesdropper has to do to break the encryption.

# Time-Lock Puzzle

Rivest, Shamir, and Wagner in 1996 proposed a scheme to reveal messages after a fixed period of time, using the idea of creating a computation of a fixed difficulty. The scheme is based off modular squaring, a one-way function commonly used in cryptography introduced by Michael Rabin.

To encrypt a time lock some message $$m$$, Alice picks an symmetric encryption scheme $$(E,D)$$ and encrypts $$m$$ to produce ciphertext $$c_m=E(k,m)$$.

Alice then picks two large primes $$p$$ and $$q$$ and has $$n=pq$$. She picks $$t$$, which roughly is how much time she wants to pass before the secret is revealed (specifically the number of squaring operations mod $$n$$ that someone needs to compute to be able to decrypt) and a random value $$a>1$$ in $$\mathbb{Z}/n\mathbb{Z}$$. She computes $$a^{2^t} \mod n$$ quickly by first computing $$e=2^t \mod \phi(n)$$ (she knows the factorization of $$n$$ so $$\phi(n)$$ can be computed easily), then obtains $$a^{2^t} \mod n = a^e \mod n$$. This works since $$e=2^t+x\phi(n)$$ for some integer $$x$$, and we have that $$a^e \mod n=a^{2^t+x\phi(n)}\mod n=a^{2^t}+(a^{\phi(n)})^x \mod n=a^{2^t} \mod n$$ since by Euler's Theorem $$a^{\phi(n)}=1\mod n$$. She encrypts $$k$$ as $$c_k=k+a^{2^t} \mod n$$.

Alice then publishes $$(n,a,t,c_k,c_m)$$. Anyone trying to get to the message would have to repeatedly square $$a$$ $$t$$ times $$\mod n$$ to decrypt $$c_k$$ and get $$k$$, and then using $$k$$ to decrypt $$m=D(k,c_m)$$. They would not be able to do the shortcut Alice used to get $$a^{2^t}$$ since they would not be able to compute $$\phi(n)$$ without the factorization of $$n$$. Note that this computation of repeated squaring is not parallelizable, which is crucial in creating a time locked puzzle.
