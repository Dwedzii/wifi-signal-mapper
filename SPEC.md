# Specification: Wi-Fi Signal Mapper

## 1. Goal and Users
* **Goal:** Create a lightweight application that reads Wi-Fi RSSI log data recorded across a physical floor plan and generates a visual heatmap saved as a PNG image.
* **Target Users:** Network administrators, students, or home users wanting to diagnose Wi-Fi dead zones.

## 2. Context
* **Hardware:** Any standard x86-64 or ARM64 computer (macOS / Windows / Linux).
* **Software & Runtime:** Python 3.10+
* **Libraries:** pandas, matplotlib, scipy, numpy

## 3. Requirements
* **R1:** The tool must accept an input CSV file containing at least 20 spatial data points with (x, y) coordinates and RSSI signal strength values (in dBm).
* **R2:** The tool must perform 2D spatial interpolation across unmeasured grid points.
* **R3:** The tool must output a color-coded heatmap saved as a standard `.png` image file.
* **R4:** The visualization must include a legible colorbar correlating color gradient to RSSI values in dBm.
* **R5:** The application must display an error message and exit cleanly if the input CSV file contains fewer than 20 points or missing fields.

## 4. Constraints
* **Time Constraint:** Core features developed and tested within 3 weeks.
* **Demo Limit:** Renders heatmap PNG in under 10 seconds during a 10-minute live demo.

## 5. Interfaces
### Input Example (`measurements.csv`)
```csv
x,y,rssi
0.0,0.0,-42
1.5,2.0,-55
3.0,0.5,-68
