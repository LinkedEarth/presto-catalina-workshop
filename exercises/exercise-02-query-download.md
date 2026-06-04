# Exercise 2: Query and Download

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
| **TSid** | A unique identifier assigned to each individual time series within LiPDverse |

---

## Task 1: A Prescribed Query (~15 minutes)

Follow these steps exactly. At the end, you should get a specific number of records — use that as a check that you've done it correctly.

**Goal:** Download all lake sediment records from North America with a temperature interpretation, covering at least the interval 0–2000 CE.

### Steps

1. Launch the PReSto custom reconstruction engine from: [paleopresto.org/custom.html](https://paleopresto.org/custom.html)
2. Select **LiPD Download**
3. Authorize PReSto to use your GitHub account
4. On the query page, choose the "Query Across LiPDverse tab
5. Set the following filters:
   - **Archive type:** Lake sediment
   - **Interpretation:** Temperature
   - **Continent:** North America
   - **Time coverage:** Records must span at least 0–2000 CE
6. Update the map and note the number of datasets returned.
7. Proceed to the next step (Data Cleaning) and note the number of records/datasets.
8. Skip Data Cleaning and submit your download request.

> **Check:** At the bottom of the Data Cleaning page you should see **236 Datasets / 1729 Records**. If you got something very different, start over and check your query carefully.

---

## Task 2: A Different Query (~15 minutes)

**Goal:** Download annually resolved records from the tropical Pacific with a temperature interpretation.

### Steps

1. Start a new query following steps 1-4 from Task 1.
2. Set the following filters:
   - **Interpretation Variable:** Temperature
   - **Geographic region:** Tropical Pacific (approximately -23.5°N to 23.5°N, –235°E to -100°E)
   - **Archive Type:** Coral
   - **Minimum record length:** Records must cover a minimum of 100 years
   - **Temporal Resolution:** Records must have a median resolution of 1 year or better
3. Export a locations map
   - Click Export PNG (green button just below the map)
   - Select an appropriate region by dragging the corners of the box
   - Add a title and decide whether or not to include the query parameters and data summary
   - Click "Download PNG"
4. Run the query (skipping de-duplication again) and note the number of records.
5. Submit your request and explore your custom repository

> **Explore:** Look over the new repository created for you. Can you identify the query paramters you used? How many datasets were downloaded? How could you use this artifact?

> **Reflection:** Compare the density and distribution of records between Tasks 1 and 2. Where are the data sparse? What parts of the world are well-sampled for corals vs. lake sediments?

---

## Task 3: Your Own Query (~10 minutes)

Design a query based on the climate event or period you are planning to explore for your project. Think about:
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
pip install pylipd

# load pilipd
from pylipd.lipd import LiPD

# load lipd files (update to your local paths)
lipd = LiPD()
lipd.load(["MD98_2181.Stott.2007.lpd", "Ant-WAIS-Divide.Severinghaus.2012.lpd", "Asi-TDAXJP.PAGES2k.2013.lpd"])
```

**R (using `lipdR`):**
```r
library(lipdR)

# Load all LiPD files from a folder
D <- readLipd('/path/to/your/lipd/files/')

# Get a quick preview
summary(D)

# Extract time series
ts <- extractTs(D)

```

These snippets are just to connect the download to what working with the data actually looks like — you don't need to run them to complete the exercise.

---

## Wrap-Up

Before we close out Day 1, take a moment to note any terms or interface options that felt unclear. We'll be coming back to this query interface first thing tomorrow morning as the entry point into running your own reconstructions.
