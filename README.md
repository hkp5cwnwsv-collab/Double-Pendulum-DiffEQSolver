# Double Pendulum: Dynamics, Phase Space, and Chaos
A Mathematica study of the double pendulum from animating the real motion, to mapping the full four-dimensional phase space across and ~180,000 initial conditions chaos map of the system
<!-- Hero GIF: animated double pendulum -->
<p align="center">
  <img src="media/pendulum_animation.gif" alt="Double pendulum animation" width="500"/>
</p>

## Table of Contents
- [Overview](#overview)
- [Physics Background](#physics-background)
- [Repository Structure](#repository-structure)
- [Notebooks](#notebooks)
  - [1. Main Notebook — Equations of Motion, Animation, and Phase Diagram](#1-main-notebook--equations-of-motion-animation-and-phase-diagram)
  - [2. 4D Phase Space Evolution](#2-4d-phase-space-evolution)
  - [3. Poincaré Sections](#3-poincaré-sections)
  - [4. Chaos Map](#4-chaos-map)
- [Why the Project Is Split Into Multiple Files](#why-the-project-is-split-into-multiple-files)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
- [Results](#results)
- [Future Work](#future-work)
- [License](#license)
- ---
 
## Overview
 
The double pendulum is one of the simplest mechanical systems that exhibits chaotic behavior. Two rigid pendulums attached end to end produce motion that is fully deterministic yet extremely sensitive to initial conditions.
 
This project:
 
1. **Derives** the equations of motion from the Lagrangian using the Euler–Lagrange method.
2. **Solves** the resulting coupled nonlinear ODEs numerically and **animates** the physical motion alongside its phase diagram.
3. **Sweeps** nearly 200,000 initial conditions to construct a **4D phase diagram that evolves in time**.
4. **Builds Poincaré sections** from the sweep to identify and analyze stable (regular) solutions.
5. **Generates a chaos map** showing which regions of initial‑condition space lead to chaotic versus regular motion.
---
 
## Physics Background
 
The system consists of two point masses, $m_1$ and $m_2$, attached to massless rigid rods of lengths $l_1$ and $l_2$. The generalized coordinates are the angles $\theta_1$ and $\theta_2$ measured from the vertical.
 
<!-- Diagram of the double pendulum setup -->
<p align="center">
  <img src="media/setup_diagram.png" alt="Double pendulum diagram" width="350"/>
</p>
### Lagrangian
 
With kinetic energy $T$ and potential energy $V$, the Lagrangian is $\mathcal{L} = T - V$:
 
$$
T = \frac{1}{2}(m_1 + m_2)\, l_1^2 \dot{\theta}_1^2
  + \frac{1}{2} m_2\, l_2^2 \dot{\theta}_2^2
  + m_2\, l_1 l_2\, \dot{\theta}_1 \dot{\theta}_2 \cos(\theta_1 - \theta_2)
$$
$$
V = -(m_1 + m_2)\, g\, l_1 \cos\theta_1 - m_2\, g\, l_2 \cos\theta_2
$$
 
### Euler–Lagrange Equations
 
Applying
 
$$
\frac{d}{dt}\left(\frac{\partial \mathcal{L}}{\partial \dot{\theta}_i}\right) - \frac{\partial \mathcal{L}}{\partial \theta_i} = 0, \qquad i = 1, 2
$$
 
yields two coupled, second‑order, nonlinear ODEs for $\theta_1(t)$ and $\theta_2(t)$. These are solved numerically in the main notebook. The full derivation is worked out in the notebook itself (and in the video linked above).
 
### Phase Space
 
The state of the system is fully described by four variables — $(\theta_1, \theta_2, \dot{\theta}_1, \dot{\theta}_2)$ — so the phase space is four‑dimensional. Visualizing this space, and slicing it with Poincaré sections, is the focus of the later notebooks.
 
---
 
## Repository Structure
 
```
.
├── README.md
├── DoublePendulum_Main.nb          # Derivation, numerical solution, animation, phase diagram
├── PhaseSpace_4D.nb                # ~200,000 initial conditions → time-evolving 4D phase diagram
├── Poincare_Sections.nb            # Poincaré sections built from the phase space sweep
├── ChaosMap.nb                     # Chaos map over initial-condition space
├── data/                           # (optional) exported solution data for the large sweeps
└── media/                          # GIFs and images used in this README
```
 
> **Note:** Rename the notebooks above to match the actual filenames in the repo.
 
---
 
## Notebooks
 
### 1. Main Notebook — Equations of Motion, Animation, and Phase Diagram
 
**File:** `DoublePendulum_Main.nb`
 
This is the starting point of the project. It:
 
- Sets up the Lagrangian for the double pendulum.
- Derives the equations of motion using the **Euler–Lagrange method**.
- Solves the equations numerically with `NDSolve` for a chosen set of initial conditions.
- Produces an **animated plot of the actual motion** of the pendulum.
- Produces the **corresponding phase diagram** for that trajectory.
<!-- GIF: animated pendulum motion -->
<p align="center">
  <img src="media/pendulum_animation.gif" alt="Animated double pendulum motion" width="450"/>
</p>
<!-- GIF or image: phase diagram for the same trajectory -->
<p align="center">
  <img src="media/phase_diagram.gif" alt="Phase diagram of the double pendulum" width="450"/>
</p>
**📺 Video:** [Main notebook walkthrough](YOUTUBE_LINK_HERE)
 
---
 
### 2. 4D Phase Space Evolution
 
**File:** `PhaseSpace_4D.nb`
 
Rather than following a single trajectory, this notebook solves the equations of motion for **almost 200,000 initial conditions** and assembles the results into a **four‑dimensional phase diagram that evolves with time**. This gives a global picture of how the entire phase space flows, stretches, and folds under the dynamics.
 
<!-- GIF: time-evolving 4D phase diagram -->
<p align="center">
  <img src="media/phase_space_4d.gif" alt="Time evolution of the 4D phase space" width="550"/>
</p>
**📺 Video:** [4D phase space walkthrough](YOUTUBE_LINK_HERE)
 
---
 
### 3. Poincaré Sections
 
**File:** `Poincare_Sections.nb`
 
Using the same large sweep of initial conditions, this notebook constructs the associated **Poincaré diagrams**. By recording the state each time a trajectory crosses a chosen surface of section, the 4D dynamics are reduced to a 2D map. Regular (stable) solutions appear as closed curves or isolated points, while chaotic solutions fill regions of the section — making it much easier to identify and analyze stable solutions.
 
<!-- Image: Poincaré section(s) -->
<p align="center">
  <img src="media/poincare_section.png" alt="Poincaré section of the double pendulum" width="550"/>
</p>
**📺 Video:** [Poincaré section walkthrough](YOUTUBE_LINK_HERE)
 
---
 
### 4. Chaos Map
 
**File:** `ChaosMap.nb`
 
This notebook produces the **chaos map**: a plot over initial‑condition space that classifies each starting configuration according to how chaotic the resulting motion is. It reveals the intricate boundary between regular and chaotic regions and highlights the sensitivity to initial conditions that makes the double pendulum a classic example of chaos.
 
<!-- Image: chaos map -->
<p align="center">
  <img src="media/chaos_map.png" alt="Chaos map of the double pendulum" width="550"/>
</p>
**📺 Video:** [Chaos map walkthrough](YOUTUBE_LINK_HERE)
 
---
 
## Why the Project Is Split Into Multiple Files
 
Solving ~200,000 initial conditions and rendering the resulting animations is memory‑intensive. The project is deliberately broken into separate notebooks so that each stage can be **run independently on a laptop without crashing the kernel**. The main notebook is lightweight and can be run on its own; the phase‑space, Poincaré, and chaos‑map notebooks can be run one at a time, and intermediate results can be exported to the `data/` folder and re‑imported rather than recomputed.
 
---
 
## Requirements
 
- **Wolfram Mathematica** (version XX or later — update to the version you used)
- Sufficient RAM for the large sweeps (recommend at least 16 GB; The project runs comfortably on a standard laptop, however the chaos map does take about a day to run)
---
 
## How to Run
 
1. Clone the repository:
```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   cd YOUR_REPO_NAME
```
2. Open `DoublePendulum_Main.nb` in Mathematica and evaluate the notebook (**Evaluation → Evaluate Notebook**) to see the derivation, animation, and phase diagram.
3. To reproduce the large‑scale results, open and evaluate the other notebooks **one at a time**:
   - `PhaseSpace_4D.nb`
   - `Poincare_Sections.nb`
   - `ChaosMap.nb`
4. Adjust the number of initial conditions or the integration time at the top of each notebook if you need to reduce memory usage on your machine.
---
 
## Results
 
<!-- Optional: a gallery of the best images/GIFs, or a short summary of key findings -->
 
| Animation | Phase Diagram | Poincaré Section | Chaos Map |
|:---:|:---:|:---:|:---:|
| <img src="media/pendulum_animation.gif" width="200"/> | <img src="media/4DWithPointcare.gif" width="200"/> | <img src="media/poincare_section.png" width="200"/> | <img src="media/chaos_map.png" width="200"/> |
 
Key observations:
 
- *(Add your findings here — e.g., which regions of initial‑condition space remain regular, where chaos onsets, notable stable solutions found via the Poincaré sections.)*
---
 
 
## License
MIT License

Copyright (c) 2026 Peter Krosniak

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
---
 
## Author
 
**Peter** — *(add contact / links here)*
  
