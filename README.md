
## GeneticQLoRA: The Theory

### 1. Foundations

* **Population starts with 3 individuals**.
* Each individual is represented as a compressed parameter vector (inspired by QLoRA: quantized, low-rank adaptation).
* The system evolves through cycles of **reproduction, mutation, and death**.

---

### 2. Core Rules

1. **Initialization**:

   $$
   P^{(0)} = \{x_1, x_2, x_3\}
   $$

2. **Reproduction**: Children are formed by mixing parent vectors with random weights and applying noise:

   $$
   c' = \alpha x_a + (1-\alpha)x_b + \epsilon
   $$

   where $\epsilon \sim \mathcal{N}(0, \sigma^2)$.

3. **Selection**: A fitness function $F(x)$ evaluates children. Survivors are chosen as the new population.

4. **Death**: Parents are completely replaced by children.

   $$
   P^{(t+1)} = \text{Children}(P^{(t)})
   $$

---

### 3. Dynamics

* **No overlap generations**: Unlike many evolutionary models, no parent survives. This enforces **total renewal**.
* **Minimal seeding**: Starting from just 3 ensures diversity is forced to grow only through mutation and recombination.
* **QLoRA inspiration**: By treating individuals as low-rank parameter adapters, the system keeps memory small and generations fast.

---

### 4. Implications

* The theory is **a generational genetic algorithm with full replacement**, tailored for **parameter-efficient model evolution**.
* It can simulate evolution, optimization, or even cultural/knowledge inheritance under strict turnover conditions.
* Unlike classic genetic algorithms, it emphasizes *compression and quantization noise* as essential to mutation.

