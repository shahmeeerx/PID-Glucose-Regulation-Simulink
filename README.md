# PID-Based Glucose Regulation in Simulink

> **A biomedical control engineering project that simulates an "artificial pancreas" using a manually implemented PID controller to maintain blood glucose homeostasis.**

##  Project Overview
This project models the physiological feedback mechanism of the human body to manage **Diabetes mellitus**, a metabolic disorder where insulin regulation is impaired. Developed using **MATLAB Simulink**, the system utilizes a closed-loop feedback strategy to counteract sudden glucose increases—simulated as postprandial (after-meal) spikes—and return blood sugar to a healthy setpoint of **100 mg/dL**.

By bridging biomedical physiology and control engineering, this simulation provides a virtual environment to test insulin delivery strategies safely without risking patient safety.

##  Technical Specifications
* **Software:** MATLAB / Simulink.
* **System Model:** First-order linear transfer function representing glucose-insulin dynamics.
* **Control Strategy:** Manually implemented Parallel PID (constructed using individual Gain, Integrator, and Derivative blocks for full visibility).
* **Disturbance:** +100 mg/dL step input at $t = 100$s to simulate a meal spike.

##  Mathematical Modeling
The system describes how glucose levels respond over time to insulin intervention.

### Glucose System Transfer Function
The dynamics are modeled as a first-order system with a **30-second time constant ($\tau$)**:

$$G(s) = \frac{1}{30s + 1}$$

### PID Control Law
The controller calculates the simulated insulin output ($u(t)$) based on the current error ($e(t)$):

$$u(t) = K_p \cdot e(t) + K_i \int e(t) \, dt + K_d \frac{de(t)}{dt}$$

**Tuned Controller Gains:**
* **Proportional ($K_p$):** 0.8 — Provides an immediate response to deviations.
* **Integral ($K_i$):** 0.05 — Accumulates past error to eliminate steady-state offset.
* **Derivative ($K_d$):** 0.2 — Predicts future trends to reduce overshoot and oscillation.

## Performance Metrics & Results
The simulation results demonstrate the effectiveness of the controller in managing a sudden glucose spike. Key metrics were calculated programmatically using exported data.

| Metric | Value | Interpretation |
| :--- | :--- | :--- |
| **Peak Glucose** | **156.31 mg/dL** | Highest concentration reached during the response. |
| **Overshoot** | **56.31%** | The amount the glucose level exceeds the setpoint. |
| **Rise Time** | **50.00 sec** | Time to reach 90% of the peak value. |
| **Settling Time** | **240.00 sec** | Time to stay within $\pm 5\%$ of the target setpoint. |

### Stability Analysis
The system exhibits damped oscillations, eventually maintaining a stable steady state of **100 mg/dL**. This proves the PID controller is well-designed to prevent runaway glucose levels and ensure long-term homeostasis.

##  Repository Contents
* **`Project-File.slx`**: The core Simulink model with manual PID implementation.
* **`Project-Report.pdf`**: Comprehensive technical report including literature review and methodology.
* **`Model-Performance-Graphs.pdf`**: Custom MATLAB plots and performance analysis visualizations.
* **`README.md`**: Project documentation.
* **`LICENSE`**: MIT License.

## Development Team
* **Shahmeer Hussain** — [@shahmeeerx](https://github.com/shahmeeerx)

---
_© 2026 PID Glucose Regulation Project._
