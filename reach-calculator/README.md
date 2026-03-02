# Paid Reach Estimator

A lightweight, browser-based tool to forecast accumulated unique reach across a paid Facebook campaign, before you launch.

Built as a single HTML file with no dependencies beyond Chart.js.

---

## What It Does

The tool estimates how many unique people your campaign will reach over time, based on your target audience size, estimated post reach, campaign duration, and posting frequency. It accounts for the fact that the same person can be reached multiple times, applying a diminishing returns model to project true unique reach.

A reachability ceiling can be applied to correct for the tendency of Facebook's algorithm to re-serve ads to the same users, which causes naive models to overestimate total reach.

---

## How to Use It

Open `index.html` in any modern browser — no installation or server required.

### Inputs

| Field | Description |
|---|---|
| Target Audience Size | The estimated audience size from Facebook Ads Manager |
| Est. Post Reach | Facebook's estimated reach per post for your budget. Can be entered manually or calculated from CPM inputs |
| Campaign Duration | Length of the campaign in months |
| Ads per Week | Number of distinct ad creatives served per week |
| Reachability Ceiling | The maximum percentage of your audience considered realistically reachable (default: 70%) |

### CPM Calculator (optional)

Toggle on **Calculate Est. Post Reach from CPM** to derive post reach from budget parameters instead:

| Field | Description |
|---|---|
| Budget per Post (€) | Spend allocated per individual post |
| CPM (€) | Cost per 1,000 impressions |
| Est. Frequency | Average number of times one person sees the ad |

The formula used is: `Est. Post Reach = (Budget ÷ CPM × 1,000) ÷ Frequency`

### Output

- **Final Reach** — estimated unique people reached by end of campaign
- **Reach Growth Chart** — cumulative reach curve as number of ads increases
- **Milestone markers** — number of ads needed to reach 25%, 50%, and 75% of audience
- **Saturation alert** — warns when additional ads are likely to yield minimal new reach

---

## Formula

Accumulated reach is modelled using a probability-based diminishing returns formula:

```
Accumulated Reach = Max Reachable × (1 - (1 - r)^N)
```

Where:

- `Max Reachable` = Target Audience × Reachability Ceiling %
- `r` = reach rate per ad = Est. Post Reach ÷ Target Audience
- `N` = total number of ads = Ads per Week × (Duration in months × 4.33)

The logic: each ad has a probability `r` of reaching any given person. The probability of never being reached after N ads is `(1 - r)^N`. Flipped, this gives the probability of being reached at least once.

The reachability ceiling corrects for the fact that Facebook's algorithm tends to concentrate delivery on the same subset of users, meaning the full audience is never truly reachable in practice.

---

## Credits

Designed by **Ruben Ceuppens**
