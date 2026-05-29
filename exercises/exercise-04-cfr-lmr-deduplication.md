# Exercise 4: CFR/LMR Reconstruction with Duplicate Handling

---

## Overview

This is the most involved exercise of the workshop. You will run a full reconstruction using the CFR/LMR engine, starting from a query all the way through to a final product — including the deduplication step that you deliberately skipped this morning.

Deduplication is one of the most consequential and least discussed steps in assembling a paleoclimate reconstruction. The same physical record sometimes appears in multiple compiled datasets, often with slight differences in chronology, variable definition, or metadata. Deciding which version to keep — or whether any version is worth keeping at all — requires scientific judgment. Different reasonable choices can produce meaningfully different reconstructions.

This exercise is designed to make that visible.

**Shared slide deck:** [Exercise 4 Slides](https://docs.google.com/presentation/d/1EonJBG4_3O6ml870S00md7PVHuawVCwrYuQbI9rL-Hw/edit?slide=id.p#slide=id.p)

---

## Part 1: Constrained Reconstruction (everyone does the same query)

In Part 1, everyone starts from the same query. Your data pool will be essentially identical. But when you get to the deduplication step, you will make your own choices — and we'll compare results at the end to see how much those choices matter.

Each reconstruction job takes approximately **[N] minutes**.

---

### Step 1: Run the Query

1. Open the PReSto custom reconstruction engine: [paleopresto.org/custom.html](https://paleopresto.org/custom.html)
2. In the bottom drop-down menu, select **LMR (Last Millennium Reanalysis)"** as the method. 
3. In the "LiPDverse Query" page, select the tab "Query Across LiPDverse", and configure the following:

| Filter | Setting |
|--------|---------|
| **Compilations** | PAGES 2k, Iso2k |
| **Archive types** | All (leave unfiltered) |
| **Interpretation** | Temperature |
| **Location filters** | [INSERT COORDINATES — e.g., Pacific focus region] |
| **Temporal Filters** | Records must span at least 1–2000 CE |

4. Run the query. Note the number of records returned before deduplication.

> **Check:** You should have approximately **50-100 raw records** before deduplication. Flag a helper if your count is very different.

---

### Step 2: Dataset-Level Deduplication

The first deduplication step identifies similar time series within an individual dataset. For each duplicate group, you need to decide which record to keep.

**Things to consider when choosing between duplicate records:**

- Which version has the longer or more complete time series?
- Interpretation: phenomenon that drove variability in this measured or inferred variable. 
- Which compilation does the record below to?
- Are there differences in the interpretation detail or seasonality that matter for your reconstruction?

Work through each flagged group. There is no single right answer — use your scientific judgment.

> **Example - Ocn-WestSpitzburg.Bonnet.2010** This dataset contain 5 similar time series split into 3 groups by the deduplication app. All metadata are identical for these records and all are strongly correlated. Older versions of Pages2kTemperature include several of these time series, while the newest iteration (v2_2_0) includes only 1. Which record(s) will you keep? 

When you've made a choice on a duplicate group, note the choices you made and why in the text box provided.

---

### Step 3: Proximity-Based Deduplication

The second deduplication step flags records that are geographically very close to each other — close enough that they may be measuring the same local climate signal. You decide whether to keep one, both, or neither.

**Things to consider:**

- Are the records from the same site or clearly different sites that happen to be nearby? (Similar records may appear in LiPDverse under different datasets when contributed by different individuals over time.)
- Do the time series correlate strongly? (A high correlation suggests they're measuring the same thing.)
- Do they cover different time periods, such that together they extend the record length?

When you've made a choice on a duplicate group, note the choices you made and why in the text box provided.

---

### Step 4: Set the Random Seed and Submit

To make results comparable across the group, everyone should use the same random seed.

**Random seed for Part 1: `[INSERT SEED]`**

Enter this seed in the **Advanced settings → Random seed** field before submitting.

Give your job a name that includes "part1" so you can find it easily (e.g., `cfr-lmr-part1-yourname`).

Submit the job.

---

### Step 5: While You Wait — Fill in Your Slide

While your reconstruction is running, set up your slide in the shared deck:

- Add your name
- Note your deduplication choices (a few bullet points is fine — what were the trickiest calls you made?)
- Leave space for two figures: a time series and a map

---

### Step 6: Capture and Upload Your Results

When your reconstruction is ready:

1. Find the **1815 CE** timestep (the Tambora eruption year).
2. Screenshot the **global anomaly map** for 1815 CE.
3. Extract a **time series** for a grid cell of your choice in the reconstructed region (record the coordinates).
4. Upload both to your slide.

We'll display everyone's slides side by side and discuss:
- How similar are the spatial patterns?
- How much spread is there in the Tambora cooling signal?
- Can you trace differences back to specific deduplication choices?

---

## Part 2: Open-Ended Reconstruction (if time permits)

If you finish Part 1 with time to spare, design and run your own reconstruction. This is a chance to start exploring the data and time period relevant to your individual project, or simply to try something you're curious about.

### Guidelines

- Choose your own compilations, archive types, region, and time period.
- You will need to run through the full deduplication workflow again.
- **Start small.** If you query too broadly you may end up with hundreds of records to deduplicate, which will take far longer than the time available. Aim for a manageable number of records (roughly 30–80) before deduplication.
- You do not need to finish — getting partway through and learning where the rough edges are is valuable.

> **Tip:** If you find yourself looking at a deduplication list with 200+ records, restart with a tighter regional or archive filter. Learning to scope a query appropriately is itself part of the skill.

Add whatever results you have to a second slide before the end of the session.

---

## Wrap-Up and Group Discussion

We'll close out Day 2 with a look at the shared slides and a conversation about what everyone found. Come ready to talk for a couple of minutes about:

- What deduplication choices did you make, and why?
- Did anything surprise you about how much (or how little) the choices mattered?
- What would you do differently if you were building a reconstruction for a paper?

This is also a good time to sketch out a plan for your individual project tomorrow. Instructors will circulate during and after dinner to help you scope something achievable for the morning session.

---

## Reporting Bugs

If something breaks or behaves unexpectedly during this exercise, please file a GitHub Issue on the PReSto repository. Good bug reports include:

1. **What you were trying to do** (copy the URL from your browser — it encodes your current settings)
2. **What you expected to happen**
3. **What actually happened** (a screenshot is very helpful)

Filing an issue is fast, keeps things organized, and directly helps us improve the platform. Your instructor will show you where to find the issue tracker if you haven't already seen it.
