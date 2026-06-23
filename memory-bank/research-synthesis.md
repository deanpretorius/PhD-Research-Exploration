# Research Synthesis: Paper Analysis and Prospective Directions

## Papers Analyzed and Key Insights

### 1. Dean's ICRA Paper (2021) — "A novel method for computing the 3D friction cone using complimentary constraints"
- **Source:** Stellenbosch University, ICRA 2021
- **Key Contribution:** Novel friction cone modeling using Maximum Dissipation Principle — samples cone along vector opposing relative velocity (polar representation)
- **Results:** 39.13% faster compute, 57% fewer inequality constraints vs. 4-sided polyhedral approximation
- **Technical Stack:** Pyomo + IPOPT solver, Google Colab, monopod robot model
- **Future Work (stated):** Implement on multi-legged bipedal and quadrupedal robots
- **Relevance:** Foundational work. Natural extension paths: (a) Grassmannian manifolds for multi-legged scaling, (b) Koopman operators for friction cone linearization

### 2. "A quantitative analysis of Koopman operator methods" — Zhang & Zuazua (2022)
- **Key Finding:** gEDMD with finite elements converges slowly (m^{-1/2}). For 1D problems, direct interpolation outperforms Koopman methods
- **Critical Caveat:** "Even in favorable settings, approximation error decreases relatively slow"
- **Relevance to Dean's work:**
  - Validates that Koopman methods have limitations — important to know
  - Suggests that if Koopman is used, careful choice of dictionary/lifting functions is critical
  - Focuses on theoretical guarantees, not practical robotics applications

### 3. "Learning Koopman Dynamics for Safe Legged Locomotion" — Kim et al. (2024)
- **Key Approach:** DMD to learn linear dynamics of a locomotion policy → MPC for safe navigation
- **Surprising Finding:** Simple Unified Linear Dynamics (no lifting) performs nearly as well as polynomial lifting for MPC-based navigation
- **Best Performance:** Time-Delay Embedding (TD(30)) significantly improves prediction accuracy
- **Platform:** Unitree Aliengo robot in IsaacGym simulator
- **Relevance:**
  - Koopman + MPC for legged locomotion is proven effective
  - Simple linear models may be sufficient for high-level planning
  - Time-delay embedding is a promising lifting technique
  - **NOT** friction cone computation — this is a gap

### 4. "On Computing Robust N-Finger Force-Closure Grasps of 3D Objects" — El-Khoury & Sahbani
- **Key Theoretical Result:** Uses Grassmann algebra and Plücker coordinates to prove wrenches from 3 non-aligned contact points form a 6D basis
- **Method:** Sufficient (but not necessary) force-closure test that is computationally efficient
- **CRITICAL RELEVANCE:** Directly uses Grassmann algebra for friction/grasping problems — closest existing work to Dean's Grassmannian direction
- **Key Insight:** "Grassmann studied manifold of lines which rank ranges varies from 0 to 6" — connects Grassmannian geometry to 6D wrench space
- **Quality Criterion:** Volume of hypertetrahedron in 6D wrench space as grasp quality measure
- **NOTE:** This is static force-closure, not dynamic friction optimization

### 5. "Framework Comparison Between a Multifingered Hand and a Parallel Manipulator" — Borràs & Dollar (2013)
- **Key Result:** Proven equivalence between grasp matrix (hand) and parallel manipulator Jacobian using screw theory
- **Key Insight:** The choice of reciprocal screws in parallel manipulator framework corresponds to choice of contact frame vectors in grasping framework
- **Relevance:** Shows knowledge transfer from parallel manipulator literature (singularity analysis, workspace optimization) to grasping
- **Future Work (stated):** General proof of equivalence left as future work

### 6. "Systems Engineering-Reengineered: The Fourth Wave" — Gibson et al.
- **Core Message:** Systems Engineering is an interdisciplinary field at the nexus of systems sciences and engineering
- **Key Framework:** T-shaped model — depth in engineering competencies + breadth in Systems Thinking competencies (DSRP: Distinction, Systems, Relationship, Perspective)
- **iPhone Case Study:** Three principles — (1) design first, engineer second; (2) insist on holistic design; (3) leadership matters
- **Relevance:** Provides the systems engineering framework Dean wants to integrate

### 7. "A Deep Convolutional Neural Network Architecture for Image Classification" — W.L. Pretorius (2020)
- **Note:** This is by W.L. Pretorius (likely a relative), not Dean Pretorius
- **Content:** Master's thesis on CNN architectures for image classification
- **Relevance:** Tangential — may be useful if Dean incorporates vision/perception in robotics work

### 8. "Pre-Impact Detection Algorithm to Identify Tripping Events Using Wearable Sensors" — Aprigliano et al. (2019)
- **Content:** Fall detection using IMUs and adaptive oscillators
- **Relevance:** Tangential — relates to locomotion and perturbation detection

---

## VERIFIED RESEARCH GAP

A focused verification scan across both the local PDF library and external literature found **no clear evidence** that anyone is using a Koopman operator to compute a friction cone, friction wrench, contact wrench cone, grasp wrench space, or force-closure wrench set directly.

### The Clean Split:

| Domain | What Exists | What's Missing |
|--------|-------------|----------------|
| **Koopman + Contact Dynamics** | O'Neill et al. (2025) — Koopman global linearization for contact-rich locomotion/manipulation; Kim et al. (2024) — Koopman/DMD for safe legged locomotion; Li et al. (2024) — Koopman dynamics for high-dimensional legged robots. These model contact-rich dynamics but do **not** compute friction/wrench cones. | **No friction cone / wrench cone computation via Koopman** |
| **Friction/Wrench Cone Computation** | Caron et al. (2015) — closed-form contact wrench cone formulae; Caron & Kheddar (2016) — frictional wrench cone constraints for multi-contact walking; Orsolino et al. (2017) — feasible wrench polytopes for legged robots. These compute feasible force/wrench sets geometrically/convexly. | **No Koopman-based methods** |

### Defensible Claim:

> Existing Koopman robotics work models contact-rich dynamics, while existing friction/contact-wrench work computes feasible force or wrench sets geometrically/convexly. I found no direct prior work using Koopman operators to compute friction cones or contact wrench cones.

---

## Prospective Research Directions

### Direction 1: Grassmannian Manifolds for Dynamic Multi-Contact Friction Optimization **(PRIMARY — Refined Gap)**

**Core Idea:** Use Grassmannian/contact-wrench geometry to reduce or structure **dynamic multi-contact friction optimization for locomotion**. The novelty is not that Grassmann has been used near contact (it has), but that it hasn't been applied to **dynamic friction cone computation from a friction-dynamics perspective** — existing work is geometric, static, grasping-oriented.

**Verified Gap (Refined):**
- Grassmann geometry used for: force closure, wrench spaces, screw theory, grasp analysis (El-Khoury, ponce.4finger, Faris 2021) — but **static**
- Grassmannian optimization used for: Koopman dictionary learning (Schurig et al. 2025) — but **not friction dynamics**
- What's missing: Grassmannian manifolds derived from **friction dynamics** for computing **dynamic friction cones/wrench cones for locomotion**

**Key Research Questions:**
1. How can Grassmannian manifolds capture the underlying structure of friction dynamics across transient motion phases?
2. What is the optimal mapping from dynamic friction cone evolution to Grassmannian subspaces?
3. Can the Grassmannian representation reduce multi-contact friction optimization from exponential to polynomial complexity?
4. How does this dynamic Grassmannian approach generalize across robot morphologies (biped → quadruped → hexapod)?

**Novelty Assessment:**
- El-Khoury & Sahbani used Grassmann algebra for force-closure testing (static)
- Schurig et al. used Grassmannian for Koopman dictionary learning (not friction)
- **Gap:** No existing work derives Grassmannian manifolds specifically from friction dynamics for locomotion

### Direction 2: Koopman Operators for Contact-Rich Friction Dynamics **(PRIMARY)**

**Core Idea:** Use Koopman operator theory to learn dynamic models of friction-rich contact in locomotion, leveraging the linear operator framework developed for contact-rich dynamics (O'Neill 2025, Kim 2024) but applied specifically to friction cone evolution rather than whole-body dynamics.

**Key Research Questions:**
1. Can Koopman operators capture the nonlinear evolution of friction cone constraints during dynamic locomotion?
2. What lifting functions are most effective for representing friction dynamics in the Koopman framework?
3. How does Koopman-based friction modeling compare to traditional geometric/convex methods (Caron et al.)?
4. Can a Koopman friction model be embedded in an MPC loop for real-time control?

**Caveat:** Zhang & Zuazua (2022) show Koopman methods converge slowly (m^{-1/2}) — careful lifting function design is critical

### Direction 3: Combined Grassmannian-Koopman Framework **(SYNTHESIS)**

**Core Idea:** Integrate both approaches — use Grassmannian manifolds to reduce the spatial/geometric dimensionality of multi-contact friction, then use Koopman operators to model the reduced friction dynamics temporally.

**Why synergy is viable:**
- Grassmannian handles the spatial/geometric structure of contact configurations (static/structural)
- Koopman handles the temporal/dynamic evolution of friction states (dynamic/data-driven)
- Schurig et al. (2025) already demonstrates a Koopman+Grassmannian connection (for dictionary learning) — this validates the mathematical compatibility
- **No existing work combines Grassmannian spatial reduction with Koopman-based friction dynamics for legged locomotion**

**Key Research Questions:**
1. How do Grassmannian projections on friction dynamics interact with Koopman lifting functions?
2. What is the end-to-end computational advantage of the combined framework?
3. Can the combined approach enable provable safety guarantees (control barrier functions)?

### Direction 4: Systems Engineering Framework for Locomotion System Design **(FRAMEWORK)**

**Core Idea:** Apply NASA Systems Engineering Handbook and the T-shaped competency model (Gibson et al.) to structure the PhD research as a systems engineering problem.

### Direction 5: Grasping-Locomotion Unified Theory **(EXPLORATORY)**

**Core Idea:** Leverage the proven equivalence between grasping and parallel manipulator frameworks (Borràs & Dollar) to develop a unified theory for contact-rich manipulation and locomotion.

---

## Prioritized Research Questions for the PhD

### High Priority (Core Contribution)

1. **RQ1:** Can a Koopman operator learn an accurate model of the friction cone from contact trajectory data, and how does it compare to existing geometric/convex methods (Caron et al., Orsolino et al.) in terms of accuracy and computational cost?
2. **RQ2:** What lifting functions (polynomials, time-delay embeddings, radial basis functions) are most effective for representing friction cone geometry in the Koopman framework?
3. **RQ3:** Can Grassmannian manifolds reduce the computational complexity of multi-contact friction optimization from exponential to polynomial in the number of legs?
4. **RQ4:** How can the Grassmannian-reduced friction model be combined with the Koopman-based friction cone model for a tractable real-time control framework?

### Medium Priority (Complementary Contributions)

5. **RQ5:** Can a Koopman friction cone model be embedded in an MPC loop for real-time multi-contact control?
6. **RQ6:** What is the minimum sensor configuration (IMU placement) needed to estimate friction states using the combined framework?
7. **RQ7:** How does the Systems Engineering framework (NASA handbook, DSRP) improve the research-to-deployment pipeline for locomotion controllers?

### Low Priority (Future Exploration)

8. **RQ8:** Can the grasping-locomotion unified theory (leveraging Borràs & Dollar equivalence) enable new insights into contact stability?
9. **RQ9:** How do environmental uncertainties (terrain variation, surface properties) affect the Grassmannian representation of friction?

---

## Literature Identified but Not Yet in Local Library

From your verification pass:
- O'Neill, Terrones & Asada (2025) — "Koopman global linearization for contact-rich locomotion/manipulation" — arXiv:2511.06515
- Caron, Pham & Nakamura (2015) — "closed-form contact wrench cone formulae" — arXiv:1501.04719
- Caron & Kheddar (2016) — "frictional wrench cone constraints for multi-contact walking" — arXiv:1607.08729
- Orsolino et al. (2017) — "feasible wrench polytopes for legged robots" — arXiv:1712.06833
- Li et al. (2024) — "Koopman dynamics for high-dimensional legged robots" — arXiv:2411.14321

These papers should be added to the local library for further analysis.

---

## Gaps Identified from Literature

### Refined Gap Statement

> Existing Grassmann/Grassmannian contact work is mostly geometric, static, grasping, or singularity-oriented. Existing Koopman contact work is dynamic and data-driven. The open gap is using Grassmannian/contact-wrench geometry to reduce or structure **dynamic multi-contact friction optimization for locomotion**.

### Specific Gaps

1. **Grassmann geometry in contact is static, not dynamic:** Grassmann algebra used for force closure, wrench spaces, screw theory, grasp analysis (El-Khoury, ponce.4finger) — but not for dynamic friction cone computation in locomotion
2. **Koopman + Grassmannian exists but not for friction:** Schurig et al. (2025) connect Koopman and Grassmannian geometry for dictionary learning — but not for friction dynamics or contact wrench cones
3. **No existing work** combines Grassmannian spatial reduction with Koopman-based friction cone computation for legged locomotion
4. **Borràs & Dollar's equivalence** between grasping and parallel manipulators has not been extended to locomotion
5. **Dean's ICRA paper** explicitly calls for extension to multi-legged robots — this is the stated future work
