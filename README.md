# **Personal Productivity Index (PPI) v2.0** ⭐

[Python 3.8+](https://www.python.org/downloads/)  
[License: MIT](https://opensource.org/licenses/MIT)  
[GitHub Stars](https://github.com/Transparency-X/PPI/stargazers)  
[GitHub Issues](https://github.com/Transparency-X/PPI/issues)

**A quantitative framework to measure and improve your digital productivity and wellness using native device data (iOS/Android) or cross-platform tools.**

PPI v2.0 translates raw screen time and app usage into an **actionable score (0–100)** across four pillars: **Focus, Efficiency, Wellness, and Recovery**. It’s designed for individuals, teams, and organizations to track, analyze, and optimize their digital habits.

---

## **📌 Features**

✅ **Four Core Pillars:**

- **Focus:** Measure interruptions via device pickups.
- **Efficiency:** Track time spent in productive vs. distracting apps.
- **Wellness:** Monitor digital boundaries (sleep, late-night usage).
- **Recovery:** Encourage screen-free time and digital detox.

✅ **Automated Tracking:**

- Python script to process CSV exports from **RescueTime, Digital Wellbeing, or Screen Time**.
- iOS **Shortcuts** and Android **Tasker** templates for manual logging.

✅ **Customizable:**

- Define your own **app categories** (Deep/Shallow/Distraction/Neutral).
- Adjust **benchmarks** and **weights** to fit your goals.

✅ **Gamification:**

- Unlock **badges** (e.g., "Deep Work Champion").
- Complete **challenges** (e.g., "7-Day Distraction Detox").
- Compete on **team leaderboards**.

✅ **Visualization:**

- Generate **trend charts**, **pillar breakdowns**, and **app usage heatmaps**.
- Export **weekly/monthly reports** (Markdown, PDF, or CSV).

✅ **Team/Organization Ready:**

- **Anonymous benchmarking** for teams.
- **Workshops** and **coaching** templates for Transparency-X.

---

## **🚀 Quick Start**

### **1️⃣ Prerequisites**

- **Python 3.8+** (for automation scripts).
- **Device Access:**
  - iOS: **Screen Time** (native).
  - Android: **Digital Wellbeing** (native) or **ActionDash/StayFree** (for CSV exports).
  - Cross-Platform: **RescueTime** or **ActivityWatch**.

### **2️⃣ Installation**

Clone the repository and install dependencies:

```bash
git clone https://github.com/Transparency-X/PPI.git
cd PPI
pip install -r requirements.txt
```

> **Requirements:** `pandas`, `matplotlib`, `streamlit` (for dashboard).

---

### **3️⃣ Set Up Your App Categories**

Edit the `app_categories.json` file to classify your apps:

```json
{
  "Notion": "D",
  "Excel": "D",
  "VS Code": "D",
  "Slack": "S",
  "Gmail": "S",
  "Instagram": "X",
  "TikTok": "X",
  "Calculator": "N"
}
```

> **Categories:**
>
> - **D (Deep):** High-value work tools.
> - **S (Shallow):** Necessary but low-value (e.g., email).
> - **X (Distraction):** Time-wasters (e.g., social media).
> - **N (Neutral):** Excluded from calculations (e.g., health apps).

---

### **4️⃣ Collect Data**

#### **Manual Method (No Coding)**

- **iOS:** Go to **Settings > Screen Time > See All Activity** → Export pickups and app usage.
- **Android:** Use **Digital Wellbeing > Dashboard** or **ActionDash/StayFree** → Export CSV.
- **Cross-Platform:** Use **RescueTime** → Export CSV from the dashboard.

#### **Automated Method (Python)**

Run the script to process CSV data:

```bash
python calculate_ppi.py --input your_data.csv --output ppi_report.md
```

> **Example CSV Format:**
>
>
> | Date       | App       | Time (mins) | Pickups |
> | ---------- | --------- | ----------- | ------- |
> | 2026-05-15 | Notion    | 120         | 0       |
> | 2026-05-15 | Instagram | 45          | 15      |
>

---

### **5️⃣ Calculate Your PPI**

The script will output:

- **PPI Score (0–100)** and **pillar breakdown**.
- **Trends** (if historical data is provided).
- **Recommendations** for improvement.

**Example Output:**

```markdown
# PPI Report (May 16, 2026)
- **PPI Score:** 78.5 (Productive)
- **Focus Index:** 80 (+5 from last week)
- **Efficiency Index:** 75 (-3)
- **Wellness Index:** 90 (+10)
- **Recovery Index:** 60 (0 screen-free days)

**🎯 Top Wins:**
✅ 5 deep work sessions (45+ mins).
✅ 0 Wellness violations.

**⚠️ Areas to Improve:**
❌ Efficiency dropped due to 2 hrs in Distraction apps.
❌ No screen-free days this week.
```

---

### **6️⃣ Visualize Your Data (Optional)**

Launch the **Streamlit dashboard** to explore trends:

```bash
streamlit run dashboard.py
```

> **Features:**
>
> - **PPI Trend Line**
> - **Pillar Breakdown**
> - **App Usage Heatmap**
> - **Weekly Reports**

PPI Dashboard Preview

---

## **📊 PPI v2.0 Formula**

The **PPI score** is calculated as:  
$$  
PPI = (0.40 \times \text{Focus Index}) + (0.30 \times \text{Efficiency Index}) + (0.20 \times \text{Wellness Index}) + (0.10 \times \text{Recovery Index})  
$$


| **Pillar**     | **Weight** | **Calculation**                                                                                       |
| -------------- | ---------- | ----------------------------------------------------------------------------------------------------- |
| **Focus**      | 40%        | $100 - (\min(\text{Pickups}, 50) \times 1.5)$ (capped at 50 pickups).                                 |
| **Efficiency** | 30%        | $\frac{\text{Time in D} + (0.5 \times \text{Time in S})}{\text{Time in D+S+X}} \times 100$            |
| **Wellness**   | 20%        | $100 - (10 \times \text{Violations}) + (5 \times \text{Sleep Habits}) - (5 \times \text{Late Usage})$ |
| **Recovery**   | 10%        | $\frac{\text{Screen-Free Days}}{7} \times 100 + \text{Weekend Bonus}$                                 |


---

## **🎯 Benchmarking**


| **Score Range** | **Tier**    | **Interpretation**                          | **Action**                                  |
| --------------- | ----------- | ------------------------------------------- | ------------------------------------------- |
| **90–100**      | Elite       | Exceptional focus and digital wellness.     | Maintain habits; set advanced goals.        |
| **70–89**       | Productive  | Strong balance, minor distractions.         | Identify 1–2 weak pillars to improve.       |
| **50–69**       | Fragmented  | High context-switching or distraction time. | Implement "Focus Blocks" (45-min sessions). |
| **30–49**       | Distracted  | Device controls attention.                  | Digital reset: Delete 1–2 Distraction apps. |
| **0–29**        | Overwhelmed | Severe fragmentation.                       | Enable Downtime; use app blockers.          |


---

## **🏆 Gamification**

### **Achievements**


| **Badge**              | **Criteria**                       | **Reward**                  |
| ---------------------- | ---------------------------------- | --------------------------- |
| **Deep Work Champion** | 5+ days with >70% Efficiency Index | +5 PPI bonus                |
| **Night Owl**          | 0 Wellness violations for a week   | "Sleep Master" badge        |
| **Focus Sprint**       | 3 consecutive days with PPI >80    | 1-hour coaching session     |
| **Digital Detox Hero** | 3+ screen-free days in a month     | Featured in team newsletter |


### **Challenges**


| **Challenge**               | **Goal**                                   | **Duration** | **Reward**                   |
| --------------------------- | ------------------------------------------ | ------------ | ---------------------------- |
| **7-Day Distraction Detox** | Delete all Distraction (X) apps            | 7 days       | +10 PPI bonus                |
| **Focus Marathon**          | 5+ deep work sessions (>45 mins) in a week | 7 days       | "Productivity Booster" badge |
| **Sleep Hygiene Week**      | 0 pickups 30 mins before/after sleep       | 7 days       | +5 Wellness Index bonus      |


---

## **🛠️ Customization**

### **Adjust Weights**

Modify the weights in `calculate_ppi.py` to prioritize certain pillars:

```python
# Default weights (v2.0)
WEIGHTS = {
    "focus": 0.40,
    "efficiency": 0.30,
    "wellness": 0.20,
    "recovery": 0.10
}
```

### **Set Custom Benchmarks**

Edit the `benchmarks.json` file to define your own tiers:

```json
{
  "elite": 90,
  "productive": 70,
  "fragmented": 50,
  "distracted": 30
}
```

---

## **📂 Project Structure**

```
PPI/
├── README.md                  # This file
├── LICENSE                    # MIT License
├── requirements.txt           # Python dependencies
├── app_categories.json        # User-defined app categories
├── benchmarks.json            # Custom benchmark thresholds
├── calculate_ppi.py            # Core PPI calculation script
├── dashboard.py               # Streamlit dashboard
├── data/                      # Sample CSV data
│   ├── screen_time.csv
│   └── rescuetime.csv
├── templates/                # Report templates
│   ├── weekly_report.md
│   └── monthly_report.md
└── docs/                      # Documentation
    ├── automation_guide.md
    ├── gamification.md
    └── visualization.md
```

---

## **🤝 Contributing**

We welcome contributions! Here’s how you can help:

1. **Fork the repository** and create a feature branch.
2. **Report bugs** or suggest features via [GitHub Issues](https://github.com/Transparency-X/PPI/issues).
3. **Submit a Pull Request** for:
  - New automation scripts (e.g., for macOS or Windows).
  - Dashboard improvements (e.g., Tableau/Power BI templates).
  - Gamification ideas (e.g., new badges/challenges).

**Contribution Guidelines:**

- Follow [PEP 8](https://peps.python.org/pep-0008/) for Python code.
- Include **tests** for new features.
- Update the **README** and **documentation** for changes.

---

## **📜 License**

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

## **🙌 Acknowledgments**

- Inspired by **Cal Newport’s "Deep Work"** and **Digital Minimalism**.
- Built with ❤️ by [Transparency-X](https://transparency-x.com).
- Special thanks to our **early adopters** for feedback and testing.

---

## **📢 Contact & Support**

- **GitHub:** [Transparency-X/PPI](https://github.com/Transparency-X/PPI)
- **Email:** [ppi@transparency-x.com](mailto:ppi@transparency-x.com)
- **Slack:** Join our [#ppi channel](https://transparency-x.slack.com/archives/ppi) for discussions.

---

**🔹 Try it today!**  
Star this repo ⭐, fork it, and start tracking your **Personal Productivity Index** to take control of your digital life.
