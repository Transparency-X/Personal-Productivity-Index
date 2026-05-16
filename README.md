# Personal Productivity Index (PPI) v1.0 🚀

The **Personal Productivity Index (PPI)** is a data-driven framework designed to quantify cognitive performance using native telemetry data from smartphones and laptops. 

Instead of relying on "feeling" productive, PPI uses objective metrics—pickups, app categorization, and usage timestamps—to generate a daily score out of 100.

## 📊 The Core Framework

The PPI is calculated based on three weighted pillars:

| Pillar | Weight | Metric | Goal |
| :--- | :--- | :--- | :--- |
| **Focus Index** | 50% | Pickups & Unlocks | Minimize context switching |
| **Efficiency Index** | 30% | App Category Ratio | Maximize Deep vs. Distraction apps |
| **Wellness Index** | 20% | Off-hour usage | Maintain digital boundaries |

---

## 🧮 The Formula

The total score is calculated as follows:

$$PPI = (0.50 \times FI) + (0.30 \times EI) + (0.20 \times WI)$$

### 1. Focus Index (FI)
Measures the frequency of interruptions.
*   **Formula:** `100 - (Total Daily Pickups × 1.5)`
*   *Note: Minimum floor of 0.*

### 2. Efficiency Index (EI)
Measures the quality of screen time. 
*   **Categories:** 
    *   **Deep (D):** IDEs, Writing, Design, Focus tools.
    *   **Distraction (X):** Social Media, Infinite Scroll, Games.
*   **Formula:** `(Time in D / (Time in D + Time in X)) × 100`

### 3. Wellness Index (WI)
Measures the ability to disconnect.
*   **Penalty:** -10 points for every "Boundary Violation" (e.g., usage within 30 mins of waking/sleeping, or usage during scheduled 'Downtime').
*   **Formula:** `100 - (Violations × 10)`

---

## 🛠 Implementation Guide

### Data Sources
*   **iOS:** Settings > Screen Time > See All Activity (Pickups & Category usage).
*   **Android:** Settings > Digital Wellbeing (Unlocks & App Dashboard).
*   **Desktop:** [RescueTime](https://www.rescuetime.com/) or [ActivityWatch](https://activitywatch.net/) (Open Source).

### Weekly Tracking
1.  On Sunday evening, aggregate daily averages for the week.
2.  Input data into the `PPI_Calculator.xlsx` (provided in this repo).
3.  Analyze trends. A "Good" score is **>75**.

## 📈 Benchmarking
*   **90 - 100 (Flow State):** Peak performance. Minimal distractions.
*   **70 - 89 (Productive):** Solid output with minor "checking" habits.
*   **50 - 69 (Fragmented):** High context switching. Attention is divided.
*   **< 50 (Reactive):** The device is controlling the user. Immediate digital detox recommended.

---

## 📄 License
This framework is licensed under the MIT License - feel free to fork, modify, and automate!
