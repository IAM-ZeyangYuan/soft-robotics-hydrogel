# Multi-Stimuli-Responsive Smart Materials for Soft Robotics

**Duration:** October 2024 – September 2025  
**Tags:** `Hardware / Experiment` · `Python` · `Simulation` · `Robotic Actuation`

---

## Overview

This project develops a multi-physics simulation model, coupled with experimental validation, for the **electrically induced actuation of NaAc/AAm hydrogel beams** immersed in a NaCl solution.

In the field of soft robotics, hydrogels are multi-stimuli-responsive, bio-compatible polymer networks with properties of both solids and liquids. Application-specific modeling and experimental validation for this class of material remain limited — this work addresses that gap.

---

## Project Structure

```
soft-robotics-hydrogel/
├── index.html           # Portfolio page (self-contained)
├── img/
│   ├── background.png
│   ├── out_gel.png          # Fabricated hydrogel beams
│   ├── mold_iter.png        # Mold design iterations
│   ├── pre_gel.png          # Molding system before polymerization
│   ├── post_gel.png         # Molding system after polymerization
│   ├── swollen_gel.png      # Swelling actuation test result
│   ├── bent_gel.png         # Bending actuation test result
│   ├── voltage_varing.png   # Simulation: actuation vs voltage
│   ├── ionic_electric.png   # Simulation: ionic/electric potential distribution
│   └── difflen.png          # Simulation: swelling at different domain lengths
└── README.md
```

---

## Sections

### 1. Objective
Build a coupled simulation + experiment framework to model and validate the electrically driven actuation of NaAc-AAm hydrogel beams in a saline environment.

### 2. Experiment

A repeatable fabrication and actuation testing protocol was established.

**Hydrogel precursor composition:**

| Component   | Material         | Amount                                    |
|-------------|------------------|-------------------------------------------|
| Monomer     | AAm and NaAc     | 5 M total (7:3 ratio)                     |
| Crosslinker | BAAm             | 1:200 or 1:2000 (divinyl to vinyl monomer)|
| Initiator   | 10 wt% APS       | 67 µL per 5 mL water                      |
| Accelerator | 99.5% TEMED      | 1.8 µL per 5 mL water                     |

**Tests conducted:**
- **Swelling actuation** in NaCl bath, varying crosslinker ratio and salt concentration
- **Bending actuation** under an applied electric field

**Swelling results (crosslinker ratio):**

| Crosslinker ratio               | 1:200 | 1:2000 |
|---------------------------------|-------|--------|
| Swollen width (mm)              | 3.00  | 5.00   |
| Swelling ratio (vs. reference)  | 3     | 5      |

### 3. Simulation (Python / MATLAB)

A multi-physics simulation was built to predict the actuation of electro-active hydrogel beams in a salt bath under an applied electric field. Predictions were validated through experiments and self-consistency checks.

**Simulation outputs include:**
- Actuation magnitude across varying voltages (experimentally validated)
- Distribution of ionic species and electric potential
- Swelling behaviour across different domain lengths

### 4. Limitations

- Only a **limited range** of voltage and electrode distance can be used (to avoid electrolysis and ensure visible bending).
- Due to the **intrinsic accuracy limitation** of the local nonlinear solvers used, consistent results were only produced within:
  - Voltage: 0.0625 V – 0.1875 V
  - Salt concentration: 8.75 – 11.25 mol/m³
  - Reference water volume percentage: 0.6 – 0.9
- A **parameter misalignment** exists between the experimental and simulation ranges, which partially reduces the credibility of the experimental validation.

### 5. Future Work

- Apply **deterministic global nonlinear solvers** and greater computational resources to improve numerical accuracy and consistency.
- Computationally investigate applicable parameter ranges first, then test viable combinations experimentally to close the simulation–experiment gap.

---

## Tech Stack

- **Python** — simulation scripting
- **MATLAB** — numerical modelling
- **HTML / CSS / JavaScript** — portfolio page
