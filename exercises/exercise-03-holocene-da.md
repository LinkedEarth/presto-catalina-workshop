# Exercise 3: Holocene Data Assimilation

---

## Overview

In this exercise you will run your first paleoclimate reconstructions using PReSto's Holocene data assimilation (DA) engine. We'll be going through the whole process, with one major exception. In this exercise, do not worry about de-duplication, we'll help you select input data without handling that extra complexity (for now). Instead we'll be focusing on how DA parameter choices and input data shape the result.

Each reconstruction job takes roughly **15 minutes** from submission to results, so plan your runs accordingly and use the wait time to read ahead. Feel free to work with a neighbor to run and compare more reconstructions than you could alone.

By the end of this exercise you should be able to:
- Submit a reconstruction job through the PReSto interface
- Read and interpret the output visualizations
- Develop intuition for how DA parameters and input data affect the final reconstruction

As before, we'll be uploading screenshots and interpretations to a shared workshop slide deck. The deck to use for this exercise is below. As before, create slides as needed.

**Shared slide deck:** [Exercise 3 Slides](https://docs.google.com/presentation/d/1cSmRyMkZ2pu4fIRe6kTPQuWe23G_Sx-U_eRG32qnWp0/edit?slide=id.p#slide=id.p)  
Add your figures to your named slide after each run.

---

## Setup: Launch a new custom reconstruction using GitHub

PReSto runs your reconstruction as a GitHub Actions workflow in a repository created in your own GitHub account. Before your first run, you need to authorize this:

1. Go to [paleopresto.org/custom.html](https://paleopresto.org/custom.html) and select "Holocene DA" sign in with your GitHub account.
2. Follow the prompts to grant PReSto permission to create repositories and run Actions on your behalf.

---

## Part 1: Exploring Data Assimilation parameters


### Starting Dataset

For this part of this excercise, we're going to use the same input data: the **Temp12k v1.0.2** dataset which was used in the Holocene DA product Erb et al. (2022). This is pre-loaded — you do not need to run a query.

Select **"Use Archived Compilation"** and choose **Temp12k v1.0.2** from the dropdown. This should be the default choice.

---

## Run 1: Default Settings (~15 min turnaround)

Start with everything at its defaults so you have a baseline to compare against.

### Steps

1. Select the **Holocene DA** method.
2. Select the **Temp12k v1.0.2** dataset.
3. Leave all parameters at their default values.
4. Give your job a descriptive name (e.g., `holocene-default`).
5. Submit the job.
6. This should take you to a GitHub actions page that is processing the code. Take a look through what's happening to get a sense of how GitHub Actions is working. You don't need to wait for this to finish to start a second run, so go ahead and start another reconstruction. 

---

## Run 2: Changing the Prior

The **prior window** determines which years of model simulation are used to inform the climate covariance structure that DA will leverage to give us spatially complete reconstructions. Unsurprisingly, there are a lot of choices that go into this. For example:

- What model(s) should we use for the prior?
- Should the prior vary through time? Or should we assume the climate covariance structure throughout the reconstruction?
- If it varies through time, we need a sliding window to calculate covariance. How long should that window be? Over what intervals should it slide?
- Should the mean of the prior be allowed to vary?

Make a change to the settings for the prior and compare it to your first, "vanilla" reconstruction. This could be as simple as changing which models are included, or you could play with the impact of allowing the prior mean to vary. Or, you could try to explore the impact of a time varying prior on covariance structures associated with the Laurentide Ice Sheet, as we saw in exercise 1. When the prior window includes years when the Laurentide Ice Sheet was still present, its strong covariance signature can "bleed" into reconstructed time periods after the ice sheet retreated. This produces a ghost ice sheet pattern in the early Holocene.

### Steps

1. Start a new reconstruction job.
2. Same dataset: **Temp12k v1.0.2**.
3. Modify the **DA parameters** of your choosing. You may need to toggle on advanced settings.
4. Name the job something specific.
5. Submit.
6. Consider conspiring with a classmate if you're interested in exploring more than one reconstruction.

### When results are ready

Compare the two reconstructions you've generated. Both the diagnostics and visualizer websites will be useful for this. Once you have a feel for the interesting similarities and differences:

7. Create screenshots of both the **spatial maps at interesting time periods** and **time series at the same location in each reconstruction**.
8. Upload to your slide(s) labeled "Modified DA settings."

> **Discussion prompt:** One of your slides (or a new one), summarize the major differences between the reconstructions. Do the parameters you selected seem sensitive to this choice? If there are differences, what's causing them? Do the results make sense given what you know about DA?

### If you have extra time or curiosity, explore your neighbors modified-parameter reconstruction as well. 

What else can you learn?


---

## Part 2: Exploring the impact of the data network

Now we will hold our reconstruction parameters constant, and instead change the data coming in. We already have our "control" run, a lower-resolution version of Erb et al., 2022. Now we'll explore how using different data affect that result.

## Querying the LiPDverse to approximate the Erb 2022 dataset

Because we're trying to avoid data deduplication in this exercise we can't exactly reproduce the Erb et al., 2022 input data, but we can get close. Plus this will help us build up your PReSto data querying skills that you developed in Exercise 2. For each of the exercises in Part 2, you will start by querying using the following steps, before further filtering the dataset. 

To get to your starting dataset:

1. Start a new custom Holocene DA reconstruction, and then select "Query across LiPDverse"
2. Select the "Temp12k v1.2.0" compilation
3. Select the "temperature" interpretation variable
4. Select "Annual" seasonality
5. Select "temperature" for the variable name

Once you've done this, update the map. You should have 646 timerseries from 631 locations. This will be your starting point for each of the following reconstructions. 

## Run 3: Single (or few) Archive Type (~15 min turnaround)

The Erb et al reconstruction blends many archive types — tree rings, ice cores, lake sediments, marine sediments, speleothems — each with different seasonal sensitivities, geographic distributions, and uncertainties. How would choosing only one, or perhaps excluding one of the major ones (i.e., marine or lake sediments) affect the final reconstruction?

### Steps

6. Continue filtering the dataset you used above, selecting a subset of the archives that were originally used. 
7. Name the job to reflect your choice (e.g., `holocene-marine-only`) and **submit**

### When the run finishes...
8. Create screenshots of both the **spatial maps at interesting time periods** and **time series at the same location in each reconstruction**.
9. Upload to your slide(s) labeled "Reduced Archived reconstruction."

> **Discussion prompt:** Where does the reconstruction degrade most when you remove most of the proxy network? What does that tell you about where we have (and don't have) good data coverage for the Holocene? Do you think the archive characteristics, or geographic coverage, have a bigger impact on the result? What kinds and locations of new records be the most valuable? 

---
### Run 4: Restricted geography

Now we're going to start a new run and get to our starting dataset by repeating steps 1-5 above. 

This time, we're not going to filter by archive, but instead we're going to filter spatially. 

6. Pick a location your interested in the "Location Filters" tab, either a coordinate box, or continent or countries that you're interested.
7. Name the job to reflect your choice (e.g., `holocene-south-america`) and **submit**


8. Create screenshots of both the **spatial maps at interesting time periods** and **time series at the same location in each reconstruction**.
9. Upload to your slide(s) labeled "Restricted geographic coverage reconstruction."

> **Discussion prompt:** Did restricting the geography work the way you expected? Why or why not? How does this impact the archive type experiment you did above? Where would new records be the most valuable? 

---

## Run 5: Your Choice (if time permits)

Play with the reconstruction! Pick a parameter or filter combination that you're curious about. Some ideas:

- Try a different single archive type and compare to your Run 3 result
- Change the **localization radius** (controls how far the influence of each proxy extends spatially)
- Combine a prior window change with an archive filter
- Team up with another student and compare your results

Name your job descriptively, run it, and add results to your slide with a brief note on what you changed and what you observed.

---

## Comparing Across the Group

Once most people have completed parts 1 and 2 we'll take a few minutes to look at the shared slide deck together. Pay attention to:

- How consistent is the global mean temperature across different runs?
- Which parameter changes produce the biggest differences?
- Where do archive-specific reconstructions agree, and where do they diverge?

These experiments are excellent seeds for your individual project on Day 3.
