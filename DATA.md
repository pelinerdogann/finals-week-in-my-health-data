# Data

## Source

Everything comes from the Apple Health export of my iPhone (Health app → profile → Export All Health Data). The export is one large XML file with every single measurement the phone recorded since May 2017. I don't upload it here because it is personal.

I turned it into a daily table, `data/processed/daily.csv`, with one row per day.

## Columns of `daily.csv`

| Column | Unit | Description |
|---|---|---|
| `date` | YYYY-MM-DD | Calendar day |
| `weekday` | Mon–Sun | Day of the week |
| `steps` | steps | Total steps that day |
| `distance_km` | km | Walking and running distance |
| `flights` | floors | Flights of stairs climbed. Empty means no record, i.e. 0 |
| `active_kcal` | kcal | Active energy burned (available from Sep 2021) |
| `walking_speed_kmh` | km/h | Average walking speed (available from Jun 2022) |
| `step_length_cm` | cm | Average step length (available from Jun 2022) |
| `headphone_db` | dB | Average headphone volume. Empty on days I didn't use headphones |
| `bedtime` | hours | Estimated time I went to sleep that night. Counted from midnight of that day, so 26.5 means 02:30 the next morning |
| `wake_time` | hours | Estimated time I woke up that morning (10.5 = 10:30) |
| `rest_hours` | hours | Length of the night's longest period without any steps |
| `university` | 0 / 1 | 1 if the day is on or after 1 October 2022, when I started at Sabancı |

## How some columns are calculated

**Two phones on the same day.** I changed phones twice (2018 and 2020). On a few days both phones recorded steps, so adding them up would count the same steps twice. For these days I keep the phone with the higher total.

**Bedtime and wake-up time.** I don't have an Apple Watch, so there is no real sleep data. Instead, for every night I look at the window from 18:00 to 16:00 the next day and find the longest stretch with no recorded steps. The start of that stretch is `bedtime` and the end is `wake_time`. Step records under 20 steps are ignored, so picking up the phone at night doesn't break the stretch. If the phone was left on a desk during the day, this can be off, so these columns are rough estimates.

## Coverage (university period, Oct 2022 – Nov 2026)

- 1,518 days, no missing days for steps and distance
- Bedtime / wake time missing for about 50 days (no clear rest period that night)
- Headphone volume missing for about 420 days (no headphone use)
