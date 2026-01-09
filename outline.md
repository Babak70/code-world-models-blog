# Blog Post Outline: State-Tracking for Code World Models

## Story Arc

**Hook**: Code World Models promise AI that truly understands program execution—but they hit a wall with long-horizon state tracking.

**Conflict**: Architectures exist that can theoretically do state-tracking, yet they fail in practice on real code.

**Resolution**: The problem isn't just architecture—it's that state-tracking architectures need state-tracking *data* to learn.

**Implications**: For better Code World Models, we need hybrid architectures + the right training data format.

---

## Detailed Structure

### 1. Introduction: The State-Tracking Problem
- **What is state-tracking?** Variable tracking through operations
- **Shell game analogy** - intuitive framing
- **Why CWMs care**: Code agents, debugging, program synthesis
- **The gap**: Current CWMs struggle with long sequences

### 2. The Theory-Practice Gap
- Transformers vs RNNs: associative recall vs state-tracking
- Linear RNNs with extended eigenvalues [-1,1] should work... but don't
- **Key question**: Why don't theoretically superior architectures help?

### 3. Our Key Insight: Data Format Matters
- Standard next-token prediction lacks state information
- **REPL traces** as the solution: code + explicit state reveals
- Controllable difficulty: group size, reveal spacing, sequence length
- This is the "bridge" between theory and practice

### 4. Experimental Findings
- **Finding 1**: Transformers collapse with sparse reveals
  - Qwen3-0.6B finetuning results
  - NTP vs State Reveal Supervision (SRS)
  
- **Finding 2**: DeltaNet[-1,1] extrapolates where transformers fail
  - 280M parameter comparison
  - Training from scratch with curriculum
  - Clean separation by architecture
  
- **Finding 3**: Interpretability confirms theory
  - Layer 12, Head 3 = the state-tracking head
  - β values consistently at 2
  - Ablation destroys capability

### 5. Real Code Challenges
- **Probabilistic transitions**: `random.choice()`, hidden inputs
  - PFSA-SR formalism
  - Theorem: Linear RNNs fail for probabilistic tracking
  
- **Tokenization discontinuity**: String manipulation nightmare
  - "alphabet" → 1 token, but edit one char → 5+ tokens
  - Cascading state update challenges

### 6. Implications for Code World Models
- **What current CWMs do**: Dense reveals, token-expensive
- **Where they fail**: Sparse reveals, non-determinism, strings
- **The path forward**:
  1. Hybrid architectures (transformer + linear RNN)
  2. State-aware training data (LeetCode traces)
  3. Non-linear RNNs for probabilistic code
  4. Stable tokenization for string operations

### 7. Conclusion
- **Core message**: Expressivity ≠ Learnability
- Architectures need matching data formats
- Future CWMs: hybrids + right training data

---

## Key Figures Needed

1. **Shell game → REPL trace** visualization (from paper Fig 1)
2. **NTP vs SRS accuracy** across reveal spacings (Fig in paper)
3. **Architecture comparison**: DeltaNet[-1,1] vs Transformer extrapolation
4. **Interpretability**: β distribution, intervention analysis
5. **Tokenization discontinuity** diagram
6. (Optional) LeetCode trace example

---

## Tone & Audience

- **Primary audience**: ML researchers, especially those working on code models
- **Secondary**: Practitioners building code agents/tools
- **Tone**: Technical but accessible, building intuition before formalism
- **Length**: ~15 min read (3000-4000 words)

---

## Content to Add Later

- [ ] Actual figures from paper
- [ ] Interactive demo (REPL trace generator?)
- [ ] Code snippets for reproducing key experiments
- [ ] Links to paper, code, data
- [ ] Author information
