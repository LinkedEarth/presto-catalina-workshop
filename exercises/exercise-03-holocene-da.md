# Exercise 3: Holocene Data Assimilation

**Day 2 | 9:30 AM–12:00 PM | 150 minutes**

---

## Overview

In this exercise you will run your first paleoclimate reconstructions using PReSto's Holocene data assimilation (DA) engine. You won't need to worry about data selection or deduplication — we'll be working with a pre-configured dataset so you can focus entirely on understanding how the DA method works and how different parameter choices shape the result.

Each reconstruction job takes roughly **15 minutes** from submission to results, so plan your runs accordingly and use the wait time to read ahead or compare with a neighbor.

By the end of this exercise you should be able to:
- Submit a reconstruction job through the PReSto interface
- Read and interpret the output visualizations
- Develop intuition for how DA parameters affect the final reconstruction

**Shared slide deck:** [Exercise 3 Slides](https://docs.google.com/presentation/d/1cSmRyMkZ2pu4fIRe6kTPQuWe23G_Sx-U_eRG32qnWp0/edit?slide=id.p#slide=id.p)  
Add your figures to your named slide after each run.

---

## Setup: Authorizing PReSto with GitHub

PReSto runs your reconstruction as a GitHub Actions workflow in a repository created in your own GitHub account. Before your first run, you need to authorize this:

1. Go to [paleopresto.org/custom.html](https://paleopresto.org/custom.html) and sign in with your GitHub account.
2. Follow the prompts to grant PReSto permission to create repositories and run Actions on your behalf.
3. This only needs to be done once.

> **Note:** If you have GitHub Copilot enabled on your account, you may see it suggest changes to your reconstruction repository. You can safely ignore or dismiss these — acting on them may consume your Actions compute budget.

---

## Starting Dataset

For all three runs in this exercise, you will use the **10–12k v1.0.2** dataset (the default Holocene DA compilation assembled by Michael Erb et al.). This is pre-loaded — you do not need to run a query.

Select **"Use pre-loaded dataset"** and choose **10–12k v1.0.2** from the dropdown.

---

## Run 1: Default Settings (~15 min turnaround)

Start with everything at its defaults so you have a baseline to compare against.

### Steps

1. Select the **Holocene DA** method.
2. Select the **10–12k v1.0.2** dataset.
3. Leave all parameters at their default values.
4. Give your job a descriptive name (e.g., `holocene-default`).
5. Submit the job.
6. While you wait, read ahead to Run 2 and note what you plan to change.

### When results are ready

7. Open your reconstruction output page.
8. Screenshot the **global mean temperature time series**.
9. Screenshot the **spatial map at 6,000 BP**.
10. Upload both to your slide with the label "Run 1: Default."

---

## Run 2: Changing the Prior Window (~15 min turnaround)

The **prior window** determines which years of model simulation are used to represent background climate covariance. When the prior window includes years when the Laurentide Ice Sheet was still present, its strong covariance signature can "bleed" into reconstructed time periods after the ice sheet retreated — producing a ghost ice sheet pattern in the early Holocene.

You explored a version of this artifact in the LGMR in Exercise 1. Now you'll try to reproduce it by adjusting the prior window here.

### Steps

1. Start a new reconstruction job.
2. Same dataset: **10–12k v1.0.2**.
3. Under **DA parameters**, find the **Prior window** setting.
4. Shift the prior window to include a period with significant ice sheet coverage (your instructor will suggest a specific range).
5. Name the job something like `holocene-prior-window-test`.
6. Submit.

### When results are ready

7. Screenshot the **spatial map at 6,000 BP** and the **global mean time series**.
8. Upload to your slide labeled "Run 2: Modified Prior Window."
9. Compare with Run 1: do you see a cold anomaly in the North Atlantic / Hudson Bay region that wasn't there before? This is the ghost ice sheet.

> **Discussion prompt:** Is the ghost ice sheet a feature or a bug? What does it tell you about how sensitive DA reconstructions are to prior choices?

---

## Run 3: Single Archive Type (~15 min turnaround)

Real-world reconstructions blend many archive types — tree rings, ice cores, lake sediments, marine sediments, corals — each with different seasonal sensitivities, geographic distributions, and uncertainties. Here you'll see what happens when you restrict to just one.

### Steps

1. Start a new reconstruction job with the **10–12k v1.0.2** dataset and default DA parameters.
2. Under **Data filters**, restrict the archive type to **one of the following** (pick whichever interests you most):
   - Marine sediments
   - Ice cores
   - Lake sediments
3. Name the job to reflect your choice (e.g., `holocene-marine-only`).
4. Submit.

### When results are ready

5. Screenshot the **spatial map at 6,000 BP** and note which regions now have poor coverage (few or no proxies nearby).
6. Screenshot the **global mean time series**.
7. Upload labeled "Run 3: [Archive type] only."

> **Discussion prompt:** Where does the reconstruction degrade most when you remove most of the proxy network? What does that tell you about where we have (and don't have) good data coverage for the Holocene?

---

## Run 4: Your Choice (if time permits)

Pick a parameter or filter combination that you're curious about. Some ideas:

- Try a different single archive type and compare to your Run 3 result
- Change the **localization radius** (controls how far the influence of each proxy extends spatially)
- Combine a prior window change with an archive filter

Name your job descriptively, run it, and add results to your slide with a brief note on what you changed and what you observed.

---

## Comparing Across the Group

Once most people have completed at least Runs 1–3, we'll take a few minutes to look at the shared slide deck together. Pay attention to:

- How consistent is the global mean temperature across different runs?
- Which parameter changes produce the biggest differences?
- Where do archive-specific reconstructions agree, and where do they diverge?

These are exactly the kinds of questions you'll bring to your individual project on Day 3.
