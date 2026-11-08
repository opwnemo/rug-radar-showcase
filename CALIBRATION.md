# Calibration

Sample: **250 pump.fun launches**, measured 40–120 minutes after creation.

Outcome is measured from the price 10 seconds after launch, i.e. a sniper's entry:

- **up**: migrated, or the price reached at least 2× at some point;
- **dump**: the price never got above 1.3×;
- **flat**: everything in between.

Base rates: dump 82%, flat 7%, up 10%.

## Signals

| Signal             | Seen in   | Dump if present | Dump if absent | Up if present | Up if absent | Log-odds of dump |
| ------------------ | --------- | --------------- | -------------- | ------------- | ------------ | ---------------- |
| bundle             | 25 (10%)  | 92%             | 81%            | 8%            | 11%          | 0.78             |
| bundleSmall        | 19 (8%)   | 68%             | 84%            | 16%           | 10%          | -0.88            |
| bundleHold         | 36 (14%)  | 81%             | 83%            | 8%            | 11%          | -0.19            |
| devDumpedEarly     | 61 (24%)  | 92%             | 79%            | 3%            | 13%          | 0.99             |
| devSoldMost        | 129 (52%) | 75%             | 90%            | 16%           | 5%           | -1.07            |
| devSoldPart        | 2 (1%)    | 100%            | 82%            | 0%            | 10%          | 0.08             |
| earlyConcentration | 26 (10%)  | 81%             | 83%            | 8%            | 11%          | -0.18            |
| linkedToDev        | 10 (4%)   | 90%             | 82%            | 0%            | 11%          | 0.33             |
| clustered          | 12 (5%)   | 83%             | 82%            | 8%            | 11%          | -0.10            |
| freshWallets       | 2 (1%)    | 100%            | 82%            | 0%            | 10%          | 0.08             |
| serialDev          | 128 (51%) | 77%             | 88%            | 12%           | 9%           | -0.72            |
| launchFactory      | 88 (35%)  | 93%             | 77%            | 5%            | 14%          | 1.37             |
| devFresh           | 25 (10%)  | 92%             | 81%            | 4%            | 11%          | 0.78             |
| noEarlyDemand      | 112 (45%) | 91%             | 75%            | 7%            | 13%          | 1.17             |
| bigDevBuy          | 45 (18%)  | 82%             | 82%            | 4%            | 12%          | -0.05            |

## Hand-set weights (before calibration)

AUC for "dump": **0.50** (0.5 = coin flip)

| Risk         | Launches | Dump | Up  |
| ------------ | -------- | ---- | --- |
| low 0–29     | 17       | 65%  | 18% |
| medium 30–59 | 153      | 84%  | 11% |
| high 60+     | 80       | 83%  | 8%  |

## Fitted weights (shipped)

AUC for "dump": **0.79** (0.5 = coin flip)

| Risk         | Launches | Dump | Up  |
| ------------ | -------- | ---- | --- |
| low 0–29     | 120      | 70%  | 17% |
| medium 30–59 | 68       | 91%  | 6%  |
| high 60+     | 62       | 97%  | 3%  |

5-fold cross-validated AUC of the fitted weights, 20 shuffles: **0.73** (range 0.69–0.75)
