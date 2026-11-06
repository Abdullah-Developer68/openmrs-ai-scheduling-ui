# OpenMRS 3.x — AI-Augmented Outpatient Scheduling Prototype

This repository contains the interactive frontend prototype, complete Carbon Design System specifications, and architectural vector design files for the **AI-Augmented Outpatient Appointment Scheduling Subsystem** in **OpenMRS**.

Developed for **CSE325 – Software Construction and Development**, COMSATS University Islamabad.

**Authors:**
* **Abdullah** (Registration Number: `FA23-BSE-137`)
* **Taha Shahid** (Registration Number: `FA23-BSE-096`)
* **Group:** Group 12 (Section BSE-7B)

---

## 🚀 Live Interactive Deployment

* **Live Vercel Application:** [https://prototype-six-ecru.vercel.app](https://prototype-six-ecru.vercel.app)
* **GitHub Repository:** [https://github.com/Abdullah-Developer68/openmrs-ai-scheduling-ui](https://github.com/Abdullah-Developer68/openmrs-ai-scheduling-ui)

---

## 🎨 Design System & Visual Assets

All formal vector and compiled design assets are preserved in this repository under [`designs/`](./designs):

| Design Asset | File Path | Description |
| :--- | :--- | :--- |
| **Design System Specification** | [`design_system.md`](./design_system.md) | Complete IBM Carbon v11 Design Tokens, Color Palettes, Typography & Accessibility Specs |
| **Baseline ER Diagram (DOT)** | [`designs/existing_er_diagram.dot`](./designs/existing_er_diagram.dot) | Graphviz source for 3NF relational data model |
| **Baseline ER Diagram (PNG)** | [`designs/existing_er_diagram.png`](./designs/existing_er_diagram.png) | High-resolution compiled ERD |
| **AI-Augmented ERD (DOT)** | [`designs/ai_augmented_er_diagram.dot`](./designs/ai_augmented_er_diagram.dot) | Graphviz source for AI extension entities & foreign keys |
| **AI-Augmented ERD (PNG)** | [`designs/ai_augmented_er_diagram.png`](./designs/ai_augmented_er_diagram.png) | High-resolution compiled augmented ERD |
| **Data Flow Diagram (DOT)** | [`designs/ai_augmented_dfd.dot`](./designs/ai_augmented_dfd.dot) | Graphviz source for end-to-end 7-step prediction pipeline |
| **Data Flow Diagram (PNG)** | [`designs/ai_augmented_dfd.png`](./designs/ai_augmented_dfd.png) | High-resolution compiled DFD |
| **Screen 1 (Dashboard)** | [`designs/screen_1_existing_dashboard.png`](./designs/screen_1_existing_dashboard.png) | Baseline Registry Dashboard Screen |
| **Screen 2 (Booking)** | [`designs/screen_ai_1_booking_capacity.png`](./designs/screen_ai_1_booking_capacity.png) | AI Dynamic Slot Capacity Manager Screen |
| **Screen 3 (Modal)** | [`designs/screen_ai_2_risk_review_modal.png`](./designs/screen_ai_2_risk_review_modal.png) | Attendance Risk Review Modal Dialog |
| **Screen 4 (Forecast)** | [`designs/screen_ai_3_engagement_hub.png`](./designs/screen_ai_3_engagement_hub.png) | Clinic Attendance Forecast & Engagement Hub |

---

## ⚡ 6 AI Operational States Implemented

The prototype features an interactive state switcher toolbar allowing clinical reviewers to test all 6 machine learning behavioral states:

1. **State 1: Normal Active Flow:** Calibrated XGBoost non-attendance score (`74.2%`), high model confidence (`92%`), and dynamic buffer assignment.
2. **State 2: Non-Blocking Loading:** Sub-50ms sidecar inference simulation with non-blocking Carbon skeleton placeholders.
3. **State 3: Tri-Layered Confidence Display:** Calibrated probability + confidence interval + horizontal TreeSHAP attribution tracks.
4. **State 4: Low-Confidence Warning:** Guarded state (<70% confidence) requiring mandatory human clerk override with rationale capture.
5. **State 5: Circuit Breaker Fallback:** Simulated microservice outage/timeout (>100ms); system falls back instantly to deterministic OpenMRS rules.
6. **State 6: Cold-Start Empty State:** Infant or first-time patient handling with unindexed visit history; assigns neutral population baseline.

---

## 💻 Tech Stack

* **UI Framework:** React 18 (Components, State Hooks, Reactive Triggers)
* **Styling & Layout:** Tailwind CSS & IBM Carbon Design System v11
* **Deployment:** Vercel Global Edge Network
* **Version Control:** Git & GitHub CLI
