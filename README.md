Absence-Aware Language Model (AALM) — Proof of Concept

AALM is a TinyGPT-based transformer designed to model contradiction as signal rather than noise.
It introduces a dialectical learning loop where the system learns not only from what it predicts, but from what it fails to predict — its absences.

Core Idea

Standard LLMs (GPT-style) optimize toward a single statistical closure: minimizing cross-entropy between predicted and target tokens.
AALM modifies this by introducing absence-aware loss dynamics that treat the “unrealized” probabilities — the tokens not chosen — as epistemic material.
Negation becomes a training signal, allowing the model to engage with its own closure productively.

Architecture

Base: Tiny GPT (2-layer TransformerEncoder, 1k vocab)

Dataset: Synthetic dialectical curriculum (repeat, alternate, quota tasks)

Hooks:

absence_alpha: scales the negation field (coherence-through-exclusion)

absence_entropy_alpha: adds an openness prior via entropy of absences

Constitution hooks allow rule modification during training (soft/hard biasing of logits)


Output: Tracks loss and “absence entropy” as dual metrics of learning and openness


Files

dialectical_transformer_final_run.py — core model + training loop

comp_test1.py — comparative harness between baseline GPT and AALM

run_log.txt — training logs and generation outputs

*.pt — saved checkpoints for both baseline and AALM

 Results Summary

AALM demonstrates higher absence-entropy variation and more principled divergence in generation compared to baseline GPT.

Token-level trajectories reveal emergent meta-token awareness (rule-level reasoning) and self-consistent contradictions.


Conceptual Lineage

Inspired by Hegelian dialectics, Lacanian absence, and the notion that closure is not failure but the condition of renewal.
Where GPT learns to complete, AALM learns to reconstitute.
