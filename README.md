# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** Dasari Lahari
**Student ID    :** 2310040036 
**Date Submitted:** 11-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**
ANS: count_clashes() calculates the number of exam conflicts for students.A clash happens when a student has two exams scheduled in the same time slot.A perfect timetable has a clash value of 0.

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**
ANS: generate_neighbor() creates a new timetable by randomly selecting one exam and moving it to a different time slot. 
All other exams stay the same.This small change allows Simulated Annealing to explore nearby solutions.

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**
ANS:This line decides whether the algorithm should accept the new solution. If the new solution is better (delta < 0) it is always accepted.If it is worse, it may
still be accepted with a probability depending on the temperature. This helps the algorithm escape local minima and explore more solutions.

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379|
| Clashes at iteration 1 |12|
| Final best clashes |3|
| Did SA reach 0 clashes? (Yes / No) |No|

**Copy the printed timetable output here:**
 Final Timetable:

  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
ANS: The number of clashes decreases quickly at the beginning, with the biggest drop occurring within the first ~100 iterations where it falls from about 12 to around 6. After that, the improvements become smaller and slower. The curve flattens after roughly 400–500 iterations, stabilizing around 3–4 clashes as the temperature becomes very low.

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |  8            |          31          |          No        |
| 0.95        |               |                      |                    |
| 0.995       |               |                      |                    |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[ YOUR OBSERVATION ]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[ YOUR ANSWER ]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 | | |
| 2 — Cooling rate | cooling_rate = ___ | | |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[ YOUR REFLECTION ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
