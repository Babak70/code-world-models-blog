# Blog Post Outline: Debugging Code World Models

## Story Arc

**Hook**: Code World Models promise faithful code execution by predicting explicit runtime state—but their limitations are not obvious from aggregate benchmark scores.

**Conflict**: CWMs look strong on many tasks, yet fail systematically in two regimes: token-budget exhaustion from long traces and brittleness in string-valued state.

**Resolution**: Debugging CWMs requires separating two questions: (i) local semantic execution (do they apply operations correctly?) and (ii) long-horizon state tracking (do they propagate state over many steps?).

**Implications**: Future work needs more efficient supervision and state representations aligned with program execution and data types (especially strings).

---

## Detailed Structure

### 1. Introduction: What CWMs Are
- Action + state traces as a “world model” interface
- Why this differs from standard LMs
- Two evaluation lenses: local semantic execution vs long-horizon state tracking

### 2. Real-Code Benchmarks: Where Errors Cluster
- CruxEval-O + HumanEval failure breakdown
- Regime 1: token-budget exhaustion (truncation from long traces)
- Regime 2: string-valued state brittleness

### 3. Controlled Compositionality: Composition Across Data Types
- Controlled “composition zoo” shows composition is reliable for non-string data
- String compositions degrade sharply with depth
- Takeaway: composition depth is not the bottleneck; string representation is

### 4. Tokenization Discontinuity: Mechanism
- Context-dependent token IDs: separators/patterns can vanish as tokens in context
- Why this breaks deterministic string methods (e.g., find/split)

### 5. Long-Horizon State Tracking: Permutation Tracking
- Baseline long-horizon degradation
- Key diagnosis: action hallucination dominates errors
- Teacher forcing isolates state propagation and recovers long-horizon accuracy

### 6. Interventions (Optional but Useful)
- Expression decomposition: expose hidden intermediates (recovers a subset)
- String decomposition: can help but risks token explosion

### 7. Conclusion
- Two dominant failure regimes: token budget + string brittleness
- What teacher forcing reveals about state propagation
- Directions: more efficient supervision + better string/state representations

---

## Key Figures Needed

1. $S_5$ permutation tracking: baseline vs teacher forcing
2. Composition across data types: non-string vs string degradation
3. Tokenization discontinuity: context-dependent token IDs example
4. Failure taxonomy: truncation + string-heavy errors

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
