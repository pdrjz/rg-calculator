# Agile Rent Guaranty Value Calculator — Project Summary

## Overview

The ARG Value Calculator is a Leap-branded, operator-facing sales tool designed to help multifamily property managers understand the financial impact of implementing Agile Rent Guaranty across their portfolios. The tool is a responsive, self-serve HTML file that generates a PDF export for offline sharing.

**Primary Use Case:** Sales teams link to this tool in emails and presentations, allowing operators to model their specific portfolio dynamics and see incremental revenue and guaranteed protection in real time.

**File Location:** `/mnt/user-data/outputs/arg-value-calculator.html`

---

## Core Value Propositions Addressed

1. **Revenue Expansion** — ARG approves conditionally approved and income/credit-denied applicants, expanding the qualified applicant pool and increasing new lease volume.
2. **NOI Protection** — Guaranteed rent revenue for the coverage period when tenants stop paying.
3. **Operational Simplicity** — No development work required; operator opt-in + referral to leaseasy.com.
4. **Competitive Pricing** — More affordable than similar rent guarantee products on the market.
5. **No Operator Cost** — Applicants pay the fee; operator unit economics remain intact.

---

## Calculator Inputs

### Portfolio Section

| Input | Type | Default | Purpose |
|-------|------|---------|---------|
| **Portfolio size (units)** | Number | 17,000 | Total units in operator's portfolio |
| **Current occupancy rate** | Slider (50–100%) | 92% | Baseline occupancy before ARG |
| **% of monthly applicants conditionally approved or denied for income/credit** | Slider (0–100%) | 20% | Identifies eligible applicant pool |
| **Average monthly leases closed** | Number | 150 | Monthly leasing velocity (used for timeline calculations) |
| **Average monthly rent** | Currency | $1,500 | Used to model revenue impact |
| **Annual write-offs/bad debt (optional)** | Currency | — | Optional input; enables bad debt displacement analysis |
| **Average lease term (months)** | Number (3–24) | 12 | Used for coverage % calculation |
| **Select a coverage level (months)** | Slider (1–12) | 6 | ARG protection period; drives guaranteed revenue calculations |

---

## Calculator Outputs

### 1. Projected Occupancy with ARG
- **Calculation:** Current occupancy + (denial rate × 60% conversion rate)
- **Example:** 92% + (20% × 60%) = 92% + 12% = 104% (capped at 100%)
- **Display Location:** Below Revenue Impact scenario cards in a highlighted box
- **Purpose:** Shows the occupancy outcome when ARG is fully adopted

### 2. Coverage Level Indicators
Based on slider selection (1–12 months), displays:
- **Lite Coverage (1–3 months):** Good for portfolios where possession is quickly regained after lease default and apartments are easily backfilled.
- **Average Coverage (4–7 months):** Ideal for portfolios that see a normal timeline to regain possession and backfill newly vacated apartments.
- **High Coverage (8–12 months):** For portfolios that experience extended timelines when regaining possession and backfilling apartments. Please note that higher levels of selected coverage can result in increased resident fees and decrease the leasing velocity benefits of the program.

### 3. Revenue Impact by Adoption Rate (Collapsible Scenario Cards)

Three fixed adoption tiers are shown: **10%, 20%, 25%**

**Initial State (Collapsed):**
- Displays adoption percentage only

**Expanded State (On Click):**
- **New lease revenue** — Year 1 revenue accounting for ramp-up timeline
- **New leases (annualized)** — Number of leases at that adoption tier (extrapolated annualized)
- **Year 1 guaranteed via ARG** — ARG-guaranteed protection for the coverage period

**Year 1 Calculation Logic:**
- All adoption tiers reach adoption in Months 1–2 (1.5 month ramp period)
- Linear ramp: Operators average 50% of full adoption during ramp period, then full adoption for remaining 10.5 months
- Formula: `(monthly_revenue × 0.5 × 1.5 months) + (monthly_revenue × 10.5 months) = Year 1 revenue`
- Guaranteed = Year 1 revenue × (coverage months ÷ lease term)

### 4. Write-off Impact Analysis (Optional)

**Display Condition:** Only shown if operator enters annual bad debt amount

**Metrics:**
- Your current annual write-offs
- ARG guaranteed revenue at 10% adoption
- Potential write-off reduction (capped at the lesser of guaranteed revenue or current write-offs)

**Full Bad Debt Displacement Badge:** 
- Appears when ARG guaranteed revenue ≥ operator's annual write-offs
- Changes color to green and displays: "Potential Full Bad Debt Displacement"
- Signals that ARG not only covers losses but provides additional protection upside

### 5. Getting Started Callout

Static messaging below scenarios:
> "Most operators easily reach 10% adoption by actively referring renters during the leasing process. This is your starting point for seeing tangible revenue lift and NOI protection from the program."

---

## Key Features

### 1. Responsive Design
- Mobile, tablet, and desktop optimized
- Collapsible scenario cards for cleaner mobile experience
- Touch-friendly sliders and inputs

### 2. Leap Brand Compliance
- Purple (#702572) dominant on all surfaces
- Gold (#A39366) for guaranteed/important metrics
- Stolzl typeface for headings; Inter for body
- 14px corner radius on buttons and cards; 20px on larger containers
- Consistent 48px left-side spacing across header, main, footer

### 3. Dynamic Calculations
- **Occupancy lift** driven by denial rate input (no flat assumptions)
- **Coverage percentage** calculated as `coverage_months ÷ lease_term`
- **Scenario revenue** accounts for Year 1 ramp-up (not pure annualization)
- **Bad debt displacement** calculated as minimum of guaranteed revenue or current write-offs (prevents inflated claims)

### 4. PDF Export
- **Filename:** `ARG-Value-Calculator-Results.pdf`
- **Contents:** All input values, projected occupancy, scenario cards, write-off analysis (if provided), disclaimers
- **Branding:** Maintains Leap styling; includes header with timestamp
- **Disclaimer:** "This calculation is based on the inputs provided and represents a projection. Actual results may vary based on your specific applicant pool, lease term mix, and operational factors."

### 5. Applicant Fee Transparency
- **Callout location:** Below coverage level slider
- **Message:** "Renters pay a one-time fee (typically less than 60% of monthly rent on average, based on individual applicant risk factors) to secure the protection you need to approve their lease. Your unit economics remain intact."
- **Frames ARG as operator-cost-free**

### 6. Competitive Positioning
**Integrated into three locations:**

**Intro Section (Purple Callout Box):**
> "Unlike deposit alternatives that make move-in more affordable, ARG actually expands your qualified applicant pool—approved applicants you would otherwise have to deny. Implementation is seamless: no development work required, just operator opt-in. Plus, our pricing is more competitive than similar rent guarantee products on the market. Leap also offers Deposit Replacement for operators using compatible property management software."

**Closing Copy:**
> "ARG gives you a competitive edge in a tight leasing environment. By expanding your pool of qualified applicants with minimal operational friction, you can hit occupancy targets faster and protect revenue from default risk—all while renters cover the cost of that protection."

**PDF:** Same positioning carries through

---

## Recent Refinements

### Phase 1: Sales Leader Feedback (Implemented ✓)
- ✓ Dynamic occupancy lift based on denial rate (60% conversion assumption)
- ✓ Fee transparency callout explaining applicant cost structure
- ✓ Industry benchmark messaging ("Getting started" callout)
- ✓ Dual CTAs: "Download results as PDF" + "Talk to our Team" (links to operator application form)
- ✓ Competitive positioning in intro, closing copy, and PDF

### Phase 2: Operator Perspective (Partially Addressed)
- ✓ Bad debt comparison with full displacement detection (#9)
- ✓ Timing / Year 1 benefit with realistic ramp-up (#4)
- ✓ Clarified monthly-based denial rate input
- ✓ Optional monthly leasing activity input (for timeline calculations)
- — Custom adoption scenario flexibility (#6) — deferred
- — Guaranteed revenue clarity (#5) — messaging in place; definition callout TBD
- — Applicant pool context (#7) — optional input available
- — Lease term mix (#8) — blended average; advanced segmentation TBD

### Phase 3: UI/UX Polish (Implemented ✓)
- ✓ Projected occupancy box moved below scenario cards
- ✓ Applicant fees callout moved below coverage level slider
- ✓ Scenario cards collapsible (click to expand/collapse)
- ✓ Scenario card labels simplified: "New lease revenue" (not Year 1 lease revenue)
- ✓ Timeline callout removed from scenario cards (cleaner initial state)
- ✓ Proper spacing between write-off analysis and "Getting started" blurb

---

## Technology Stack

- **Language:** HTML5 + CSS3 + Vanilla JavaScript
- **PDF Export:** html2pdf.js (CDN: https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js)
- **Fonts:** 
  - Stolzl (headings) — embedded as base64 WOFF
  - Inter (body, labels) — Google Fonts
- **CSS Variables:** Full design token system for colors, spacing, typography, radii, shadows
- **Responsive:** Mobile-first approach; media query breakpoint at 768px

---

## Usage Flow

1. **Operator navigates to calculator** (shared link in email/deck)
2. **Inputs portfolio details** (size, occupancy, denial rate, monthly leases, avg rent, lease term)
3. **Optionally adds bad debt** to see displacement potential
4. **Adjusts coverage level** to see protection tier and fee implications
5. **Clicks scenario cards** to expand and see Year 1 revenue and guaranteed protection
6. **Downloads PDF** to share internally or discuss with sales team
7. **Contacts Leap** via "Talk to our Team" button

---

## Open Items & Considerations

### For Future Enhancement
- **Custom adoption scenarios** — Allow operators to input specific adoption % instead of fixed tiers
- **Guaranteed revenue clarity callout** — Educational tooltip explaining what "guaranteed" means, coverage limits, and claim process
- **Portfolio segmentation** — Handle mixed portfolios (Class A, workforce, student) with separate lease terms and occupancy baselines
- **Sensitivity analysis** — Show impact of ±10% adoption variance
- **Applicant volume context** — Optional "annual applications" input to show eligible applicant pool size

### Current Constraints
- Single blended lease term (assumes portfolio mix is relatively consistent)
- Fixed 60% conversion rate (based on partner data; not operator-adjustable)
- Three adoption tiers (10/20/25%) are illustrative; actual adoption depends on operator execution
- No staged rollout modeling (e.g., pilot in one community before portfolio-wide)

---

## Sales Enablement Notes

### Strongest Use Cases
- **Lease-up situations** — Operators facing occupancy pressure see immediate upside
- **Bad debt concerns** — Operators with high write-offs see concrete displacement math
- **Tight labor markets** — Leasing teams see velocity and referral simplicity
- **Mixed portfolios** — Default blended inputs work for portfolio-level ROI conversations

### Common Objections & Responses
- **"Why 60% conversion rate?"** → Based on partner data; operators can adjust denial rate to model their specific pool
- **"What if we don't hit 10% adoption?"** → Tool shows Year 1 benefit accounting for ramp-up; adoption depends on leasing team execution
- **"Doesn't this cannibalize my own approvals?"** → ARG approves applicants you would otherwise *deny*; expands your pool, doesn't replace existing approvals
- **"How does this compare to deposit waiver?"** → ARG expands qualified pool; deposit waiver just makes move-in cheaper for already-qualified tenants

### Talking Points
- "You bring your numbers; the calculator shows your specific outcome"
- "60% of denied applicants become approvals — that's incremental occupancy you don't have today"
- "No dev work, no integration complexity — just referral and adoption"
- "Your renters pay; your unit economics stay intact"

---

## Files

**Main Deliverable:**
- `arg-value-calculator.html` — Standalone, ready-to-deploy calculator

**Supporting:**
- `ARG-VALUE-CALCULATOR-SUMMARY.md` — This document

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Aug 26, 2026 | Initial release with all core features, positioning, and operator feedback integration |

---

## Contact & Maintenance

For updates, questions, or bug reports, contact Dylan Webster (Director of Marketing and Enablement, Leap Insurance Agency LLC).
