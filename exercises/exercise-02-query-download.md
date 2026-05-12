# Exercise 2: Query and Download

**Day 1 | 4:15–5:00 PM | 45 minutes**

---

## Overview

The PReSto custom reconstruction engine starts with a data selection step: you define what proxy records you want to work with, and the platform queries the LiPDverse database and returns a set of matching LiPD files. In this exercise you will practice that query and download step on its own — without running any reconstruction — so that tomorrow, when you are building your own products, the data selection interface will already feel familiar.

By the end of this exercise you should be able to:
- Navigate the query interface and understand the available filter options
- Identify how different parameter choices affect what data gets returned
- Download a set of LiPD files and verify the result

**Shared slide deck:** [Exercise 2 Slides](https://docs.google.com/presentation/d/1ZKNnr0ysmj161Hcuv_Po0b6WLqjCjb1OkzEo22tvNJs/edit?slide=id.p#slide=id.p)  
Add a screenshot of your Task 3 query results and a brief note on what you found to your named slide.

---

## A Quick Glossary

These terms come up throughout the query interface. It's worth having a shared definition before you start:

| Term | Meaning |
|------|---------|
| **Archive type** | The physical material the proxy comes from (e.g., tree ring, coral, ice core, lake sediment, marine sediment, speleothem) |
| **Variable** | The climate-relevant measurement recorded (e.g., δ¹⁸O, MXD, Sr/Ca, pollen percentage) |
| **Interpretation** | The inferred climate signal — what the variable is thought to represent (e.g., temperature, hydroclimate) |
| **Compilation** | A curated, community-assembled collection of records (e.g., PAGES 2k, Iso2k, CoralHydro2k) |
| **LiPD file** | Linked Paleo Data — the standard file format used throughout the PReSto ecosystem |
| **TSid** | A unique identifier assigned to each individual time series within LiPDverse |

---

## Task 1: A Prescribed Query (~15 minutes)

Follow these steps exactly. At the end, you should get a specific number of records — use that as a check that you've done it correctly.

**Goal:** Download all lake sediment records from North America with a temperature interpretation, covering at least the interval 0–2000 CE.

### Steps

1. Open the PReSto custom reconstruction engine: [paleopresto.org/custom.html](https://paleopresto.org/custom.html)
2. Select **Query and Download** (not "Run Reconstruction").
3. Set the following filters:
   - **Archive type:** Lake sediment
   - **Interpretation:** Temperature
   - **Geographic region:** Draw a bounding box covering North America (approximately 15°N–75°N, 170°W–50°W)
   - **Time coverage:** Records must span at least 0–2000 CE
4. Run the query and note the number of records returned.
5. Download the LiPD files.

> **Check:** You should have approximately **[N] records**. If you got something very different, check your bounding box and whether your interpretation filter is set correctly.

---

## Task 2: A Different Query (~15 minutes)

**Goal:** Download coral records from the tropical Pacific with a hydroclimate or salinity interpretation.

### Steps

1. Start a new query.
2. Set the following filters:
   - **Archive type:** Coral
   - **Interpretation:** Hydroclimate or salinity (include both if the interface allows multiple selections)
   - **Geographic region:** Tropical Pacific (approximately 25°S–25°N, 120°E–270°E)
   - **Time coverage:** Records must span at least 1800–2000 CE
3. Run the query and note the number of records.
4. Download the LiPD files.

> **Check:** You should have approximately **[N] records**.

> **Reflection:** Compare the density and distribution of records between Tasks 1 and 2. Where are the data sparse? What parts of the world are well-sampled for corals vs. lake sediments?

---

## Task 3: Your Own Query (~10 minutes)

Design a query based on the climate event or period you explored in Exercise 1. Think about:
- What archive types are most likely to record your event?
- What time period do you need to cover?
- What region are you interested in?

Run the query, note how many records you get, and download the results. We won't use this data today, but you may want to come back to it when you're developing your individual project on Day 3.

> **If you get too many records (>300):** Try narrowing your region, restricting to fewer archive types, or tightening the time coverage requirement.  
> **If you get too few (<5):** Broaden your region or relax your archive type and interpretation filters.

---

## Optional Extension: Load Your Data in Python or R

If you have Python or R installed and want to explore the data you just downloaded, here are snippets to get you started.

**Python (using `lipd`):**
```python
import lipd

# Point to the folder where you saved your downloaded LiPD files
lipd.loadLipds('/path/to/your/lipd/files/')

# Get a list of all time series
ts = lipd.extractTs(lipd.getLipdNames())

# Print the archive types in your dataset
import pandas as pd
df = lipd.ts.to_df(ts)
print(df['archiveType'].value_counts())
```

**R (using `lipdR`):**
```r
library(lipdR)

# Load all LiPD files from a folder
D <- readLipd('/path/to/your/lipd/files/')

# Extract time series
ts <- extractTs(D)

# View a summary
print(sapply(ts, function(x) x$archiveType))
```

These snippets are just to connect the download to what working with the data actually looks like — you don't need to run them to complete the exercise.

---

## Wrap-Up

Before we close out Day 1, take a moment to note any terms or interface options that felt unclear. We'll be coming back to this query interface first thing tomorrow morning as the entry point into running your own reconstructions.
