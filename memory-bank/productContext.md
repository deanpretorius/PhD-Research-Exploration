# Product Context: PhD Research Exploration

## Why This Research Exists

The PhD research addresses a fundamental challenge in robotic locomotion: **computing and modeling friction dynamics for multi-legged robots is computationally intractable using conventional methods.**

### The Problem
- Traditional friction cone modeling uses pyramidal approximations that sacrifice accuracy for tractability
- The maximum dissipation principle provides more accurate cone modeling but is computationally expensive (18,000 epochs × 6 hours for biped simulations)
- Extending to multi-legged robots (hexapods, octopods) exacerbates this computational challenge exponentially as the number of contact points increases
- Current approaches treat each contact point independently, missing the geometric structure inherent in the problem
- **Verified Gap (23 June 2026):** Existing Grassmann/Grassmannian contact work is mostly geometric, static, grasping, or singularity-oriented. Existing Koopman contact work is dynamic and data-driven but does not handle friction cone/wrench cone computation. The open gap is using Grassmannian/contact-wrench geometry to reduce or structure **dynamic multi-contact friction optimization for locomotion**.

### Why It Matters
- Space robotics requires reliable locomotion in uncertain, unstructured environments
- Sensorless friction estimation reduces hardware complexity and failure points
- Real-time control demands computationally efficient solutions
- Industry applications include mining robotics, search-and-rescue, and planetary exploration

## How It Should Work

### The Mathematical Bridge
The core insight connecting friction cones to Grassmannian manifolds:
1. **Friction cones are Riemannian manifolds** — they have inherent geometric structure
2. **Multi-legged contact configurations can be represented as points on a Grassmannian manifold** — the Grassmannian Gr(k,n) represents all k-dimensional subspaces of an n-dimensional space
3. **Each joint configuration and motion phase creates different manifolds** that can be projected as points on the Grassmannian
4. **The Grassmannian captures the solution space curvature**, reducing the dimensionality of the optimization problem

### Research Pipeline
1. **Foundation:** Dean's existing master's work (friction cone computation using optimization on monopod/biped)
2. **Extension:** Apply Grassmannian methods to reduce problem complexity for multi-legged robots
3. **Validation:** Simulation in Google Colab → Real robot testing (Spot robot or similar)
4. **Demonstration:** Create compelling demo videos showcasing research findings

## User Experience Goals

### For the Research Community
- Publish novel methodology for friction computation using differential geometry
- Provide open-source implementations (ICRA paper, thesis as starting points)
- Demonstrate clear performance improvements (computational speed, accuracy)

### For Industry
- Enable real-time friction-aware locomotion control
- Reduce hardware requirements through sensorless estimation
- Provide integration pathways for existing robotic platforms

### For the PhD Committee
- Clear contribution narrative bridging systems engineering and mathematics
- Reproducible results with documented experimental setup
- Strong demonstration of novelty and impact

## Key Technical Decisions

### Why Grassmannian Manifolds? **(Refined Gap — Dynamic vs. Static)**
- Hozefa suggested friction cones are already Riemannian manifolds → natural connection
- Grassmannian manifolds reduce dimensionality by projecting multiple contact spaces into unified subspace representation
- **Verified gap:** Grassmann geometry has been used for contact (El-Khoury, ponce.4finger) — but only for **static** force-closure and grasping, not **dynamic** friction optimization for locomotion
- The novelty is not that Grassmann has been used near contact, but that it hasn't been applied to **dynamic friction cone computation from a friction-dynamics perspective**
- Enables generalization across different robot configurations (monopod → biped → hexapod → octopod)

### Why Koopman Operators? **(Gap Confirmed)**
- **Verified Gap:** No existing work uses Koopman operators to compute friction cones or contact wrench cones
- Koopman + Contact Dynamics exists (O'Neill 2025, Kim 2024) but models whole-body dynamics, not cone computation
- Friction/wrench cone computation exists (Caron 2015/2016, Orsolino 2017) but uses geometric/convex methods
- **The opportunity:** Bringing Koopman's data-driven linearization to friction cone computation is novel
- **Caveat:** Zhang & Zuazua (2022) show Koopman methods converge slowly (m^{-1/2}) — careful lifting function design is critical

### Combined Grassmannian-Koopman Framework
- Schurig et al. (2025) demonstrate Koopman+Grassmannian compatibility (for dictionary learning) — validates mathematical feasibility
- **Verified gap:** No existing work combines Grassmannian spatial reduction with Koopman-based friction dynamics for locomotion
- Grassmannian handles spatial/geometric structure of contact configurations (static/structural)
- Koopman handles temporal/dynamic evolution of friction states (dynamic/data-driven)
- Potential for real-time friction-aware control for multi-legged robots

### Why Systems Engineering Integration?
- NASA Systems Engineering Handbook provides structured framework for requirements management
- Industry background (CSIR, mining robotics projects) gives practical grounding
- Distinguishes the PhD from purely theoretical work

## Relationships and Dependencies

| Direction | Relationship | Dependencies |
|-----------|-------------|--------------|
| Friction cones | Foundation | Dean's master's thesis, ICRA paper |
| Riemannian manifolds | Mathematical base | Differential geometry literature |
| Grassmannian manifolds | Novel application | State-of-the-art review needed |
| Koopman operators | Complementary approach | Flow matching paper, EDMD literature |
| Systems engineering | Framework | NASA Systems Engineering Handbook |
| Simulation/validation | Experimental | Google Colab, Spot robot access |

## Current State
The research is in **early exploratory phase**. The core mathematical insight (friction cones as Riemannian manifolds → Grassmannian representation) has been identified and validated by the supervisory team. Active work includes literature review, state-of-the-art analysis, and PSD document creation.