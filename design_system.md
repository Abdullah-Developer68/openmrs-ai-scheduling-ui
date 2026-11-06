# OpenMRS 3.x AI-Augmented Outpatient Scheduling: Design System Specification

## 1. Design Philosophy & Foundations
The design system for the AI-augmented outpatient scheduling subsystem extends the **IBM Carbon Design System (Carbon v11)**—the official UI framework utilized by OpenMRS 3.x Microfrontends. The visual language balances high clinical density with cognitive transparency, ensuring healthcare clerks and triage personnel can rapidly distinguish between **deterministic rule-based constraints** and **probabilistic AI predictions**.

### Core Form Factor
- **Target Form Factor**: Primary Desktop Workstation (1440 × 900 px responsive layout) optimized for outpatient clinic intake counters and triage desks.
- **Minimum Viewport**: 1280 × 720 px.
- **Tablet Responsive**: 1024 × 768 px for mobile clinical cart tablets.

---

## 2. Color Palette & Token Architecture

| Token Name | Hex Code | Visual Swatch | Semantic Usage |
| :--- | :--- | :--- | :--- |
| `--navy-hospital` | `#102C57` | Navy Blue | Primary header brand, institutional authority, dominant headings |
| `--primary-ibm` | `#0F62FE` | IBM Blue | Primary user interactive controls, active navigation tabs, action buttons |
| `--primary-dark` | `#0043CE` | Deep Blue | Hover and active button states, selected table row borders |
| `--bg-canvas` | `#F4F7FB` | Soft Slate White | Application canvas background reducing glare under clinic lighting |
| `--card-bg` | `#FFFFFF` | Pure White | Data containers, modal dialog surface, data table background |
| `--text-primary` | `#161616` | Carbon Gray 100 | Primary clinical text, patient names, timestamps |
| `--text-secondary` | `#525252` | Carbon Gray 70 | Field labels, secondary identifiers, audit metadata |
| `--border-subtle` | `#E0E0E0` | Carbon Gray 30 | Table grid borders, card outlines, form element borders |
| `--ai-purple` | `#8A3FFC` | Purple 60 | Machine learning tags, model version provenance, sidecar status |
| `--ai-purple-light` | `#F6F2FF` | Purple 10 | AI prediction preview surface, inference latency cards |
| `--risk-high` | `#DA1E28` | Red 60 | High no-show probability (>60%), SHAP risk-increasing features |
| `--risk-high-light` | `#FFE3E5` | Red 10 | High-risk callout backgrounds, error alerts |
| `--risk-med` | `#F1C21B` | Yellow 30 | Medium risk (30%–60%), low confidence warnings |
| `--risk-low` | `#198038` | Green 60 | Low risk (<30%), protective SHAP features, buffer confirmed |
| `--risk-low-light` | `#DEFBE6` | Green 10 | Successful booking badge, standard slot available |

---

## 3. Typography Hierarchy

The typography strictly adheres to **IBM Plex Sans** (with fallback to system `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto`).

| Level | Size / Line Height | Weight | Usage |
| :--- | :--- | :--- | :--- |
| **Page Title** | 22px / 28px | SemiBold (600) | Top-level screen title (e.g., "Schedule Outpatient Appointment") |
| **Section Header** | 15px / 20px | SemiBold (600) | Card titles, modal headers, table group headers |
| **Body Primary** | 14px / 20px | Regular (400) | General clinical data, patient demographic strings |
| **Data Table Cell** | 13px / 18px | Regular / Medium | Slot times, provider names, unallocated slot counts |
| **Badge / Tag** | 11px / 14px | SemiBold (600) | Status pills (`AI BUFFER OPEN`, `DETERMINISTIC FULL`) |
| **Caption / Fine** | 11px / 14px | Regular (400) | Audit timestamps, TreeSHAP feature attributions, model hash |

---

## 4. Component Library & Micro-Interactions

### A. Status Badges & Pills
- **Deterministic Badges**: Flat grey background (`#E0E0E0`) with dark grey text (`#393939`) and gear icon `⚙️`, indicating a hard-coded clinical rule.
- **AI Probabilistic Badges**: Distinct light purple background (`#F6F2FF`) with violet border (`#8A3FFC`) and lightning/bot icon `⚡`, indicating model-derived insight.
- **Risk Tier Badges**:
  - High Risk: Red pill with bold white text.
  - Medium Risk: Amber pill with dark brown text.
  - Low Risk: Green pill with dark green text.

### B. Form Inputs & Buttons
- **Primary Action Button**: High-contrast blue background (`#0F62FE`), 4px border radius, 8px vertical padding, 14px horizontal padding.
- **Secondary Action Button**: White background with 1px border (`#E0E0E0`), dark text.
- **Override Dropdowns**: Clear focus ring (2px blue border), explicit options stating clinical protocol recommendations.

### C. TreeSHAP Feature Attribution Bars
- Composed of a 6px height track (`#E0E0E0`) with rounded ends.
- **Risk-Increasing Factors**: Fill color `--risk-high` (`#DA1E28`), growing from left to right.
- **Protective Attendance Factors**: Fill color `--risk-low` (`#198038`), growing from left to right with green percentage notation.

### D. Modal Dialogs & Fallback Banners
- **Modal Dialog**: Centered overlay on 50% opacity backdrop, rigid 600px width, structured into Header, Scrollable Clinical Body, and Dual-action Footer (`Cancel` vs `Confirm & Log AI Decision`).
- **System Alert Banners**: Full-width container with 1px border and bold left icon indicating Circuit Breaker state (Red = Fallback active; Amber = Low confidence human review).
