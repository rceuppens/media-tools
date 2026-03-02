# A/B Test Sensitivity Calculator by Ruben Ceuppens

An interactive, browser-based tool for planning and evaluating A/B tests on digital advertising campaigns. Enter your impression volumes and observed CTR/engagement rate differences to instantly visualise statistical power and minimum detectable effects.

---

## What It Does

This tool helps digital marketers, growth analysts, and media planners answer two key questions before and after running A/B tests on ad creatives:

- **Given my impression volume** — what is the smallest CTR or engagement rate difference I can reliably detect?
- **Given my observed difference** — how many impressions do I need to confirm it is statistically significant?

---

## Features

- **Minimum Detectable Effect (MDE) curves** plotted on a log scale for both α = 0.05 (strict) and α = 0.10 (lenient) significance thresholds
- **Impressions input** — enter any value from 100 to 10M and see a live marker dropped onto the chart with the exact MDE
- **CTR / ER difference input** — enter your observed difference in percentage points and see a horizontal reference line showing whether your result clears the detection threshold
- **Verdict banner** — automatically tells you whether your difference is detectable at α = 0.05, α = 0.10 only, or not yet detectable, with the required sample size to reach significance
- **Green shading** above the MDE curve to visually distinguish the detectable zone from the underpowered zone
- Zero build steps, zero dependencies — a single self-contained HTML file

---

## Statistical Methodology

The calculator uses a **two-proportion z-test** — the standard approach for comparing click-through rates or engagement rates between two variants.

**Minimum Detectable Effect formula:**

```
MDE = (z_α/2 + z_β) × √(2 × p₀ × (1 − p₀) / n)
```

**Required sample size formula:**

```
n = 2 × p₀ × (1 − p₀) × ((z_α/2 + z_β) / d)²
```

**Fixed assumptions:**
| Parameter | Value |
|---|---|
| Baseline CTR | 1.0% |
| Statistical power (1 − β) | 80% |
| Test type | Two-tailed |
| Significance levels | α = 0.05 and α = 0.10 |

> These assumptions reflect typical display advertising benchmarks. If your baseline CTR differs significantly, the MDE values will scale accordingly — lower baseline CTRs require larger relative lifts to reach significance.

---

## When To Use This Tool

- **Pre-campaign planning** — determine whether your expected impression volume gives you sufficient statistical power before launching a test
- **Post-campaign analysis** — check whether an observed difference in CTR or engagement rate between two creatives is statistically meaningful or within the margin of noise
- **Media planning** — set minimum impression thresholds in briefs to ensure A/B tests are adequately powered
- **Stakeholder communication** — visually explain why a small observed difference may not be statistically significant

---

## Usage

No installation required. Open `index.html` in any modern browser.

```bash
git clone https://github.com/rceuppens/ab-test-calculator.git
cd ab-test-calculator
open index.html
```


---

## Tech Stack

- **Vanilla HTML/CSS/JavaScript** — no frameworks, no build tools
- **[Chart.js 4.4](https://www.chartjs.org/)** — loaded via CDN for chart rendering
- **[DM Sans](https://fonts.google.com/specimen/DM+Sans)** — loaded via Google Fonts
- Single file, fully self-contained, works offline once loaded

---

## Limitations

- Assumes equal sample sizes across both variants
- Baseline CTR is fixed at 1.0% — suitable for display and programmatic advertising; may not reflect search, social, or email benchmarks
- Power is fixed at 80% — standard convention, but higher-stakes decisions may warrant 90%
- Does not account for multiple testing corrections (e.g. Bonferroni) if running more than one simultaneous test

---

## Related Concepts

`A/B testing` `statistical significance` `minimum detectable effect` `sample size calculator` `click-through rate` `engagement rate` `two-proportion z-test` `statistical power` `type I error` `type II error` `digital advertising` `ad creative testing` `conversion rate optimisation` `CRO` `media planning` `programmatic advertising`

---

## License

MIT — free to use, adapt, and share.
