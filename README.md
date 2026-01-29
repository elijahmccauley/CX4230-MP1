# SIR Epidemic Dynamics Model

## 📌 Project Overview
This project models the spread of an infectious disease through a population using the **Susceptible-Infected-Recovered (SIR)** compartmental model. By solving a system of nonlinear **Ordinary Differential Equations (ODEs)**, the project analyzes how parameters like infection rate ($\tau$) and recovery rate ($\kappa$) influence the peak infection load and the time required for the disease to die out.

## 🛠 Tech Stack
* **Language:** Python
* **Libraries:** SciPy (`solve_ivp`), NumPy, Matplotlib
* **Concepts:** Differential Equations, Numerical Integration (Runge-Kutta), Linear Stability Analysis, Jacobian Matrix

## 🧮 Mathematical Model
The system is defined by the following conservation laws:
1.  $\frac{dS}{dt} = -\tau S I$
2.  $\frac{dI}{dt} = \tau S I - \frac{I}{\kappa}$
3.  $\frac{dR}{dt} = \frac{I}{\kappa}$

Where:
* $S$: Susceptible population fraction
* $I$: Infected population fraction
* $R$: Recovered population fraction

## 🔬 Analysis & Methods

### 1. Numerical Solution
We utilized **SciPy's `solve_ivp`** with the **RK45 (Runge-Kutta)** method to numerically integrate the system over time until the infected population dropped below a significance threshold ($10^{-4}$).

### 2. Stability Analysis
We performed a **Linear Stability Analysis** on the system's fixed points. By computing the **Jacobian Matrix** and its eigenvalues, we determined the conditions under which the disease-free equilibrium is stable vs. unstable (i.e., when an outbreak occurs).

### 3. Parameter Sensitivity
We generated heatmaps to analyze the "Stopping Time" (time to extinction) across a grid of $\tau$ and $\kappa$ values.
* **Observation:** High transmission rates ($\tau$) combined with slow recovery (high $\kappa$) lead to rapid, high-peak outbreaks that burn through the population quickly.
* **Observation:** Low transmission rates lead to "flattened curves" that persist longer but infect fewer total individuals.

## 📂 File Structure
* `SIR_Model.ipynb`: Contains the ODE definitions, solver logic, and phase-space visualizations.

## 🚀 How to Run
1.  Open the notebook.
2.  Adjust `tau` (transmission rate) and `kappa` (recovery period).
3.  Run the solver to visualize the $S(t)$, $I(t)$, and $R(t)$ curves.
