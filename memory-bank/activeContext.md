# Active Context: PhD Research Exploration

## Current Work Focus

The research is in its **early exploratory phase** following the first three supervision meetings (13 May, 22 May, 10 June 2026). The primary focus is establishing the mathematical foundations and conducting a state-of-the-art literature review.

### Active Tasks

1. **Create Overleaf PSD Document**
   - Title: "PSD Dean's PSD Plan"
   - Structure: Separate LaTeX pages for tentative plan, ideas, progress, and meeting notes
   - Purpose: Central document for tracking research progress and discussions

2. **State-of-the-Art Literature Review**
   - **Primary focus:** Application of Grassmannian/Riemannian manifolds to friction cones, sliding, and related robotics topics
   - **Secondary focus:** Koopman operators and data-driven methods for nonlinear dynamics in locomotion
   - **Specific paper to review:** Flow matching paper shared by Dr. Hozefa
   - **Tools:** NotebookLM, ChatGPT, Claude for exploring research gaps

3. **Mathematical Framework Development**
   - Understand Grassmannian manifold projections for multi-contact friction modeling
   - Establish connection between friction cones (Riemannian manifolds) and Grassmannian representation
   - Investigate how different joint configurations and motion phases map to manifold points

4. **Share Prior Work**
   - Send ICRA paper and master's thesis links to Fares and Hozefa
   - These documents are the foundation for extending to multi-legged robots

## Recent Changes

### 10 June 2026 — Third Supervision Meeting
- **Key Discussion:**
  - Fares made contact with DLR Germany space robotics specialist — potential October/November talk
  - Systems engineering integration using NASA handbook discussed
  - Edge-to-cloud computing with Spot robot proposed
  - Hozefa confirmed feasibility of research direction
  - Flow matching paper relevance discussed
- **New Assignments:**
  - Create Overleaf PSD document with structure: tentative plan, ideas, progress
  - Investigate Koopman operators and EDMD for nonlinear dynamics
  - Review flow matching paper
  - Explore co-supervision possibilities (identify needs first)
  - Use NYU email/chat for communications

### 22 May 2026 — Second Supervision Meeting
- **Key Discussion:**
  - Dean presented master's work (friction cone computation using optimization)
  - Grassmannian manifolds proposed to reduce complexity for multi-legged robots
  - Hozefa: friction cones are already Riemannian manifolds → natural connection to Grassmannian
  - Concept: contact points as projections on Grassmannian manifold
  - Fares: friction represents a projection; Grassmannian captures solution space curvature
- **New Assignments:**
  - Search literature for Grassmannian/Riemannian manifold applications to friction
  - Use AI tools for research gap exploration
  - Send ICRA paper and thesis to Fares and Hozefa
  - Weekly meetings (30 min from next week)

### 13 May 2026 — First Supervision Meeting
- **Introduction:** Dean joining NYU PhD program (space systems engineering track)
- **Initial direction established:** Extend ICRA paper using Grassmannian/Manifold methods
- **Administrative:** Clearance and transcript complete, awaiting work permit
- **First assignment:** Read assigned papers and prepare summaries

## Active Decisions and Considerations

### Mathematical Approach
- **Decision:** Use Grassmannian manifolds to reduce friction optimization complexity
- **Status:** Theoretical foundation being validated; literature search needed to confirm novelty
- **Risks:** May not be novel (requires thorough state-of-the-art review); Hozefa noted this is genuinely exploratory

### Research Directions
- **Primary:** Grassmannian/Riemannian manifolds for friction modeling
- **Secondary:** Koopman operators for dynamic linearization
- **Tertiary:** Force flow dynamics, higher-order differential equations
- **Framework:** Systems engineering integration (NASA handbook)

### Tool Selection
- **Simulation:** Google Colab (existing workflow from master's)
- **AI Assistance:** NotebookLM (audio overviews, summaries), ChatGPT, Claude, DeepSeek
- **Document Management:** Overleaf (LaTeX), NYU email/chat
- **Note:** Fares noted DeepSeek has superior niche search but reliability issues

## Important Patterns and Preferences

### Communication
- Use NYU email/chat for future communications with Fares
- Weekly 30-minute meetings (ongoing)
- Zoom meeting minutes sent by Fares after meetings

### Documentation
- LaTeX-based project management (Overleaf)
- Meeting summaries documented in LaTeX
- Literature review using AI tools for summarization and gap identification

### Technical Approach
- Optimization method: epsilon relaxation for trajectory optimization
- Solver: unspecified (to be determined — Hozefa asked in 22 May meeting)
- Model: classic trajectory optimization (not MPC) — optimizes entire rest-to-steady-state trajectory

## Learnings and Project Insights

### Technical Insights
1. **Maximum dissipation principle** provides more accurate cone modeling than pyramidal approximation
2. **Monopod feasibility** demonstrated; **biped** implemented (18,000 epochs × 6 hours — computationally expensive)
3. **Transient motion phases** are highly nonlinear and difficult to compute — this is where the method provides value
4. **Sliding mass model** captures velocity of center of gravity — produces trajectories similar to normal sliding box on frictional surface
5. **Epsilon relaxation** method iteratively tightens solution space from large error margin to feasible solution

### Collaboration Insights
- Hozefa brings Grassmannian manifold expertise and confirms feasibility
- Fares exploring DLR Germany collaboration for space robotics specialization
- Co-supervision should complement, not conflict, with main supervisor
- Industry applications important — need to create own industrial scenarios

## Next Immediate Steps (Priority Order)
1. **HIGH:** Create Overleaf PSD document with proposed structure
2. **HIGH:** Complete literature review on Grassmannian manifolds for friction cones
3. **HIGH:** Review flow matching paper from Hozefa
4. **MEDIUM:** Send ICRA paper and thesis links to supervisors
5. **MEDIUM:** Investigate Koopman operators/EDMD for the system
6. **LOW:** Explore co-supervision options
7. **LOW:** Begin coordinating lab space/desk arrangements for August arrival