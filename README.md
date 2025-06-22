# Inverse Design of Aging Schedules for Al–Cu Alloys Using Thermo-Calc, PRISMA and Machine Learning

This project accelerates heat-treatment optimization for Al–Cu alloys by combining Thermo-Calc/PRISMA simulations, Orowan-based strengthening models, and a random forest surrogate for rapid inverse design. The tool recommends the most energy and time efficient aging schedule to achieve a target yield strength.

---

## Overview

- **Simulate**: Solutionizing, quenching, and aging of Al–4wt%Cu alloys using Thermo-Calc and PRISMA. With this, we obtain Mean radius and volume fraction vs time data for a wide range of aging tempertures.
- **Calculate**: Yield strength vs time using the Orowan model for each simulated schedule.
- **Train**: Random forest regressor to predict yield strength from temperature and time.
- **Inverse Design**: Grid-search the surrogate model to find the optimal (temperature, time) schedule for any target strength, prioritizing energy and time efficiency.

## Orowan Strengthening Model

Yield strength for each schedule is computed as:

$\sigma_y = \sigma_0 + M G \epsilon \sqrt{f_v} + \frac{0.4\,G\,b}{2\pi\sqrt{1-\nu}\,\lambda} \ln \left( \frac{r}{b} \right)$

where:

- $\sigma_0$: Friction stress (50 MPa)
- $M$: Taylor factor (3.0)
- $G$: Shear modulus of Al (27,000 MPa)
- $\epsilon$: Misfit strain (0.007)
- $f_v$: Precipitate volume fraction
- $b$: Burgers vector (0.286 nm)
- $\nu$: Poisson’s ratio (0.33)
- $r$: Mean precipitate radius (nm)
- $\lambda = \dfrac{2r}{\sqrt{3f_v}}$: Precipitate spacing

---

## Impact

- **Cut process optimization time by >95%**: Aging schedule selection reduced from hours of simulation to milliseconds per recommendation.
- **Enables energy and cost-efficient alloy design**
- **Integrates Thermo-Calc simulation, Orowan physics, and machine learning**: A complete digital workflow, directly relevant to industrial alloy processing.

**Completely eliminates the trial and error framework to find out the best ageing schedule for a target yield strength!**

## Future Improvements

- **Generalization to Other Alloys:**  
  Extend the approach to handle a broader range of alloy systems by including additional alloy compositions (e.g., multi-component Al–Cu–Mg or Ni-based alloys) in the training data and retraining the surrogate model. This would allow the tool to recommend heat-treatment schedules for a wide variety of industrial alloys.

- **Composition as Input Feature:**  
  Incorporate alloy composition (wt% of each element) as an input feature to the machine learning model. This would enable prediction and inverse design of yield strength and process schedules for any alloy within the simulated composition window.

## Required Files:

- **Thermo-Calc Project file:** Al-Cu Project.tcu
- **Code:** Al_Cu_Inverse_Design.ipynb
- **Dataset generated from Thermo-Calc:** PRISMA Dataset.csv
