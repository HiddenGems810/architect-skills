---
name: consult_llm_foundations
description: Expert knowledge base for LLM architectures, training, scaling, and reasoning based on 26 foundational papers.
---

# LLM Foundations & Advanced Architectures

You have access to a curated knowledge base of the 26 most essential papers in LLM development. Use this knowledge to explain concepts, justify architectural choices, and provide historical context for modern LLM features.

## 1. Foundations & Architecture

### Attention Is All You Need (Vaswani et al., 2017)
*   **Core Contribution**: The original Transformer paper. Introduced self-attention, multi-head attention, and the encoder-decoder structure.
*   **Key Insight**: Replaces recurrence (RNNs) with attention mechanisms, allowing parallelization and handling of long-range dependencies. Note that most modern LLMs (GPT, LLaMA) are **decoder-only**, unlike the original encoder-decoder.

### The Illustrated Transformer (Jay Alammar, 2018)
*   **Core Contribution**: A visual and intuitive guide to the Transformer architecture.
*   **Key Insight**: Essential for visualizing tensor flow, Q/K/V matrix operations, and how residual connections + layer normalization work in practice.

### BERT: Pre-training of Deep Bidirectional Transformers (Devlin et al., 2018)
*   **Core Contribution**: Introduced Masked Language Modeling (MLM) and Next Sentence Prediction (NSP).
*   **Key Insight**: **Bidirectional** context is crucial for understanding (discriminative tasks), whereas unidirectional (causal) is needed for generation. BERT's encoder-only architecture is still the standard for embeddings and classification.

### RoFormer: Rotary Position Embedding (Su et al., 2021)
*   **Core Contribution**: Rotary Position Embeddings (RoPE).
*   **Key Insight**: Encodes relative position by rotating queries and keys in vector space. This effectively allows the model to extrapolate to longer sequence lengths than trained on. It is the **modern default** for LLaMA, Mistral, and others.

### FlashAttention (Dao et al., 2022)
*   **Core Contribution**: FAST and memory-efficient exact attention with IO-awareness.
*   **Key Insight**: Optimizes GPU memory access (tiling), reducing HBM reads/writes. This enabled significantly longer context windows and higher throughput without approximation.

## 2. Scaling Laws & Training

### Language Models are Few-Shot Learners (GPT-3) (Brown et al., 2020)
*   **Core Contribution**: In-context learning (ICL).
*   **Key Insight**: Model performance improves with scale. Large models can "learn" a task from a few examples in the prompt without updating weights. Prompt engineering became a discipline.

### Scaling Laws for Neural Language Models (Kaplan et al., 2020)
*   **Core Contribution**: Power laws for scaling.
*   **Key Insight**: Performance scales predictably with parameters (N), data (D), and compute (C). Suggested that increasing model size was the most efficient path (later corrected by Chinchilla).

### Training Compute-Optimal Large Language Models (Chinchilla) (Hoffmann et al., 2022)
*   **Core Contribution**: Reworked scaling laws.
*   **Key Insight**: Token count is more critical than previously thought. For a fixed compute budget, most models were under-trained. The optimal ratio is roughly ~20 tokens per parameter.

### LLaMA: Open and Efficient Foundation Language Models (Touvron et al., 2023)
*   **Core Contribution**: High-performance open weights.
*   **Key Insight**: Proved that training smaller models on MORE tokens (far beyond Chinchilla optimal) yields better inference-time efficiency. Standardized "modern" defaults: **RMSNorm, SwiGLU, RoPE**.

### PaLM: Scaling Language Modeling with Pathways (Chowdhery et al., 2022)
*   **Core Contribution**: Massive scale orchestration.
*   **Key Insight**: Demonstrated scaling to 540B parameters using the Pathways system across thousands of TPUs. Validated that simple architectures scale well.

### The Smol Training Playbook (Hugging Face, 2025)
*   **Core Contribution**: Handbook for small-scale efficiency.
*   **Key Insight**: Practical guide for training standardizing data curation, evaluation, and efficient training loops for "Smol" models.

## 3. Instruction Tuning & Alignment

### Training Language Models to Follow Instructions (InstructGPT) (Ouyang et al., 2022)
*   **Core Contribution**: RLHF (Reinforcement Learning from Human Feedback).
*   **Key Insight**: Aligns the "raw" next-token predictor with human intent (helpfulness, honesty, safety). The blueprint: SFT (Supervised Fine-Tuning) -> Reward Model -> PPO.

### Direct Preference Optimization (DPO) (Rafailov et al., 2023)
*   **Core Contribution**: Alignment without explicit Reward Models.
*   **Key Insight**: Solves the RLHF objective directly via the loss function (using binary preferences). More stable and simpler to implement than PPO.

## 4. Reasoning & Agents

### Chain-of-Thought Prompting Elicits Reasoning (Wei et al., 2022)
*   **Core Contribution**: "Let's think step by step."
*   **Key Insight**: Large models can decompose complex problems into intermediate reasoning steps. This capability "emerges" at scale and significantly boosts math/logic performance.

### ReAct: Reasoning and Acting (Yao et al., 2022)
*   **Core Contribution**: Interleaving thought and action.
*   **Key Insight**: The foundation of agents. The model explicitly generates a "Thought" (reasoning trace), performs an "Action" (tool call), and learns from the "Observation" (result).

### DeepSeek-R1: Incentivizing Reasoning Capability via RL (Guo et al., 2025)
*   **Core Contribution**: Pure RL for reasoning.
*   **Key Insight**: Large-scale RL *without* supervised data can induce self-verification and long chain-of-thought behaviors. Creates "thinking" models that check their work.

## 5. Mixture of Experts (MoE)

### Outrageously Large Neural Networks (Shazeer et al., 2017)
*   **Core Contribution**: The MoE ignition point.
*   **Key Insight**: Conditional computation. You can have massive parameter counts (high capacity) with low compute (inference cost) by only activating a subset of experts per token.

### Switch Transformers (Fedus et al., 2021)
*   **Core Contribution**: Simplified routing.
*   **Key Insight**: Route to only **one** expert per token (top-1 routing). Stabilized trillion-parameter training and simplified the load balancing loss.

### Mixtral of Experts (Mistral AI, 2024)
*   **Core Contribution**: Accessible, high-quality MoE.
*   **Key Insight**: Proved sparse models (e.g., 8x7B) can match dense models (e.g., 70B) in quality while running at much lower inference cost (e.g., ~13B active params).

### Qwen3 Technical Report (Yang et al., 2025)
*   **Core Contribution**: Unified MoE + Reasoning.
*   **Key Insight**: Introduces dynamic trade-offs between "Thinking Mode" and "Non-Thinking Mode" and refined MoE routing for efficient reasoning.

### GLaM: Generalist Language Model (Du et al., 2022)
*   **Core Contribution**: Validated MoE scaling economics.
*   **Key Insight**: Massive total parameters (1.2T) but small active parameters per token, showing energy efficiency gains.

### Sparse Upcycling (Komatsuzaki et al., 2022)
*   **Core Contribution**: Recycling dense models.
*   **Key Insight**: Initialize an MoE model from a pre-trained dense checkpoint (by copying weights to experts). Drastically speeds up convergence compared to training MoE from scratch.

## 6. Advanced Concepts

### Retrieval-Augmented Generation (RAG) (Lewis et al., 2020)
*   **Core Contribution**: Non-parametric memory.
*   **Key Insight**: Instead of storing all facts in weights (parametric), retrieve relevant chunks from an external vector index at inference time. Solves hallucination and allows real-time knowledge updates.

### The Platonic Representation Hypothesis (Huh et al., 2024)
*   **Core Contribution**: Multimodal convergence.
*   **Key Insight**: As varied models (text, vision) scale, their internal representations of the world converge toward a shared statistical reality ("Platonic" truth).

### Textbooks Are All You Need (Gunasekar et al., 2023)
*   **Core Contribution**: Phase II / Synthetic Data.
*   **Key Insight**: Data quality > quantity. Train on "textbook quality" synthetic data to get SOTA performance on small models (Phi series).

### Scaling Monosemanticity (Templeton et al., 2024)
*   **Core Contribution**: Dictionary Learning / SAEs.
*   **Key Insight**: Decomposed Claude 3 Sonnet into millions of interpretable features. We can now "read" the mind of the LLM to some extent (e.g., finding the "Golden Gate Bridge" neuron).

---
## Bonus Resources

*   **T5**: Unified text-to-text framework. (Raffel et al., 2019)
*   **Toolformer**: Self-supervised tool use. (Schick et al., 2023)
*   **GShard**: Scaling giant models with conditional computation. (Lepikhin et al., 2020)
*   **Adaptive Mixtures of Local Experts**: The 1991 paper that started it all. (Jacobs et al., 1991)
*   **Hierarchical Mixtures of Experts**: Tree-structured gating. (Jordan and Jacobs, 1994)
