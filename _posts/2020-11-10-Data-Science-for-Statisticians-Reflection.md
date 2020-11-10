---
layout: post
title: Data Science for Statisticians Reflection
---

As I'm coming into my last days as a student in a Data Science for Statisticians class, it's time to reflect on what I've learned and how my opinions have changed.  My assessment of a datascientist is still the same -- someone who's navigating the efficient use of data we aggregate in the 21st century.  

R as a tool for datascience has definitely taken a couple steps in the lead over python.  The biggest selling point to me is the caret package for modeling.  Being able to try several hundred different modeling algorithms by simply changing the method argument is incredibly convenient.  Python has various implementations of many of these models, but they have yet to be consolidated into the same wrapper.

My biggest complaint about R is the need to type out column references, compared to GUI interfaces like JMP.  With a GUI, you can drag and drop column names, and be confident that you have the correct column -- at most this takes 10 seconds, even if you're selecting vast swaths of columns.  With R, you need to worry about capitalization, space characters, whether or not the dataframe is being referenced correctly, and many other nuances that aren't inherently robust when you're stuck typing in references.  I am currently playing around with R Shiny to determine how well dashboarding might fix that, and am hopeful that a good solution can be found.

As much as possible, I'm going to start using the caret package for all of my modeling going forward.  The readily available cross-validation controls save on implementation overhead, and really manage expectations for how well models perform on prediction.