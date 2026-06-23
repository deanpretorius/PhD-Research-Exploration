# System Patterns: PhD Research Exploration

## Research Architecture

The PhD research follows a multi-layered architecture connecting mathematical foundations, computational methods, and experimental validation.

### Layer 1: Mathematical Foundation
```
Riemannian Manifolds (Friction Cones)
        ↓
Grassmannian Manifolds (Contact Configuration Space)
        ↓
Subspace Projections (Dimensionality Reduction)
        ↓
Optimization on Manifolds
```

### Layer 2: Computational Methods
```
Maximum Dissipation Principle
        ↓
Friction Cone Modeling (3D)
        ↓
Trajectory Optimization (Epsilon Relaxation)
        ↓
Multi-Contact Optimization (Grassmannian-reduced)
```

### Layer 3: Validation Pipeline
```
Simulation (Google Colab)
        ↓
Single Robot Validation
        ↓
Multi-Legged Robot Testing
        ↓
Real-World Deployment
```

## Key Technical Decisions

### Decision 1: Grassmannian Manifolds for Friction Modeling
**Context:** Traditional friction cone computation treats each contact point independently, leading to exponential complexity growth with additional legs.
**Decision:** Represent multi-contact configurations as points on a Grassmannian manifold Gr(k,n), where k-dimensional subspaces capture the essential structure of the friction problem.
**Consequence:** Reduces dimensionality of the optimization problem, enabling real-time computation for multi-legged robots.

### Decision 2: Maximum Dissipation Principle
**Context:** Pyramidal approximations of friction cones sacrifice accuracy for computational efficiency.
**Decision:** Use the maximum dissipation principle for more accurate cone modeling.
**Consequence:** More computationally expensive but provides physically accurate friction modeling — the trade-off is managed by Grassmannian dimensionality reduction.

### Decision 3: Epsilon Relaxation for Trajectory Optimization
**Context:** Full trajectory optimization from rest to steady state is a complex non-linear problem with local minima issues.
**Decision:** Use epsilon relaxation method — start with large error margin and iteratively tighten to find feasible solutions.
**Consequence:** Provides robust convergence but requires careful parameter tuning (6 hours per simulation for biped).

### Decision 4: Classical Trajectory Optimization over MPC
**Context:** Need to optimize full motion lifecycle, not just receding horizon.
**Decision:** Use classical trajectory optimization (entire rest-to-steady-state trajectory) rather than Model Predictive Control.
**Consequence:** More computationally intensive per run but provides global optimality guarantees and avoids MPC's horizon limitations.

## Component Relationships

### Research Direction Dependency Graph
```
Grassmannian/Riemannian Manifolds (Active)
    ├── Foundation: Friction Cone Optimization (master's work)
    ├── Method: Subspace projection for multi-contact reduction
    └── Validation: Simulation → Real robot

Koopman Operators (Exploratory)
    ├── Connection: Linearization of nonlinear locomotion dynamics
    ├── Method: Data-driven EDMD
    └── Validation: Flow matching paper comparison

Force Flow Dynamics (Exploratory)
    └── Connection: Force propagation in multi-legged systems

Systems Engineering (Framework)
    ├── NASA Systems Engineering Handbook
    ├── Requirements gathering
    ├── Use case analysis
    └── Stakeholder management
```

### Meeting Structure Pattern
```
Bi-weekly → Weekly (30 min) supervision meetings
├── Progress review
├── Technical discussion
├── New assignments
└── Next steps alignment
```

## Critical Implementation Paths

### Path 1: Literature Review → Novelty Confirmation
```
1. Search existing work on Grassmannian/Riemannian manifolds for friction
2. Use AI tools (NotebookLM, ChatGPT, Claude) for gap analysis
3. Document findings in Overleaf PSD document
4. Present findings to supervisory team
5. Confirm novelty or pivot direction
```

### Path 2: Mathematical Framework Development
```
1. Understand Grassmannian manifold projections
2. Map friction cones → Riemannian manifolds → Grassmannian representation
3. Formulate optimization problem on manifold
4. Derive dimensionality reduction bounds
5. Implement in simulation
```

### Path 3: Validation Pipeline
```
1. Simulation (Google Colab)
2. Single robot testing (monopod/biped from master's)
3. Multi-legged robot extension (hexapod/octopod)
4. Real robot validation (Spot robot)
5. Demo video creation
```

## Design Patterns in Use

### 1. PhD Exploration Pattern
- **Idea → Literature → Validation → Integration**
- Each research direction (manifolds, Koopman, force flow) follows this pattern independently
- Periodic convergence checks ensure directions remain aligned

### 2. Systems Engineering Integration Pattern
- **Requirements → Use Cases → Architecture → Implementation → Validation**
- NASA Systems Engineering Handbook provides structured process
- Applied to both research methodology and robot system design

### 3. Tool-Assisted Research Pattern
- **AI tools (NotebookLM, Claude, ChatGPT) → Gap identification → Human validation**
- Combines AI's broad search capabilities with human expertise
- NotebookLM specifically used for paper summarization and audio overviews

## Key Architectural Constraints

1. **Computational budget:** 18,000 epochs × 6 hours baseline — Grassmannian reduction must significantly improve this
2. **Physical validation:** Real robot testing required alongside simulation (insufficient alone)
3. **Industry relevance:** Must demonstrate real-world applicability beyond theoretical results
4. **Novelty requirement:** Grassmannian approach to friction must not be previously published — Hozefa noted this is exploratory with unknown existing work