# Predicting Bat Coronavirus Positivity with Machine Learning

[Website](https://bat-cov-positivity.org/home/) / [Paper](https://docs.google.com/document/d/1FLlotUx1XfFxBzky489_72njXnUz16bHtqIj62QFxO0/edit?usp=sharing) / [Summary Slides](https://docs.google.com/presentation/d/13Ot_wj25HCAfJi9_KOllAUaPXitvok93bEULxCFregQ/edit?usp=sharing)

## Abstract

About 20% of the approximately 5,000 species of mammals are bats (order Chiroptera [meaning “hand wing”]). Among mammals, bats are unique in their ability to fly, and are found on all continents except Antarctica. The ability of bats to fly allows for efficient virus spread, and viral transmission from bats has been suspected in a number of major emerging infectious disease outbreaks. These include outbreaks of the SARS (Severe Acute Respiratory Syndrome) virus, MERS (Middle East Respiratory Syndrome) virus, Ebola virus, Nipah virus, and others. We planned to build machine learning model to predict how likely a bat species can serve as reservoir host of coronavirus.

## Background

- Bats comprise ~20% of mammal species (> 1,400 species)
- Serve as reservoir hosts of many deadly viruses (e.g. Ebola, Hendra, Nipah, SARS-type coronaviruses)
- Scientists do research on bats worldwide to study relationships between bats and viruses
- The SARS-CoV-2 virus that led to the COVID-19 pandemic most likely originated from an Asian bat species

## Our Challenges

Our original aim was to identify species of bat that were able to carry coronavirus, with focus on Bat characteristics & Coronavirus positivity (as a binary outcome).

However, initial data showed that it is likely that most, if not all, bat species can carry Coronavirus. Coronavirus positivity strongly associated with number of bats caught.

![total](img/Total.png)

## Problem Statement

Predict factors that make it more likely for a particular bat species to be a potential coronavirus reservoir host

- Geographical or Environmental Characteristics
- Morphological or Other Biological Traits
- Phylogenetic Grouping

## Our Data

- Bat CoV Positivity (Dataset manually collected from 100+ published papers. Look for coronavirus positivity rates among samples from bats)
- PanTHERIA (Dataset Global mammalian species-level dataset of life-history, ecological and geographical traits)
- EltonTraits1.0 (Global species-level foraging attributes of mammals)
- Bat Ecology / Viral Diversity (Bat specific dataset used in a study on viral diversity and reservoir status in a Canadian study)
- Zoonotic Infectious Diseases (Dataset used in a study on zoonotic emerging infectious diseases, including geographical / environmental features)

## Features

We divided the species into 2 groups, high CoV prevalence rate vs low CoV prevalence. Features are selected base on univariate logistic regression on high vs low classification.

![features](img/Density_Plot.png)

Our features can be roughly grouped into six categories.

![features2](img/MainFeatures.jpg)

## Feature Engineering

From correlation heat map, we can see features can be roughly grouped in to 2 main categories. Top left hand square corresponds to natural features, and bottom right hand square corresponds to man-made features.

![heatmap](img/Feature-correlation.png)

Correlation between weather variables e.g. temperature and precipitation is high. We perform DBSCAN clustering on 2D plot of temperature vs precipitation and use these clusters for subsequent modeling. This is to reduce inter-variable correlations.

![weather1](img/weather1.png)
![weather1](img/weather2.png)

## Modeling