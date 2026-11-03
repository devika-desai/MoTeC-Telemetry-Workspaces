# MoTeC i2 Pro Telemetry Analysis & DAQ Workspaces

A repository of standardized MoTeC i2 Pro analysis workspaces configured for trackside data acquisition, driver performance coaching, chassis envelope evaluation, and electronics sensor diagnostics.

Includes bundled sample log files (`.ld` / `.ldx`) to load and inspect configured worksheets without requiring a live trackside logger connection.

---

## Workspace Architecture

The included workspace configurations focus on three core operational workflows used in race engineering and trackside logging:

### 1. Driver Comparison & Delta-T (Distance Domain)
* **Domain Alignment:** Telemetry traces aligned over circuit lap distance (meters) via `F9` toggle rather than elapsed time, ensuring identical track coordinates across overlaid laps.
* **Coaching Channels:**
  * **Ground Speed & Time Slip (Delta-T):** Continuous tracking of cumulative time gain/loss across each sector and braking zone.
  * **Driver Inputs:** Superimposed throttle position (%) and brake pressure (bar/kPa) to pinpoint initial application, threshold stability, trail braking release, and throttle pickup points.
  * **Corner Apex Correlation:** Steering angle and engine RPM traces to evaluate corner-entry hesitation and minimum corner speed ($V_{\text{min}}$).

### 2. Grip Envelope & Friction Circle ($G\text{-}G$ Diagram)
* **Scatter Plot Architecture:** Lateral Acceleration ($G$) plotted on the X-axis against Longitudinal Acceleration ($G$) on the Y-axis.
* **Dynamic Filtering:** Low-speed data (<40 km/h) filtered out to remove pit lane rolling noise, isolating high-speed aero compression, mid-corner balance, and braking-to-turn-in transition limits.

### 3. Systems Health & DAQ Sensor Diagnostics
* **Electrical Rails:** Real-time monitoring of DC bus/battery voltage to detect alternator ripple, under-voltage drops, or grounding issues.
* **Powertrain Baselines:** Engine RPM, coolant/water temperatures, and oil pressure tracking across sessions to ensure operating window integrity.
* **Wheel Speed Synchronization:** Four-corner individual wheel speed channel verification (FL, FR, RL, RR) to detect lockups, excessive slip ratios, or optical/magnetic sensor pulse dropouts.

---

## File Structure

```text
motec-telemetry-workspaces/
├── data/
│   ├── Sample.ld
├── images/
│   ├── 01_Driver_Overlay_DeltaT.png
│   ├── 02_Friction_Circle_GG_Diagram.png
│   └── 03_Systems_Sensor_Health_Diagnostics.png
├── workspaces/
│   └── Performance_Trackside_Analysis.i2wsp
└── README.md
