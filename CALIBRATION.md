# Calibration

Sample: **150 pump.fun launches**, measured 40–120 minutes after creation.

Outcome is measured from the price 10 seconds after launch, i.e. a sniper's entry:

- **up**: migrated, or the price reached at least 2× at some point;
- **dump**: the price never got above 1.3×;
- **flat**: everything in between.

Base rates: dump 83%, flat 5%, up 11%.

## Signals

| Signal             | Seen in   | Dump if present | Dump if absent | Up if present | Up if absent | Log-odds of dump |
| ------------------ | --------- | --------------- | -------------- | ------------- | ------------ | ---------------- |
| bundle             | 12 (8%)   | 92%             | 83%            | 8%            | 12%          | 0.49             |
| bundleSmall        | 14 (9%)   | 71%             | 85%            | 14%           | 11%          | -0.83            |
| bundleHold         | 18 (12%)  | 89%             | 83%            | 6%            | 12%          | 0.35             |
| devDumpedEarly     | 35 (23%)  | 89%             | 82%            | 6%            | 13%          | 0.47             |
| devSoldMost        | 75 (50%)  | 80%             | 87%            | 15%           | 8%           | -0.47            |
| devSoldPart        | 2 (1%)    | 100%            | 83%            | 0%            | 11%          | 0.03             |
| earlyConcentration | 14 (9%)   | 93%             | 82%            | 7%            | 12%          | 0.67             |
| linkedToDev        | 5 (3%)    | 100%            | 83%            | 0%            | 12%          | 0.84             |
| clustered          | 8 (5%)    | 88%             | 83%            | 13%           | 11%          | 0.03             |
| freshWallets       | 1 (1%)    | 100%            | 83%            | 0%            | 11%          | -0.49            |
| serialDev          | 132 (88%) | 83%             | 83%            | 11%           | 17%          | 0.10             |
| devFresh           | 11 (7%)   | 100%            | 82%            | 0%            | 12%          | 1.63             |
| noEarlyDemand      | 66 (44%)  | 91%             | 77%            | 8%            | 14%          | 1.02             |
| bigDevBuy          | 25 (17%)  | 92%             | 82%            | 4%            | 13%          | 0.77             |

## Hand-set weights (before calibration)

AUC for "dump": **0.50** (0.5 = coin flip)

| Risk         | Launches | Dump | Up  |
| ------------ | -------- | ---- | --- |
| low 0–29     | 36       | 86%  | 8%  |
| medium 30–59 | 70       | 81%  | 14% |
| high 60+     | 44       | 84%  | 9%  |

## Fitted weights (shipped)

AUC for "dump": **0.71** (0.5 = coin flip)

| Risk         | Launches | Dump | Up  |
| ------------ | -------- | ---- | --- |
| low 0–29     | 110      | 81%  | 13% |
| medium 30–59 | 20       | 80%  | 15% |
| high 60+     | 20       | 100% | 0%  |

5-fold cross-validated AUC of the fitted weights, 20 shuffles: **0.62** (range 0.56–0.68)
