# Research Synthesis: Paper Analysis and Prospective Directions

## Papers Analyzed and Key Insights

### 1. Dean's ICRA Paper (2021) — "A novel method for computing the 3D friction cone using complimentary constraints"
- **Source:** Stellenbosch University, ICRA 2021
- **Key Contribution:** Novel friction cone modeling using Maximum Dissipation Principle — samples cone along vector opposing relative velocity (polar representation)
- **Results:** 39.13% faster compute, 57% fewer inequality constraints vs. 4-sided polyhedral approximation
- **Technical Stack:** Pyomo + IPOPT solver, Google Colab, monopod robot model
- **Future Work (stated):** Implement on multi-legged bipedal and quadrupedal robots
- **Relevance:** This IS the foundational work. The natural extension → Grassmannian manifolds for multi-legged scaling

### 2. "A quantitative analysis of Koopman operator methods" — Zhang & Zuazua (2022)
- **Key Finding:** gEDMD with finite elements converges slowly (m^{-1/2}). For 1D problems, direct interpolation outperforms Koopman methods
- **Critical Caveat:** "Even in favorable settings, approximation error decreases relatively slowly"
- **Relevance to Dean's work:**
  - Validates that Koopman methods have limitations — important to know
  - Suggests that if Koopman is used, careful choice of dictionary/lifting functions is critical
  - The paper focuses on theoretical guarantees, not practical robotics applications

### 3. "Learning Koopman Dynamics for Safe Legged Locomotion" — Kim et al. (2024)
- **Key Approach:** DMD to learn linear dynamics of a locomotion policy → MPC for safe navigation
- **Surprising Finding:** Simple Unified Linear Dynamics (no lifting) performs nearly as well as polynomial lifting for MPC-based navigation
- **Best Performance:** Time-Delay Embedding (TD(30)) significantly improves prediction accuracy
- **Platform:** Unitree Aliengo robot in IsaacGym simulator
- **Relevance:**
  - Directly applicable: Koopman + MPC for legged locomotion is proven effective
  - Simple linear models may be sufficient for high-level planning
  - Time-delay embedding is a promising lifting technique

### 4. "On Computing Robust N-Finger Force-Closure Grasps of 3D Objects" — El-Khoury & Sahbani
- **Key Theoretical Result:** Uses Grassmann algebra and Plücker coordinates to prove wrenches from 3 non-aligned contact points form a 6D basis
- **Method:** Sufficient (but not necessary) force-closure test that is computationally efficient
- **CRITICAL RELEVANCE:** Directly uses Grassmann algebra for friction/grasping problems — this is the closest existing work to Dean's proposed direction
- **Key Insight from paper:** "Grassmann studied manifold of lines which rank ranges varies from 0 to 6" — connects Grassmannian geometry to 6D wrench space
- **Quality Criterion:** Volume of hypertetrahedron in 6D wrench space as grasp quality measure

### 5. "Framework Comparison Between a Multifingered Hand and a Parallel Manipulator" — Borràs & Dollar (2013)
- **Key Result:** Proven equivalence between grasp matrix (hand) and parallel manipulator Jacobian using screw theory
- **Key Insight:** The choice of reciprocal screws in parallel manipulator framework corresponds to choice of contact frame vectors in grasping framework
- **Relevance:** Shows that knowledge from parallel manipulator literature (singularity analysis, workspace optimization) can transfer to grasping
- **Future Work (stated):** General proof of equivalence left as future work

### 6. "Systems Engineering-Reengineered: The Fourth Wave" — Gibson et al.
- **Core Message:** Systems Engineering is an interdisciplinary field at the nexus of systems sciences and engineering
- **Key Framework:** T-shaped model — depth in engineering competencies + breadth in Systems Thinking competencies (DSRP: Distinction, Systems, Relationship, Perspective)
- **iPhone Case Study:** Three principles — (1) design first, engineer second; (2) insist on holistic design; (3) leadership matters
- **Relevance:** Provides the systems engineering framework Dean wants to integrate

### 7. "A Deep Convolutional Neural Network Architecture for Image Classification" — W.L. Pretorius (2020)
- **Note:** This is by W.L. Pretorius (likely a relative), not Dean Pretorius
- **Content:** Master's thesis on CNN architectures for image classification — covers LeNet, AlexNet, VGGNet, GoogLeNet, ResNet
- **Relevance to Dean's work:** Tangential — may be useful if Dean incorporates vision/perception in his robotics work

### 8. "Pre-Impact Detection Algorithm to Identify Tripping Events Using Wearable Sensors" — Aprigliano et al. (2019)
- **Content:** Fall detection using IMUs and adaptive oscillators
- **Relevance to Dean's work:** Tangential — relates to locomotion and perturbation detection

---

## Prospective Research Directions

### Direction 1: Grassmannian Manifolds for Multi-Contact Friction Optimization **(PRIMARY)**

**Core Idea:** Extend Dean's ICRA friction cone method from monopod/biped to multi-legged robots (hexapod/octopod) by representing multi-contact configurations as points on a Grassmannian manifold.

**Why it works (from papers):**
- El-Khoury & Sahbani proved wrenches from 3 non-aligned contact points form a 6D basis using Grassmann algebra
- Borràs & Dollar showed equivalence between grasp matrix and parallel manipulator Jacobian — enabling knowledge transfer
- Friction cones themselves are Riemannian manifolds (confirmed by Hozefa)

**Key Research Questions:**
1. How can Grassmannian manifolds be used to reduce the dimensionality of multi-contact friction optimization?
2. What is the optimal mapping from contact configuration space to Grassmannian representation?
3. Can the Grassmannian capture the essential structure of friction dynamics across different gaits and terrains?
4. How does the computational complexity scale with number of legs using Grassmannian reduction vs. traditional methods?

**Novelty Assessment:**
- El-Khoury & Sahbani used Grassmann algebra for force-closure testing (static)
- Dean's proposed direction extends this to dynamic friction optimization (novel)
- Borràs & Dollar's framework equivalence suggests cross-pollination opportunities
- **Gap:** No existing work applies Grassmannian manifolds to dynamic friction cone optimization in trajectory optimization

### Direction 2: Koopman Operators for Friction Dynamics Linearization **(SECONDARY)**

**Core Idea:** Use Koopman operator theory (with DMD/EDMD) to linearize the nonlinear friction dynamics in legged locomotion, enabling real-time control.

**Why it might work:**
- Kim et al. (2024) demonstrated Koopman + MPC for safe legged navigation
- Simple linear models (Unified Linear Dynamics) can capture high-level locomotion dynamics
- Time-delay embedding significantly improves prediction accuracy

**Key Research Questions:**
1. Can Koopman operators capture the nonlinear friction dynamics during transient phases of locomotion?
2. What lifting functions are most effective for friction dynamics (polynomials, time-delay, neural network-based)?
3. How does Koopman-based linearization compare to Grassmannian reduction for friction computation?
4. Can the two approaches be combined — Grassmannian for spatial reduction, Koopman for temporal linearization?

**Caveats (from Zhang & Zuazua):**
- Koopman methods converge slowly (m^{-1/2})
- Direct methods may outperform Koopman for low-dimensional problems
- Careful choice of dictionary/lifting functions is critical

### Direction 3: Combined Grassmannian-Koopman Framework **(INNOVATIVE)**

**Core Idea:** Integrate both approaches — use Grassmannian manifolds to reduce the spatial dimensionality of multi-contact friction, then use Koopman operators to linearize the reduced dynamics.

**Why this could be novel:**
- No existing work combines Grassmannian spatial reduction with Koopman temporal linearization
- The two approaches address complementary aspects of the problem
- Could enable real-time friction-aware control for multi-legged robots

**Key Research Questions:**
1. How do Grassmannian projections interact with Koopman lifting functions?
2. What is the end-to-end computational advantage of the combined framework?
3. Can the combined approach enable provable safety guarantees (control barrier functions)?

### Direction 4: Systems Engineering Framework for Locomotion System Design **(FRAMEWORK)**

**Core Idea:** Apply NASA Systems Engineering Handbook and the T-shaped competency model (Gibson et al.) to structure the PhD research as a systems engineering problem.

**Key Research Questions:**
1. How can Systems Engineering methodologies improve the design cycle for legged locomotion controllers?
2. What are the stakeholder requirements for a space robotics locomotion system?
3. Can the DSRP (Distinction, Systems, Relationship, Perspective) framework be applied to locomotion system architecture?

### Direction 5: Grasping-Locomotion Unified Theory **(EXPLORATORY)**

**Core Idea:** Leverage the proven equivalence between grasping and parallel manipulator frameworks (Borràs & Dollar) to develop a unified theory for contact-rich manipulation and locomotion.

**Key Research Questions:**
1. Can insights from force-closure grasping (El-Khoury & Sahbani) be transferred to locomotion contact planning?
2. What is the role of Grassmannian geometry in unifying grasping and locomotion frameworks?
3. Can the 6D wrench space analysis from grasping be applied to multi-legged locomotion stability?

---

## Prioritized Research Questions for the PhD

### High Priority (Core Contribution)

1. **RQ1:** Can Grassmannian manifolds reduce the computational complexity of multi-contact friction optimization from exponential to polynomial in the number of legs?
2. **RQ2:** What is the optimal mathematical mapping from friction cones (Riemannian manifolds) to Grassmannian subspaces for legged locomotion?
3. **RQ3:** How does the Grassmannian-reduced friction model generalize across different robot morphologies (biped → quadruped → hexapod → octopod)?

### Medium Priority (Complementary Contributions)

4. **RQ4:** Can Koopman operators provide real-time linear approximations of the Grassmannian-reduced friction dynamics for MPC-based control?
5. **RQ5:** What is the minimum sensor configuration (IMU placement) needed to estimate friction states using the combined framework?
6. **RQ6:** How does the Systems Engineering framework (NASA handbook, DSRP) improve the research-to-deployment pipeline for locomotion controllers?

### Low Priority (Future Exploration)

7. **RQ7:** Can the grasping-locomotion unified theory (leveraging Borràs & Dollar equivalence) enable new insights into contact stability?
8. **RQ8:** How do environmental uncertainties (terrain variation, surface properties) affect the Grassmannian representation of friction?

---

## Gaps Identified from Literature

1. **No existing work** applies Grassmannian manifolds to dynamic friction cone optimization in trajectory optimization (El-Khoury focused on static force-closure)
2. **No existing work** combines Grassmannian spatial reduction with Koopman temporal linearization for robotics
3. **Borràs & Dollar's equivalence** between grasping and parallel manipulators has not been extended to locomotion
4. **The convergence limitations** of Koopman methods (Zhang & Zuazua) have not been addressed for friction dynamics specifically
5. **Dean's ICRA paper** explicitly calls for extension to multi-legged robots — this is the stated future work