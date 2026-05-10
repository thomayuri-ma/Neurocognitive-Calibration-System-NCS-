# Neurocognitive-Calibration-System-NCS
Detecting Hallucinations in Small Language Models via Intermediate Activation Probing

Neurocognitive Calibration System (NCS) 

Can we detect hallucinations in small language models, without retraining, without access to output logits, just by reading intermediate activations? 

That's what NCS does.

I trained linear probes across all 24 layers of OPT-1.3B on TruthfulQA (n=400). The results:

📊 Layer 22: 77.5% accuracy, AUC 0.855 📊 Layer 1: 55% accuracy, AUC 0.588

The finding I find most interesting isn't the peak number, it's the layer-depth profile. Probe discriminability rises monotonically across all 24 layers, with the steepest gain between layers 8–12 (AUC +0.087). PCA of layer 22 activations shows hallucination-relevant information is distributed across the residual stream, not concentrated in a small subspace. 

This tells us something mechanistic: a model's uncertainty about the truthfulness of its own output is encoded progressively as information propagates through the network, richer and more linearly decodable in deeper layers.  

Why does this matter? I build AI systems for vulnerable people through SerenMind AI. When a model produces a confident, fluent, and subtly wrong output for someone in a mental health context, that's not a benchmark failure. It's a real harm. NCS is a lightweight post-hoc detection layer that can flag high-risk outputs at inference time, no retraining, no large compute required.

📄 Preprint: https://lnkd.in/epYXW4WE
💻 Code: osf.io/d67ek

Part of three active research frameworks, NCS, CTA, and BIDF, all targeting safe and trustworthy on-device LLM deployment.

