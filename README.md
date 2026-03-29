# Sub_oil_v00
Sub-source spill oil sim v00
This Python code is a GUI-based subsea oil spill simulator that visualizes the spread of oil leaks underwater, based on the Hong Ji et al. (2020) model using a VOF (Volume-of-Fluid) approach combined with a realizable k-ε turbulence model. Here’s a concise breakdown:



1. Physics Engine (`OilSpillPhysics`)

^ Implements a 2D semi-analytical oil spill model.
^ Simulates:

  ^ Oil fraction (F_o) – volume-of-fluid representation of oil concentration.
  ^ Turbulent kinetic energy (k) and dissipation (ε) – using a simplified k-ε turbulence closure.
  ^ Velocity field (u, v) – combination of jet, buoyancy, and background current.
  ^ Plume trajectory – tracks oil rise due to buoyancy and current advection.
^ Time evolution is handled with a time-stepping loop; no heavy PDE solvers, so the GUI remains responsive.



2. GUI Components

^ PyQt5 used for all interface elements:

  ^ Parameter input panel (`ParamPanel`) to adjust leak rate, oil density, current, etc.
  ^ Preset cases from the Hong Ji paper for easy scenario selection.
^ Styled widgets:

  ^ Buttons, labels, spin boxes, and cards use a dark professional theme.
  ^ Colors emphasize clarity: oil in amber/orange, turbulence in deep blue → yellow gradient.



3. Visualization (`PropagationCanvas`)

^ Matplotlib integration with Qt (`FigureCanvas`) for interactive plots.
^ 2×2 grid showing:

  1. Oil volume fraction
  2. Turbulent kinetic energy
  3. Velocity field (magnitude + quiver arrows)
  4. Plume trajectory and correlation of R₁ vs R (dimensionless ratios of plume velocities)
^ Supports real-time updates per simulation frame and clearing/resetting.



4. Simulation Threading (`SimWorker`)

^ Runs simulations in a separate QThread to avoid freezing the GUI.
^ Emits `done` or `error` signals back to the main interface.



5. Color Maps

^ Custom colormaps for:

  ^ Oil: black → amber → white
  ^ Turbulence: deep-blue → cyan → yellow
^ Designed for dark-themed GUI readability.



6. Key Features

^ Semi-analytical approach allows fast simulation of plume evolution.
^ Handles buoyancy-driven rise, jet spreading, surface accumulation, and downstream entrainment.
^ Provides quantitative metrics (e.g., R₁, turbulent energy) and visual insight.



In short, it’s a desktop application for studying and visualizing subsea oil leak propagation, optimized for interactive exploration of different leak scenarios without heavy numerical solvers.

