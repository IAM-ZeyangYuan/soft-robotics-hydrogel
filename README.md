# Modelling and Experimentation of NaAc/AAm Hydrogel Beams as Soft Robotics Actuators

**Duration:** 10/2024 – 09/2025  
**Tags:** `Hardware / Experiment` · `Simulation` · `Robotic Actuation` · `Python` 

---

## Overview

**Background:** Hydrogels are multi-stimuli-responsive actuators in the field of soft robotics. However, application-specific modelling and corresponding experimental validation for this material are currently limited.

In this project, I developed a multi-physics simulation model, coupled with experimental validation, for the **electrically induced actuation of NaAc/AAm hydrogel beams** immersed in a NaCl solution.





---

## Experiment

I established a repeatable experimental system for fabricating NaAc-AAm hydrogel beams and conducting actuation tests to validate the corresponding simulation.

### Fabrication

**Hydrogel precursor composition:**

| Component   | Material     | Amount                                     |
|-------------|--------------|--------------------------------------------|
| Monomer     | AAm + NaAc   | 5 M total (7:3 ratio)                      |
| Crosslinker | BAAm         | 1:200 or 1:2000 (divinyl to vinyl monomer) |
| Initiator   | 10 wt% APS   | 67 µL per 5 mL water                       |
| Accelerator | 99.5% TEMED  | 1.8 µL per 5 mL water                      |

I iterated the composition and the molding system design for an optimal, repeatable fabrication protocol.

| Image | Description |
|---|---|
| ![Extracted hydrogel beams](images/out_gel.png) | **Extracted NaAc-AAm hydrogel beams** |
| ![Mold design iterations](images/mold_iter.png) | **Iterations of the molding design** |
| ![Before polymerisation](images/pre_gel.png) | **Molding system before polymerisation** |
| ![After polymerisation](images/post_gel.png) | **Molding system after polymerisation** in a 45 °C environment |

---

### Swelling Actuation Test

I conducted swelling actuation tests on the fabricated hydrogel beams in a NaCl bath, with varying crosslinker ratio and salt concentration, as a way to validate the simulation.




<table align="left">
  <tr>
    <td>
      <b>Crosslinker ratio vs. swelling</b>
      <table>
        <tr><th>Crosslinker ratio</th><th>1:200</th><th>1:2000</th></tr>
        <tr><td>Swollen width (mm)</td><td>3.00</td><td>5.00</td></tr>
        <tr><td>Swelling ratio (vs. reference)</td><td>3</td><td>5</td></tr>
      </table>
    </td>
    <td>
      <b>NaCl concentration vs. swelling</b>
      <table>
        <tr><th>NaCl concentration</th><th>0.01 M</th><th>0.1 M</th><th>1 M</th></tr>
        <tr><td>Swollen width (mm)</td><td>3.00</td><td>2.55</td><td>2.05</td></tr>
        <tr><td>Swelling ratio (vs. reference)</td><td>3</td><td>2.55</td><td>2.05</td></tr>
      </table>
    </td>
    <td>
      <img src="images/swollen_gel.png" width="300"/>
    </td>
  </tr>
</table>

---

### Bending Actuation Test

- I conducted bending actuation tests on the fabricated hydrogel beams in a NaCl bath, under an electric field, with varying crosslinker ratio and electric field strength, as a way to validate the simulation.
<details>
<summary>Click to view the bending test setup</summary>

  <table align="center">
    <tr>
      <td align="center">
        <img src= "images/setup_side.png" width="300"/><br/>
        <sub>Bending test setup (side view)</sub>
      </td>
      <td align="center">
        <img src="images/setup_top.png" width="300"/><br/>
        <sub>Bending test setup (top view)</sub>
      </td>
      <td align="center">
        <img src="images/clamp.png" width="300"/><br/>
        <sub>Fixture design</sub>
      </td>
    </tr>
  </table>

</details>
<br>



- The bending response exhibits first-order–like dynamics, with an initially near-linear transient and an asymptotic approach to its magnitude limit; behaviour against varying parameters (electric field strength, crosslinker ratio) is used to validate the simulation

<table align="center">
    <tr>
      <td align="center">
        <img src= "images/bent_gel.png" width="300"/><br/>
        <sub>Bending test setup (side view)</sub>
      </td>
      <td align="center">
        <img src="images/bending_results.png" width="300"/><br/>
        <sub>Bending test setup (top view)</sub>
      </td>
    </tr>
</table>




















---


## Simulation (Python / MATLAB)

I built a multi-physics simulation that predicts the actuation of electro-active hydrogel beams in a salt bath under an electric field. The prediction is validated through experiments and self-consistency checks.

### Predicted Actuation

| Image | Description |
|---|---|
| ![Actuation vs voltage](images/voltage_varing.png) | **Predicted actuation at different voltages** — predicted swelling is within the same order of magnitude as experimental values; swelling increases to a maximum of 8.7% in the presence of an electric field (not observed experimentally); predicted deflection trend matches experimental observations |
| ![Actuation vs water percentage](images/phiw_0_varing.png) | **Predicted actuation at different reference water percentages (ψ₀ʷ)** — simulation and experiment show opposite behaviours when crosslinker ratio is assumed to be associated solely with ψ₀ʷ; further investigation will include the effect of the crosslinker on the Lamé coefficients |
| ![Actuation vs salt concentration](images/cstar_varing.png) | **Predicted actuation at different salt bath concentrations** — predicted swelling follows the same trend as the experiment; however, achieving a linear swelling decrease requires a near-linear concentration increase in the model vs. an exponential increase in the experiment |

### Predicted Field Distributions

| Image | Description |
|---|---|
| ![Ionic and electric distribution](images/ionic_electric.png) | **Predicted distribution of ionic species and electric potential** — shows the asymmetry in ionic distributions and the drop in electric potential created by the presence of the hydrogel (c_f = fixed ionic distribution on the hydrogel network); results agree with published work using different algorithm/formulation systems, further validating the simulation |
| ![Displacement and pressure](images/dis_press.png) | **Predicted distribution of hydrogel displacement and fluid pressure** — displacement asymmetry about the fixed midpoint and the fluid pressure gradient are consistent with the actuation direction of the hydrogel |

### Further Validation

![Domain length validation](images/difflen.png)

**Dependence of predicted swelling on domain length (expected invariance)** — I used a range of numerical domain lengths to investigate their influence on the predicted swollen width (at ψ₀ʷ = 0.6; NaCl = 10 mol/m³). A 20% change in domain length leads to only 1% variation in predicted swelling width, demonstrating simulation reliability in this regard.

---

## Limitations

- Only a **limited range** of voltage and electrode distance can be used, to avoid electrolysis and ensure visible bending.
- Due to the **intrinsic accuracy limitation** of the selected local nonlinear solvers, consistent results were only produced within:
  - Voltage: 0.0625 V – 0.1875 V
  - Salt concentration: 8.75 – 11.25 mol/m³
  - Reference water volume percentage: 0.6 – 0.9
- A **parameter misalignment** exists between the experimental and simulation ranges, which partially reduces the credibility of the experimental validation.

---

## Future Work

- Apply **deterministic global nonlinear solvers** and greater computational resources to improve numerical accuracy and consistency.
- Computationally investigate applicable parameter ranges first, then test viable combinations experimentally to close the simulation–experiment gap.

---

## Tech Stack

`Python` · `MATLAB` · `HTML / CSS / JavaScript`