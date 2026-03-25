# Inverse Design of 1D Photonic Crystals

## 📌 Overview
This project explores the **inverse design of 1D photonic crystals (Bragg stacks)**.
Designing photonic nanostructures is inherently challenging due to the **complex, non-linear relationship between structure and optical response**. Traditional approaches rely heavily on forward simulations and parameter sweeps, which are computationally expensive and do not scale well with increasing design complexity. 
Leveraging computational design approaches can enable more direct and efficient exploration of the design space. \
Here, by integrating the Transfer Matrix Method (TMM) with gradient-based optimization, a framework for the systematic design of multilayer structures that meets specified optical targets while remaining physically consistent is developed.


## 🧠 Key Idea

We solve the inverse problem by directly optimizing the structure:
Thickness → TMM → Reflectance → Loss(target)


## ⚙️ Methodology

### 1. Physical Model (TMM)
- Uses the **Transfer Matrix Method (TMM)** to compute optical response. Implemented in **PyTorch**


### 2. Parameterization of Structure
- Multilayer stack with alternating refractive indices:
  - $n_\mathrm{1} = 1.45 $  
  - $n_\mathrm{2} = 2.0 $
- Physical bounds ($10–100 \mathrm{nm}$) are ensured
- Practical fabrication constraints were considered in the selection of design parameters and in the formulation of the problem.


### 3. Inverse Design (Optimization)
We directly optimize layer thickness: \
Initialize thickness → Compute spectrum (TMM) → Compare with target → Update 
- Optimizer: **Adam**
- Loss: Mean Squared Error (MSE)


### 4. Target Design 
Example target:
- High reflectance around 550 nm  
- Low reflectance elsewhere  
This produces a **bandpass / Bragg mirror-like structure**.


### 5. Validation

- Final structure evaluated using the same physics model  


## 🎯 Example Result

- Target: Narrow high-reflectance band at 550 nm  
- Output: Optimized multilayer stack  
- Result: Physically valid reflectance spectrum closely matching the target  



## 🔧 Future Work
- Extension to:
  - 2D photonic crystals and metasurfaces
- Hybrid models:
  - Physics + neural networks


## 📦 Requirements

```bash
pip install numpy torch matplotlib tqdm
