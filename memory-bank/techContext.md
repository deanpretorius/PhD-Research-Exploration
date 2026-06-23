# Tech Context: PhD Research Exploration

## Technologies Used

### Document Preparation
| Technology | Purpose | Status |
|-----------|---------|--------|
| LaTeX | Primary document preparation | Active (main.tex, sections/) |
| Overleaf | Collaborative LaTeX editing via Git sync | **Active** — this repository IS the Overleaf document, synced via Git |
| BibTeX | Reference management | references.bib (needs fixing — currently contains LaTeX preamble, not BibTeX entries) |
| Markdown (hybrid) | Inline markdown within LaTeX | Active (lit_notes.tex) |

### Computational Tools
| Technology | Purpose | Status |
|-----------|---------|--------|
| Python | Primary programming language | Active (master's work) |
| Google Colab | Cloud-based simulation environment | Active (existing workflow from master's) |
| Optimization solver | Non-linear optimization (unspecified) | Used in master's; Hozefa asked for details in 22 May meeting |

### AI/Research Tools
| Technology | Purpose | Notes |
|-----------|---------|-------|
| NotebookLM | Paper summarization, audio overviews, research gap analysis | Used by Dean |
| Claude | Research exploration, code generation | Current tool |
| ChatGPT | Research exploration, literature analysis | Supplementary |
| DeepSeek | Niche topic search | Fares noted superior search but reliability issues |

### Communication & Collaboration
| Technology | Purpose | Status |
|-----------|---------|--------|
| NYU email | Official communications | Active |
| NYU chat/Teams | Day-to-day messaging | To be adopted |
| Zoom | Supervision meetings | Active (weekly 30 min) |

## Development Setup

### Local Environment
- **OS:** Windows 11
- **LaTeX Distribution:** Assumed installed (main.tex compiles)
- **Python:** Available (via pip, used in master's)
- **Git:** Available (repo hosted at github.com/deanpretorius/PhD-Research-Exploration)
- **IDE:** Visual Studio Code

### Remote/Collaborative
- **Overleaf:** Shared PSD document — **this Git repository is synced with Overleaf** via the GitHub-Overleaf integration. `main.tex` is the root document, and `sections/` are included via `\input{}` commands. Changes pushed to GitHub sync to Overleaf automatically.
- **Google Colab:** For simulation notebooks
- **Google Drive:** File sharing (Dean faced firewall issues accessing)

## Technical Constraints

### Computational Constraints
1. **Simulation time:** 18,000 epochs × ~6 hours per biped simulation
2. **Non-linear optimization:** Prone to local minima — requires epsilon relaxation or similar robust method
3. **Hardware access:** Spot robot not yet physically available (Dean arriving August 2026)
4. **Lab access:** To be coordinated with Fares once logistics are clear

### Data/Access Constraints
1. **Existing code/data:** On Google Drive (Dean experienced firewall issues)
2. **Master's thesis & ICRA paper:** Available but need sharing with supervisors
3. **Literature access:** Papers shared via Zoom/email; need systematic organization

### Research Constraints
1. **Novelty requirement:** Grassmannian approach to friction must be novel — state-of-the-art review required
2. **Physical validation:** Simulation alone is insufficient; real robot testing required
3. **Industry relevance:** Must demonstrate practical applications beyond theory
4. **Time:** PhD timeline has just started; PSD development in progress

## Dependencies

### Papers to Review
| Paper | Relevance | Status |
|-------|-----------|--------|
| Dean's master's thesis | Foundation: friction cone optimization | Available, needs sharing |
| Dean's ICRA paper | Published work on 3D friction computation | Available, needs sharing |
| Flow matching paper (from Hozefa) — ForceFlow (2605.11048v1) | Contact-driven flow matching for manipulation | Reviewed (now in library) |
| 1-s2.0-S2405896322028622-main.pdf | Koopman for quadruped leg dynamics on deformable terrain | In repository |
| 2303.10471v2.pdf | In repository | Not yet categorized |
| 2411.14321v3.pdf | In repository | Not yet categorized |
| 2512.13009v1.pdf | In repository | Not yet categorized |
| 2605.11048v1.pdf | ForceFlow: Learning to Feel and Act via Contact-Driven Flow Matching | In repository |
| A_novel_method_for_computing_the_3D_friction_cone_using_complimentary_constraints.pdf | Friction cone computation | In repository |
| A_quantitative_analysis_of_Koopman_operator_method.pdf | Koopman operator analysis | In repository |
| Borras_CK2013.pdf | Related work | In repository |
| Learning_Koopman_Dynamics_for_Safe_Legged_Locomoti.pdf | Koopman + legged locomotion | In repository |
| Ng-jerryng-phd-meche-2023-thesis.pdf | Related thesis | In repository |
| On Computing Robust N-Finger Force-Closure Grasps of 3D Objects.pdf | Grasping (related to friction) | In repository |
| poland-lec5.pdf | Lecture notes | In repository |
| ponce.4finger.pdf | Grasping literature | In repository |
| pretorius_deep_2020.pdf | Author's prior work | In repository |
| s42492-023-00137-4.pdf | Digital twin technology review | In repository |
| s43154-023-00099-8.pdf | Koopman operators for soft robotics (survey) | In repository |
| sensors-19-03713.pdf | Related work | In repository |
| Systems_Engineering-Reengineered_The_Fourth_Wave-1.pdf | Systems engineering | In repository |
| terrones-jterrone-sm-meche-2024-thesis.pdf | Terrones MIT thesis: Koopman for legged locomotion | In repository |
| thesis.pdf | Additional thesis | In repository |
| Two_graphical_methods_for_planar_contact_problems.pdf | Contact mechanics | In repository |

### Key Libraries/Frameworks
- Not yet explicitly documented; master's work used Python in Google Colab
- Optimization solver: to be identified (Hozefa asked in meeting)
- Potential: SciPy, CasADi, or similar for optimization
- Potential: PyTorch/JAX if neural network components needed

## Tool Usage Patterns

### Literature Review Workflow
```
Paper identified → Read/NotebookLM summary → Annotate in lit_notes.tex
→ AI-assisted gap analysis → Document in Overleaf → Present in meeting
```

### Simulation Workflow
```
Google Colab notebook → Python optimization → Results analysis
→ Iterate with Grassmannian reduction → Compare performance
```

### Meeting Workflow
```
Prepare updates in Overleaf → Present progress → Discuss technical issues
→ Receive assignments → Document minutes → Update research plan
```

## Configuration Notes

### LaTeX Configuration
- **Document class:** article (11pt, A4 paper)
- **Packages:** geometry, hyperref, enumitem, graphicx, markdown (hybrid mode)
- **Structure:** sections included via \input{} commands
  - `sections/research_directions.tex` — Research direction names
  - `sections/ideas.tex` — Ideas and exploratory thoughts
  - ` sections/lit_notes.tex` — Literature notes (markdown hybrid)
  - `sections/research_questions.tex` — Open questions
  - `sections/meeting_notes.tex` — Meeting summaries
  - `sections/Meeting Minutes.tex` — Detailed meeting minutes
- **Bibliography:** plain style (references.bib needs fixing — currently contains LaTeX preamble instead of BibTeX entries)

### GitHub-Overleaf Sync
- This repository is directly linked to Overleaf via Git integration
- Pushing to GitHub remote automatically syncs to Overleaf
- The main.tex file is the root document in the Overleaf project
- Section files are modular and can be edited independently
- **Implication:** All changes made to this repo (either locally or via Cline) are reflected in the Overleaf document

### Git Repository
- **Remote:** github.com/deanpretorius/PhD-Research-Exploration.git
- **Latest commit:** 3e05d6e3fc5f38858072dc0bb0587cd5363ba63c
- **Status:** Active, used for research exploration documents

### Potential Issues Flagged
1. **references.bib** contains LaTeX document preamble instead of BibTeX data — needs correction for proper bibliography compilation
2. **sections/meeting_notes.tex** appears to be empty — may be duplicate of Meeting Minutes.tex
3. **sections/lit_notes.tex** has minimal content (placeholder markdown only)