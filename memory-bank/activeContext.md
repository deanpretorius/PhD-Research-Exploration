# Active Context: PhD Research Exploration

## Current Work Focus

The research is in its **early exploratory phase** following the first three supervision meetings (13 May, 22 May, 10 June 2026). The primary focus is establishing the mathematical foundations and conducting a state-of-the-art literature review.

### Active Tasks

1. **Overleaf PSD Document (ACTIVE)**
   - This Git repository IS the Overleaf document — synced via GitHub-Overleaf integration
   - Root: `main.tex` with modular `sections/` included via `\input{}`
   - Lesson learned: Section files (research_directions.tex, research_questions.tex, ideas.tex, lit_notes.tex) need substantive content — currently sparse
   - Memory Bank contains rich content ready to populate these sections

2. **State-of-the-Art Literature Review**
   - **Primary focus:** Application of Grassmannian/Riemannian manifolds to friction cones, sliding, and related robotics topics
   - **Secondary focus:** Koopman operators and data-driven methods for nonlinear dynamics in locomotion
   - **Specific papers reviewed:** ForceFlow (2605.11048v1), Krolicki et al. (2022) Koopman quadruped deformable terrain, Shi et al. (2023) Koopman soft robotics survey
   - **Gap verification complete:** Two-pass analysis (Koopman + friction cone, Grassmannian + dynamic friction)
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

### Refined Research Gap (23 June 2026) — Two-Pass Verification

**Pass 1 — Koopman + Friction Cone Gap:**
- Koopman + Contact Dynamics exists (O'Neill 2025, Kim 2024, Li 2024) but models whole-body dynamics, not friction cone computation
- Friction/wrench cone computation exists (Caron 2015/2016, Orsolino 2017) but uses geometric/convex methods, not Koopman
- **No direct prior work uses Koopman operators to compute friction cones or contact wrench cones**

**Pass 2 — Grassmannian + Dynamic Friction Gap:**
- Grassmann geometry used for: force closure, wrench spaces, screw theory, grasp analysis (El-Khoury, ponce.4finger) — but **static**, not dynamic
- Schurig et al. (2025) connect Koopman and Grassmannian for dictionary learning — **not for friction dynamics**
- **No evidence of Grassmannian manifolds derived specifically from friction dynamics for locomotion**

**Stronger PhD Framing:**
> Existing Grassmann/Grassmannian contact work is mostly geometric, static, grasping, or singularity-oriented. Existing Koopman contact work is dynamic and data-driven. The open gap is using Grassmannian/contact-wrench geometry to reduce or structure **dynamic multi-contact friction optimization for locomotion**.

### Mathematical Approach
- **Decision:** Grassmannian manifolds for **dynamic** multi-contact friction optimization (primary, refined gap), with Koopman operators as complementary direction for contact-rich friction dynamics
- **Status:** Both directions strengthened by refined gap analysis; Grassmannian novelty confirmed as dynamic (not static) application
- **Risks:** Koopman convergence limitations (Zhang & Zuazua 2022 — slow m^{-1/2} convergence with finite elements)

### Research Directions (Re-prioritized)
- **Primary:** Grassmannian manifolds for dynamic multi-contact friction optimization (gap: existing Grassmann contact work is static/geometric)
- **Primary:** Koopman operators for contact-rich friction dynamics (gap: no Koopman work on friction cone computation)
- **Synthesis:** Combined Grassmannian-Koopman framework (validated by Schurig et al. 2025 mathematical compatibility)
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

### Refined Gap (23 June 2026)
> Existing Grassmann/Grassmannian contact work is mostly geometric, static, grasping, or singularity-oriented. Existing Koopman contact work is dynamic and data-driven. The open gap is using Grassmannian/contact-wrench geometry to reduce or structure **dynamic multi-contact friction optimization for locomotion**.

This refined framing is **stronger** than the original claim because:
1. It acknowledges that Grassmann has been used near contact (which is true — El-Khoury, ponce.4finger)
2. It precisely locates the novelty: **dynamic** vs. **static** application
3. It distinguishes from Schurig et al. (2025) who use Grassmannian for Koopman dictionary learning, not friction dynamics
4. It creates a natural synthesis path between Grassmannian (spatial/structural) and Koopman (temporal/dynamic)

### Technical Insights
1. **Maximum dissipation principle** provides more accurate cone modeling than pyramidal approximation
2. **Monopod feasibility** demonstrated; **biped** implemented (18,000 epochs × 6 hours — computationally expensive)
3. **Transient motion phases** are highly nonlinear and difficult to compute — this is where the method provides value
4. **Sliding mass model** captures velocity of center of gravity — produces trajectories similar to normal sliding box on frictional surface
5. **Epsilon relaxation** method iteratively tightens solution space from large error margin to feasible solution
6. **Koopman convergence warning:** Zhang & Zuazua (2022) show gEDMD with finite elements converges at m^{-1/2}, and direct interpolation outperforms Koopman for 1D problems — important caveat for the proposed direction

### Collaboration Insights
- Hozefa brings Grassmannian manifold expertise and confirms feasibility
- Fares exploring DLR Germany collaboration for space robotics specialization
- Co-supervision should complement, not conflict, with main supervisor
- Industry applications important — need to create own industrial scenarios

## Next Immediate Steps (Priority Order)
1. **DONE:** Overleaf PSD document created — this Git repo IS the Overleaf doc (synced via GitHub)
2. **DONE:** Flow matching paper reviewed (ForceFlow, arXiv:2605.11048v1) — now in local library
3. **HIGH:** Populate LaTeX section files with substantive content — research_directions.tex, research_questions.tex, ideas.tex, lit_notes.tex are currently sparse; Memory Bank has rich content ready
4. **HIGH:** Complete literature review on Grassmannian manifolds for friction cones — add newly acquired papers (Krolicki, Shi, O'Neill, Terrones) to the synthesis
5. **HIGH:** Update literature review to include verified gap — add Caron et al. (2015/2016), Orsolino et al. (2017), O'Neill et al. (2025) papers
6. **MEDIUM:** Send ICRA paper and thesis links to supervisors
7. **MEDIUM:** Investigate Koopman operators/EDMD for the system — specifically for friction cone computation
8. **LOW:** Explore co-supervision options
9. **LOW:** Begin coordinating lab space/desk arrangements for August arrival
