# Finals Week in My Health Data

DSA210 term project, Sabancı University, Fall 2026.

My iPhone has been counting my steps for more than two years. I want to see whether my exam weeks actually look different in that data: do I move less, start my days later, go to bed later?

## Data

- **Apple Health export** from my iPhone: step count, walking distance, flights climbed. I don't have an Apple Watch, so there is no heart rate or proper sleep tracking.
- **Sabancı University academic calendar**: I use it to label each week as exam, break or regular.

Since there is no sleep data, I estimate wake-up and bedtime from the first and last steps recorded each day. It is rough, but it should show if my daily rhythm shifts during exams.

The raw export is private and is not in this repo. Only daily summaries will be uploaded.

## Hypotheses

1. I walk less during exam weeks than during regular weeks.
2. During exam weeks my day starts and ends later.
3. Break weeks are different from both.

## Plan

- Parse the Health export and aggregate it to daily values
- Label days using the academic calendar
- Exploratory analysis and visualizations
- Hypothesis tests (t-test / Mann-Whitney U)
- A simple ML model to predict activity from the features above
