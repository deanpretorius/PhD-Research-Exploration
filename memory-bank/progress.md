# Progress: PhD Research Exploration

## What Works

### Completed Milestones
- [x] **Initial supervision structure established** (3 meetings conducted: 13 May, 22 May, 10 June 2026)
- [x] **Core research direction identified** (Grassmannian manifolds for friction modeling in multi-legged robots)
- [x] **Mathematical foundation validated** (friction cones as Riemannian manifolds → Grassmannian connection confirmed by Hozefa)
- [x] **Complementary directions identified** (Koopman operators, force flow dynamics, systems engineering framework)
- [x] **Prior work foundation** (master's thesis, ICRA paper — friction cone optimization on monopod/biped)
- [x] **DLR Germany collaboration initiated** (Fares established contact with space robotics specialist)
- [x] **AI-assisted research workflow established** (NotebookLM, Claude, ChatGPT in use)
- [x] **Local LaTeX research repository set up** (Git-tracked, Overleaf PSD document pending)
- [x] **Administrative progress** (clearance and transcript complete; work permit in process)

### Technical Achievements (from master's work)
- [x] 3D friction cone computation using maximum dissipation principle (more accurate than pyramidal approximation)
- [x] Monopod feasibility demonstrated
- [x] Biped implementation completed (trajectory optimization using epsilon relaxation)
- [x] Sliding mass model for velocity tracking (center of gravity trajectory captured)
- [x] Epsilon relaxation method for robust non-linear optimization convergence

## What's Left to Build

### Immediate Priorities (Next 2-4 Weeks)

- [ ] **Create Overleaf PSD document** ("PSD Dean's PSD Plan") with structure:
  - Tentative research plan
  - Ideas and exploratory directions
  - Progress tracking
  - Meeting notes
- [ ] **Complete state-of-the-art literature review** on:
  - Grassmannian/Riemannian manifolds applied to friction cones and sliding
  - Koopman operators for locomotion dynamics
  - Relevance and novelty confirmation
- [ ] **Review flow matching paper** (shared by Hozefa)
- [ ] **Share ICRA paper and master's thesis** with Fares and Hozefa
- [ ] **Investigate Koopman operators/EDMD** for friction dynamics linearization

### Medium-Term (Next 2-3 Months)

- [ ] **Mapping: Friction cones → Riemannian manifolds → Grassmannian representation**
  - Mathematical formulation of contact configuration subspace projections
  - Dimensionality reduction bounds derivation
- [ ] **Grassmannian-reduced friction optimization implementation** (Python/Google Colab)
  - Benchmark against existing monopod/biped results (reduced computation time)
  - Extend to multi-legged configurations (hexapod/octopod simulation)
- [ ] **Optimization solver identification** (Hozefa's question from 22 May meeting)
- [ ] **Prepare for DLR Germany specialist talk** (October/November 2026)

### Long-Term (6+ Months)

- [ ] **PhD research proposal (PSD) submission**
- [ ] **Real robot validation** (Spot robot or similar platform)
- [ ] **Demo video creation** for research findings
- [ ] **Publication pipeline** (journal papers, conferences)
- [ ] **Industry application demonstration** (edge-to-cloud, VR integration)
- [ ] **Co-supervision arrangement** (if needed)

## Current Status

### Phase: Early Exploration
The research is in **Phase 1: Foundation and Literature Review** of the PhD timeline.

**Progress indicators:**
- Research direction: ✅ Identified and validated by supervisory team
- Mathematical framework: 🔄 In development (Grassmannian mapping)
- Literature review: 🔄 Active (state-of-the-art search in progress)
- Simulation: ⬜ Not yet started for this direction (master's code available)
- Real robot testing: ⬜ To begin after August 2026 arrival
- PSD document: ⬜ To be created (Overleaf)
- Publication: ⬜ Not yet started

| Area | Status | Next Action |
|------|--------|-------------|
| Grassmannian manifolds | 🔄 Literature search | Confirm novelty, document findings |
| Riemannian manifolds | 🔄 Theory validation | Map friction cone geometry |
| Koopman operators | ⬜ Literature review | Read flow matching paper |
| Force flow dynamics | ⬜ Exploration | TBD |
| Systems engineering | ⬜ Integration | Apply NASA handbook framework |
| PSD document | ⬜ Creation | Set up Overleaf structure |

## Known Issues

### Repository Issues
1. **references.bib is malformed** — contains LaTeX document preamble instead of BibTeX entries. Will cause bibliography compilation errors if main.tex is built with bibliography enabled.
2. **sections/meeting_notes.tex is empty** — appears to be a duplicate of sections/Meeting Minutes.tex. Unclear which is authoritative.
3. **sections/lit_notes.tex is placeholder** — contains only example markdown, no actual literature notes.

### Technical Issues
4. **Optimization solver not specified** — Hozefa asked about this in the 22 May meeting. Needs investigation and documentation.
5. **Simulation computational cost is high** — 18,000 epochs × 6 hours for biped. Grassmannian reduction target not yet quantified.
6. **Google Drive access issues** — Dean experienced firewall problems accessing shared files. Alternative sharing methods may be needed.

### Research Risks
7. **Novelty unconfirmed** — Grassmannian manifolds may already be applied to friction problems. State-of-the-art review is critical.
8. **PhD timeline uncertainty** — Work permit pending, arrival expected August 2026, but delays possible.
9. **Physical robot access** — Spot robot or alternative platform availability not yet confirmed.

## Evolution of Project Decisions

### Decision Timeline

**13 May 2026 — Meeting 1: Direction Setting**
- Initial focus: Extending ICRA paper using Grassmannian/Manifold methods
- Decision: Pursue space robotics track with Professor Fares
- Decision: Involve Hozefa as Grassmannian manifold expert

**22 May 2026 — Meeting 2: Technical Deep Dive**
- Decision: Use Grassmannian manifolds to reduce friction optimization complexity
- Insight (Hozefa): Friction cones are Riemannian manifolds → provides natural connection
- Decision: Treat contact points as projections on Grassmannian manifold
- Decision: Use AI tools (NotebookLM, ChatGPT, Claude) for gap analysis
- Decision: Transition to weekly 30-minute meetings

**10 June 2026 — Meeting 3: Expansion**
- Decision: Create Overleaf PSD document with structured sections
- Decision: Investigate Koopman operators as complementary approach
- Decision: Use NYU email/chat for all future communications
- Decision: Explore DLR Germany collaboration
- Decision: Integrate systems engineering framework (NASA handbook)
- Decision: Pursue edge-to-cloud computing + VR for industrial demonstration
- Decision: Identify co-supervision needs before proposing specific candidates
- Confirmed: Real robot testing required alongside simulation

### Decision Patterns
- **Exploratory approach:** Multiple research directions maintained in parallel (manifolds, Koopman, force flow) with periodic convergence checks
- **Industry grounding:** Every theoretical direction paired with practical application consideration
- **Tool-rich methodology:** AI tools leveraged for literature review and gap analysis, not as replacement for human judgment
- **Documentation-first:** Overleaf/LaTeX used for systematic progress tracking from Day 1

## Dependencies Tracker

| Dependency | Status | Blocking |
|-----------|--------|----------|
| Work permit | 🔄 In progress | 🇳🇬 Admission, August arrival |
| Lab space/desk | ⬜ Pending | Physical presence at NYU AD |
| Spot robot | ⬜ Unconfirmed | Real robot validation |
| DLR collaboration | 🔄 Fares initiated | Space robotics specialization |
| Co-supervisor | ⬜ To identify | Direction-specific guidance |
| Overleaf access | 🔄 To set up | PSD document creation |
| ICRA paper sharing | ⬜ Pending | Supervisor review of foundation |

## Metrics & Targets

### Performance Targets (Tentative)
- **Current biped optimization:** 18,000 epochs × ~6 hours
- **Grassmannian reduction target:** Order-of-magnitude improvement (to be quantified)
- **Target platforms:** Monopod ✅ → Biped ✅ → Hexapod/Octopod ⬜

### Quality Targets
- Novelty: Beyond existing friction cone methods (confirmed via literature review)
- Reproducibility: Documented simulation environment (Google Colab notebooks)
- Validation: Both simulated and physical robot testing
- Impact: Publication in robotics/control venues (ICRA, RSS, TRO)