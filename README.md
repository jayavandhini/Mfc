# Gamma Photon Buildup Factor Simulation

This project simulates the random walk of gamma photons passing through a material slab, calculates their buildup factors, and determines the final intensity after attenuation and scattering. The simulation supports multiple materials including Aluminum, Lead, Iron, and Tungsten.


## Overview
Gamma photons passing through materials experience attenuation, scattering, and absorption. This script simulates these interactions using Monte Carlo techniques to:

- **Calculate the buildup factor**: A factor representing the total energy of photons exiting the slab relative to their initial energy.
- **Estimate the final intensity** of gamma photons after passing through the slab.

The program supports four materials:
- **Aluminum**
- **Lead**
- **Iron**
- **Tungsten**

The simulation uses random sampling to determine photon interactions such as scattering directions, energy loss, and absorption.

---

## Dependencies
The script uses the following Python libraries:

- `numpy` for numerical calculations and random sampling.

Make sure Python is installed (version 3.7 or higher).

---

## How It Works
1. The **attenuation coefficients** (total and absorption) are calculated for the given material and photon energy.
2. A random walk is simulated for each photon:
    - **Scattering**: Photon changes direction and energy.
    - **Absorption**: Photon stops moving.
    - **Transmission**: Photon exits the slab.
3. The simulation tracks the energy of all photons that exit the slab.
4. The **buildup factor (BF)** is calculated using:
   
   \[
   BF = \frac{\text{Total Exit Energy}}{N \cdot E_0 \cdot e^{-\mu L}}
   \]
   
5. The **final intensity** is estimated as:

   \[
   I_{final} = e^{-\mu L} \cdot BF
   \]

where:
- \( N \): Number of photons
- \( E_0 \): Initial photon energy
- \( \mu \): Attenuation coefficient
- \( L \): Thickness in mean free paths

---

## Parameters
The key parameters used in the simulation are:
- **`muL`**: Thickness of the slab in mean free paths (default: 2.0 cm).
- **`E0`**: Initial energy of gamma photons (default: 1.0 MeV).
- **`N`**: Number of photons to simulate (default: 1,000,000).
- **`material`**: The material of the slab (options: `Aluminum`, `Lead`, `Iron`, `Tungsten`).

---

### Code Overview
The main functions in the script are:
- **`AttnCoeffs(E, material)`**: Computes attenuation coefficients based on material and energy.
- **`calculate_buildup_factor(material, muL, E0, N)`**: Simulates photon interactions and calculates the buildup factor.

---

## Output
For each material, the program prints:
1. **Buildup Factor**: Indicates the total energy contribution of scattered and transmitted photons.
2. **Final Intensity**: The final intensity of photons after passing through the material.

Example Output:
```
Buildup Factor for Aluminum: 1.2345
Buildup Factor for Lead: 1.6789
Buildup Factor for Iron: 1.4567
Buildup Factor for Tungsten: 1.8901

Final Intensity for Aluminum: 0.5678
Final Intensity for Lead: 0.7890
Final Intensity for Iron: 0.6789
Final Intensity for Tungsten: 0.8901
```

---
