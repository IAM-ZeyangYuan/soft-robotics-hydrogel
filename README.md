# Actuation Modelling and Experimentation of NaAc/AAm Hydrogel Beams as Soft Robotics Actuators

**Duration:** 10/2024 – 09/2025  
**Tags:** `Experiment / Hardware` · `Simulation` · `Robotic Actuation` · `Python` 

---

## Overview

**Background:** Hydrogels are multi-stimuli-responsive actuators in the field of soft robotics. However, application-specific modelling and corresponding experimental validation for this material are currently limited.

In this project, I developed a multi-physics simulation model, coupled with experimental validation, for the **electrically induced actuation of NaAc/AAm hydrogel beams** immersed in a NaCl solution.





---

## Experiment

I established a repeatable experimental system for fabricating NaAc-AAm hydrogel beams and conducting actuation tests, to test the electro responses of material and validate the corresponding simulation.

### Fabrication

- The hydrogel composition was iterated to achieve controllable polmerisation speed, maximum electro responses.

<details>
<summary><i>Click to view the hydrogel precursor composition</i></summary>

<br>

**Hydrogel precursor composition:**
| Component   | Material     | Amount                                     |
|-------------|--------------|--------------------------------------------|
| Monomer     | AAm + NaAc   | 5 M total (7:3 ratio)                      |
| Crosslinker | BAAm         | 1:200 or 1:2000 (divinyl to vinyl monomer) |
| Initiator   | 10 wt% APS   | 67 µL per 5 mL water                       |
| Accelerator | 99.5% TEMED  | 1.8 µL per 5 mL water                      |


</details>





<br>

- The molding design was iterated to resolve issues including mold deformation, undesirable gel shape, and polymerisation inhibition caused by the mold material.

<details>
<summary><i>Click to view the iterations of the molding design</i></summary>
<br>

  <p align="center">
    <img src= "images/mold_iter.png" width="300"/><br/>
    <sub>Iterations of the molding design</sub>
  </p>

</details>

<br>

<table align="center">
  <tr>
    <td align="center">
      <img src= "images/pre_gel.png" width="300"/><br/>
      <sub>Molding system pre polymerisation</sub>
    </td>
    <td align="center">
      <img src="images/post_gel.png" width="300"/><br/>
      <sub>Molding system post polymerisation</sub>
    </td>
      <td align="center">
    <img src= "images/out_gel.png" width="300"/><br/>
    <sub>Extracted NaAc-AAm hydrogel beams</sub>
    </td>
  </tr>
</table>






---

### Swelling Actuation Test

I conducted swelling actuation tests on the fabricated hydrogel beams in a NaCl bath, with varying crosslinker ratio and salt concentration, also as a way to validate the simulation.




**Results — swelling under different conditions:**
| Crosslinker ratio  or NaCl concentration| 1:200 | 1:2000 | 0.01 M | 0.1 M | 1 M  |
|----------------------------------|-------|--------|--------|-------|------|
| Swollen width (mm)               | 3.00  | 5.00   | 3.00   | 2.55  | 2.05 |
| Swelling ratio (vs. reference)   | 3     | 5      | 3      | 2.55  | 2.05 |


<p align = "center">
    <img src="images/swollen_gel.png" width="300"/><br/>
    <sub>Swelling actuation test of the hydrogel beams</sub>
</p>


---

### Bending Actuation Test

I conducted bending actuation tests on the fabricated hydrogel beams in a NaCl bath, under an electric field, with varying crosslinker ratio and electric field strength, as a way to validate the simulation.
<details>
<summary><i>Click to view the bending test setup</i></summary>

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





<table align="center">
    <tr>
      <td align="center">
        <img src= "images/bent_gel.png" width="300"/><br/>
        <sub>Bending actuation test of the hydrogel beams</sub>
      </td>
      <td align="center">
        <img src="images/bending_results.png" width="300"/><br/>
        <sub>Bending actuation test results</sub>
      </td>
    </tr>
</table>


- The bending response exhibits first-order–like dynamics, with an initially near-linear transient and an asymptotic approach to its magnitude limit; behaviour against varying parameters (electric field strength, crosslinker ratio) is also used to validate the simulation.

















---


## Simulation (Python / MATLAB)

I built a multi-physics simulation that predicts the actuation of electro-active hydrogel beams in a salt bath under an electric field. The prediction is validated through experiments and self-consistency checks.

### Predicted Actuation

<table align="center" style="width: 90%; table-layout: fixed;">

  <colgroup>
    <col style="width: 33%">
    <col style="width: 33%">
    <col style="width: 33%">
  </colgroup>
  <tr>
    <td align="center" valign="top">
      <img src="images/voltage_varing.png" style="width:300px; object-fit:contain;">
      <br>
      <sub>Predicted actuation at different voltages</sub>
      <details>
        <summary><i>Details</i></summary>
        <div style="text-align: left;">
          <ul>
            <li>
              The predicted swelling is within the same order of magnitude as the experimental values.
            </li>
            <li>
              The predicted swelling increases to a maximum of 8.7% in the presence of an electric field, which was not observed in the experiments.
            </li>
            <li>
              The predicted deflection exhibits the same trend as that observed in the experiments.
            </li>
          </ul>
        </div>
      </details>
    </td>
    <td align="center" valign="top">
      <img src="images/phiw_0_varing.png" style="width:300px; object-fit:contain;">
      <br>
      <sub>Predicted actuation at different reference water percentages (ψ₀ʷ)</sub>
      <details>
        <summary><i>Details</i></summary>
        <div style="text-align: left;">
          <ul>
            <li>
              The simulation and the experiment exhibited opposite behaviours when the crosslinker ratio was assumed to be associated solely with ψ₀ʷ.
            </li>
            <li>
              Further investigation will include the effect of the crosslinker on the Lamé coefficients.
            </li>
          </ul>
        </div>
      </details>
    </td>
    <td align="center" valign="top">
      <img src="images/cstar_varing.png" style="width:300px; object-fit:contain;">
      <br>
      <sub>Predicted actuation at different salt bath concentrations</sub>
      <details>
        <summary><i>Details</i></summary>
        <div style="text-align: left;">
          <ul>
            <li>
              The predicted swelling follows the same trend as the experimental result; however, to achieve a linear swelling decrease, the model requires a near-linear increase in salt concentration, whereas the experiment requires an exponential increase.
            </li>
            <li>
              Further investigation will increase the sample size and the parameter range, to realize a more confident analysis.
            </li>
          </ul>
        </div>
      </details>
    </td>
  </tr>
</table>





### Predicted Field Distributions




<table align="center" style="width: 60%; table-layout: fixed;">

  <colgroup>
    <col style="width: 50%">
    <col style="width: 50%">
  </colgroup>
  <tr>
    <td align="center" valign="top">
      <img src="images/ionic_electric.png" style="width:300px; object-fit:contain;">
      <br>
      <sub>Predicted distribution of ionic species and electric potential</sub>
      <details>
        <summary><i>Details</i></summary>
        <div style="text-align: left;">
          <ul>
            <li>
              The plot showcases the asymmetry in the ionic distributions and the ‘drop’ in electric potential distribution created by the presence of the hydrogel. (cf represents the fixed ionic distribution on the hydrogel network)
            </li>
            <li>
              The plot is in agreement with results in other researches using different algorithm/formulation systems, further validating the simulation.
            </li>
          </ul>
        </div>
      </details>
    </td>
    <td align="center" valign="top">
      <img src="images/dis_press.png" style="width:300px; object-fit:contain;">
      <br>
      <sub>Predicted distribution of hydrogel displacement and fluid pressure</sub>
      <details>
        <summary><i>Details</i></summary>
        <div style="text-align: left;">
          <ul>
            <li>
              The displacement asymmetry about the fixed mid point and the fluid pressure gradient is consistent with the actuation direction of the hydrogel.
            </li>
          </ul>
        </div>
      </details>
    </td>
  </tr>
</table>

### Further Validation

- **Dependence of predicted swelling on domain length (expected invariance)** — I used a range of numerical domain lengths to investigate their influence on the predicted swollen width (at ψ₀ʷ = 0.6; NaCl = 10 mol/m³). A 20% change in domain length leads to only 1% variation in predicted swelling width, demonstrating simulation reliability in this regard.

  <p align="center">
    <img src= "images/difflen.png" width="300"/><br/>
    <sub>Further validation: swelling at different domain lengths</sub>
  </p>

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

