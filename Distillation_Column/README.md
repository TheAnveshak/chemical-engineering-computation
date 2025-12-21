# Packed Distillation Column Design and Cost Optimization

## What this project is (and what it is not)

This project implements a **complete, end-to-end computational workflow** for the design and economic optimization of a **packed distillation column w.r.t. Operation Pressure**, intended strictly for **academic use**.

The focus is **not** on GUI-style process simulation or black-box solvers.
Instead, the emphasis is on:

* Explicit modeling assumptions
* Transparent thermodynamics
* Reproducible calculations
* Design decisions that can be traced step by step

All calculations are implemented explicitly in code. The notebook is meant to be *read*, *modified*, and *questioned*.

---

## Why this approach

Most distillation design workflows either:

1. Remain fully hand-calculation based (good for intuition, bad for iteration), or
2. Jump directly to commercial simulators (fast, but opaque).

This project deliberately sits in between.

The objective was to **translate classical design methodology** (as taught in standard texts and courses) into a **programmable framework**, where:

* design variables can be changed easily,
* sensitivity and optimization are natural extensions,
* and assumptions are not hidden.

---

## Academic context

The methodology implemented in this notebook primarily follows classical separation process design as presented in **Coulson & Richardson, Volume 6**, which serves as the main reference for column design logic, stage requirements, packing correlations, and costing philosophy.

Thermodynamic modeling and vapor–liquid equilibrium concepts are grounded in standard chemical and biochemical engineering thermodynamics texts, particularly those commonly used for activity coefficient models and non-ideal systems. These references informed the selection and interpretation of the NRTL framework and general VLE behavior.

This project was developed as part of an academic assignment under **Prof. A. W. Patwardhan**, whose courses provided the foundational theoretical background for the material and energy balance formulation and thermodynamic reasoning used throughout the work.

The following courses formed the core academic basis for this project:

* **CET1156 – Engineering Thermodynamics**
* **CET1167 – Chemical Engineering Thermodynamics**
* **CEP1152 – Material and Energy Balance**
* **CET1160 – Chemical Engineering Operations**

##### Key references

1. Coulson, J. M.; Richardson, J. F. *Chemical Engineering, Volume 2: Particle Technology and Separation Processes*; Butterworth-Heinemann, Amsterdam, 2010.

2. Seader, J. D.; Henley, E. J.; Roper, D. K. *Separation Process Principles: Chemical and Biochemical Operations*, 3rd ed.; John Wiley & Sons, Chichester, 2011.

3. Green, D. W.; Perry, R. H. (Eds.). *Perry’s Chemical Engineers’ Handbook*, 8th ed.; McGraw-Hill Professional, New York, 2007.

4. Prausnitz, J. M. *Molecular Thermodynamics of Fluid-Phase Equilibria*, 3rd ed.; Prentice-Hall, Upper Saddle River, NJ, 1999.

These references are cited to establish theoretical grounding and standard practice. All implementation choices, assumptions, and interpretations in the notebook represent an academic exercise and the my independent computational translation of the methodology.

#### Supplementary notes and background

Conceptual notes and supporting material related to **chemical engineering thermodynamics, phase equilibria, and separation processes** are maintained separately in the following repository:

* [https://github.com/TheAnveshak/Anvesiki/tree/main/Chemical_Engineering_101/ThermoDynamics](https://github.com/TheAnveshak/Anvesiki/tree/main/Chemical_Engineering_101/ThermoDynamics)

These notes reflect personal academic understanding developed through coursework and self-study. They are provided for context and learning support only and should not be interpreted as complete design guidelines or authoritative references.

---
## For Usage

To use this project, clone or download the repository as-is.
The CSV files provided for packing performance data must be kept in their original names and directory structure, as they are read directly by the notebook for interpolation and design calculations.

Changing file names or formats will require corresponding updates in the notebook.

---

## Scope of the model

The notebook covers the following design stages in sequence:

* Thermodynamic modeling of the system (activity coefficient–based)
* Material balance formulation
* Minimum reflux and operating reflux selection
* Stage requirement estimation (including pinch considerations)
* Energy balance for internal and external flows
* Packing selection and performance interpolation
* Column sizing
* Equipment costing (column, reboiler, condenser)
* Overall cost minimization

Each stage is coded explicitly rather than wrapped into a single solver.

---

## Thermodynamics and model choice

The **NRTL activity coefficient model** is used for VLE calculations.

The choice is deliberate:

* The system under study exhibits non-ideal liquid-phase behavior
* NRTL is well-documented, widely used, and consistent with the reference methodology
* Model fitting and limitations are discussed in the attached project report

Rather than overfitting or introducing multiple models, the intent was to **stay consistent** with one thermodynamic framework across all calculations.

---

## Material and energy balances

Material and energy balances are written explicitly and solved numerically.

Key points:

* No simulator-generated balances
* All flow rates, duties, and internal streams are visible

---

## Packing data and interpolation

Structured packings from **Sulzer (2X series)** are used as benchmark references.

Important clarifications:

* Manufacturer data are used **only for academic demonstration**
* No proprietary correlations are claimed
* Original manufacturer PDFs are attached for transparency

Packing performance data were digitized using **WebPlotDigitizer**, and the extracted datasets are stored as individual CSV files.
These are then used for **2D interpolation** to evaluate pressure drop and HETP across operating conditions.

This approach was chosen to:

* avoid hardcoding discrete data points,
* allow smooth variation during optimization,
* keep the data handling explicit and inspectable.

---

## Costing methodology

Equipment costing follows standard chemical engineering heuristics consistent with **Coulson & Richardson**.
All cost correlations and assumptions are clearly separated from the process calculations so that:

* costing methods can be replaced or updated independently,
* sensitivity to economic parameters can be studied.

---

## Optimization philosophy

The optimization performed here is **engineering-driven**, not purely mathematical.

Rather than blindly minimizing cost, the workflow:

* respects feasible operating regions,
* maintains physically meaningful designs,
* avoids unrealistic parameter combinations.

The goal is not “optimal by solver,” but **reasonable, justifiable design choices** backed by computation.

---

## References

* Coulson & Richardson, *Chemical Engineering*, Volume 6
* Sulzer structured packing technical documentation
* Course notes and standard separation process design literature

---

## Final note

This project reflects an attempt to **treat distillation design as a computational problem**, not just a solved exercise.

If something feels explicit, slow, or repetitive in the code - that is intentional.
The priority is **clarity over cleverness**.
Refer to the attached PDF report for derivations and background.
The notebook is intentionally linear and verbose in logic, even where it could be condensed.


### Important clarification

This work is intended for **academic learning and demonstration**.
The notebook reflects how standard design methods can be implemented computationally and does not claim completeness, industrial readiness, or authoritative correctness beyond its educational scope.

---


