# Product Context: PhD Research Exploration

## Why This Research Exists

The PhD research addresses a fundamental challenge in robotic locomotion: **computing and modeling friction dynamics for multi-legged robots is computationally intractable using conventional methods.**

### The Problem
- Traditional friction cone modeling uses pyramidal approximations that sacrifice accuracy for tractability
- The maximum dissipation principle provides more accurate cone modeling but is computationally expensive (18,000 epochs × 6 hours for biped simulations)
- Extending to multi-legged robots (hexapods, octopods) exacerbates this computational challenge exponentially as the number of contact points increases
- Current approaches treat each contact point independently, missing the geometric structure inherent in the problem

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

### Why Grassmannian Manifolds?
- Hozefa suggested friction cones are already Riemannian manifolds → natural connection
- Grassmannian manifolds reduce dimensionality by projecting multiple contact spaces into unified subspace representation
- Enables generalization across different robot configurations (monopod → biped → hexapod → octopod)

### Why Koopman Operators?
- Data-driven linearization of nonlinear dynamics complements the geometric approach
- Flow matching techniques from fluid mechanics may transfer to locomotion dynamics
- Provides alternative viewpoint for analyzing transient motion phases

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