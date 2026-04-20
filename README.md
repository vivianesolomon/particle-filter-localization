# particle-filter-localization

Particle filter for mobile robot localization, fusing BNO055 IMU and Lidar over a 10×10m 
square path with a single known landmark. Benchmarked against an EKF baseline, with 
global initialization and kidnapped robot recovery scenarios.

> Built on a code stub by **Andrew Pham**.

## What it does
- **Motion model** — IMU acceleration integrated in global frame with velocity damping (α = 0.75)
- **Correction step** — Gaussian likelihood weighting from Lidar-derived position measurements
- **Resampling** — systematic resampling every timestep; 1000 particles
- **Global localization** — unknown-start initialization with uniform particle scatter
- **Kidnapped robot recovery** — autonomous re-convergence after full particle scatter mid-run

## Key results
| Scenario | Mean error | Max error | RMS error |
|---|---|---|---|
| Known start (N=1000) | 0.176 m | 0.653 m | 0.217 m |
| Unknown start (N=1000) | 0.181 m | 0.563 m | 0.215 m |
| Kidnapped at t=10s | 0.196 m | 0.614 m | 0.230 m |
| Kidnapped at t=35s | 0.189 m | 0.552 m | 0.222 m |
| EKF baseline (Lab 3) | 0.181 m | 0.982 m | 0.219 m |

## Stack
Python · NumPy · BNO055 IMU · Lidar

## Setup
Open the notebook in Google Colab, upload the `data/` folder to Drive, mount when 
prompted, and run top to bottom.

