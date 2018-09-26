---
layout: single
title: "What is the Different Between Lidar Measured vs Human Measured Tree Heights - Understand Remote Sensing Uncertainty"
excerpt: "In this lesson, we cover the topic of uncertainty. We focus on the types of uncertainty that you can expect when working with tree height data both derived from lidar remote sensing and human measurements. Further we cover sources of error including systematic vs. random error."
authors: ['Leah Wasser', 'Chris Holdgraf']
modified: 2018-09-25
category: [courses]
class-lesson: ['remote-sensing-uncertainty-python']
permalink: /courses/earth-analytics-python/lidar-remote-sensing-uncertainty/understand-uncertainty-lidar/
nav-title: 'Remote Sensing Uncertainty'
module-title: 'Lidar Compared to Human Measurements: Uncertainty and Remote Sensing Data'
module-description: 'In this module, we will discuss the concept of uncertainty as it relates to both remote sensing and other data. We will also explore some metadata to learn how to understand more about our data. '
module-nav-title: 'Uncertainty in scientific data & metadata '
module-type: 'class'
course: 'earth-analytics-python'
week: 5
sidebar:
  nav:
author_profile: false
comments: true
order: 1
---

{% include toc title="In This Lesson" icon="file-text" %}

<div class='notice--success' markdown="1">

## <i class="fa fa-graduation-cap" aria-hidden="true"></i> Learning Objectives

After completing this tutorial, you will be able to:

* List atleast 3 sources of uncertainty / error associated with remote
sensing data
* Interpret a scatter plot that compares remote sensing values with field
measured values to determine how "well" the two metrics compare
* Describe 1-3 ways to better understand sources of error associated
with a comparison between remote sensing values with field measured values

## <i class="fa fa-check-square-o fa-2" aria-hidden="true"></i> What You Need

You will need a computer with internet access to complete this lesson. You will also need the data you downloaded for last week of this class: `spatial-vector-lidar data subset`. 

{% include/data_subsets/course_earth_analytics/_data-spatial-lidar.md %}

</div>

## Understand Uncertainty and Error.

It is important to consider error and uncertainty when presenting scientific
results. Most measurements that we make - be they from instruments or humans -
have uncertainty associated with them. We will discuss what
that means, below.

## Uncertainty

**Uncertainty:** Uncertainty quantifies the range of values within which the
value of the measure falls within - within a specified level of confidence. The
uncertainty quantitatively indicates the "quality" of your measurement. It
answers the question: "how well does the result represent the value of the
quantity being measured?"

### Tree Height Measurement Example

So for example let's pretend that we measured the height of a tree 10 times. Each
time our tree height measurement may be slightly different? Why? Because maybe
each time we visually determined the top of the tree to be in a slightly different
place. Or maybe there was wind that day during measurements that
caused the tree to shift as we measured it yielding a slightly different height
each time. or... what other reasons can you think of that might impact tree height
measurements?

<figure>
   <a href="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/measuring-tree-height.jpg">
   <img src="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/measuring-tree-height.jpg" alt="national geographic scaling trees graphic"></a>
   <figcaption>When we measure tree height by hand, many different variables may impact the accuracy and precision of our results. Source:  http://www.haddenham.net/newsroom/guess-tree-height.html
   </figcaption>
</figure>

## What is the True Value?

So you may be wondering, what is the true height of our tree?
In the case of a tree in a forest, it's very difficult to determine the
true height. So we accept that there will be some variation in our measurements
and we measure the tree over and over again until we understand the range of
heights that we are likely to get when we measure the tree.



{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_2_0.png">

</figure>




In the example above, the mean tree height value is towards the center of
the distribution of measured heights. You might expect that the sample mean of
our observations provides a reasonable estimate of the true value. The
variation among our measured values may also provide some information about the
precision (or lack thereof) of the measurement process.

<a href="http://www.physics.csbsju.edu/stats/box2.html" target="_blank">Read more about the what a box plots tells you about data.</a>


{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_4_0.png">

</figure>




## Measurement Accuracy

Measurement **accuracy** is a concept that relates to whether there is bias in
measurements, i.e. whether the expected value of our observations is close to
the true value. For low accuracy measurements, we may collect many observations,
and the mean of those observations may not provide a good measure of the truth
(e.g., the height of the tree). For high accuracy measurements, the mean of
many observations would provide a good measure of the true value. This is
different from **precision**, which typically refers to the variation among
observations. Accuracy and precision are not always tightly coupled. It is
possible to have measurements that are very precise but inaccurate, very
imprecise but accurate, etc.

## Systematic vs random error

**Systematic Error:** a systematic error is one that tends to shift all measurements
in a systematic way. This means that the mean value of a set of measurements is
consistently displaced or varied in a predictable way, leading to inaccurate observations.
Causes of systematic errors may be known or unknown but should always be corrected
for when present. For instance, no instrument can ever be calibrated perfectly,
so when a group of measurements systematically differ from the value of a standard
reference specimen, an adjustment in the values should be made. Systematic error
can be corrected for only when the "true value" (such as the value assigned to a
calibration or reference specimen) is known.

*Example:* Remote sensing instruments need to be calibrated. For example a laser in
a lidar system may be tested in a lab to ensure that the distribution of output light
energy is consistent every time the laser "fires".

**Random Error:** is a component of the total error which, in the course of a number
of measurements, varies in an unpredictable way. It is not possible to correct for
random error.  Random errors can occur for a variety of reasons such as:

* Lack of equipment sensitivity. An instrument may not be able to respond to or
indicate a change in some quantity that is too small or the observer may not be
able to discern the change.
* Noise in the measurement. Noise is extraneous disturbances that are unpredictable
or random and cannot be completely accounted for.
* Imprecise definition. It is difficult to exactly define the dimensions of a object.
For example, it is difficult to determine the ends of a crack with measuring its
length.  Two people may likely pick two different starting and ending points.

*Example:* Random error may be introduced when we measure tree heights as discussed above.

- <a href="https://www.nde-ed.org/GeneralResources/ErrorAnalysis/UncertaintyTerms.htm">Source: nde-ed.org</a>


<figure>
   <a href="{{ site.url }}/images/courses/earth-analytics/remote-sensing/accuracy_precision.png">
   <img src="{{ site.url }}/images/courses/earth-analytics/remote-sensing/accuracy_precision.png" alt="national geographic scaling trees graphic"></a>
   <figcaption>Accuracy vs precision. Accuracy quantifies how close a measured value is to the true value. Precision quantifies how close two or more measurements agree with each other (how quantitatively repeatable are the results) Source: http://www.ece.rochester.edu/courses/ECE111/error_uncertainty.pdf
   </figcaption>
</figure>

## Use Lidar to Estimate Tree Height

Lidar data can be used estimate tree height because it is an efficient way to measure
large areas of trees (forests) quantitatively. However, you can process the lidar
data in many different ways to estimate height. Which method most closely represents
the actual heights of the trees on the ground?

<figure>
   <a href="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/scaling-trees-nat-geo.jpg">
   <img src="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/scaling-trees-nat-geo.jpg" alt="national geographic scaling trees graphic"></a>
   <figcaption>It can be difficult to measure the true height of trees! Often times "seeing" the very top of the tree where it is tallest is not possible from the ground - especially in dense, tall forests. One can imagine the amount of uncertainty that is thus introduced when we try to estimate the true height of trees! Image Source:
   National Geographic
   </figcaption>
</figure>

<figure>
   <a href="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/waveform.png" target="_blank">
   <img src="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/waveform.png" alt="Example of a lidar waveform"></a>
   <figcaption>An example LiDAR waveform. Source: NEON, Boulder, CO.
   </figcaption>
</figure>


<figure>
   <a href="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/treeline-scanned-lidar-points.png">
   <img src="{{ site.url }}/images/courses/earth-analytics/lidar-raster-data-r/treeline-scanned-lidar-points.png" alt="example of a tree profile after a lidar scan."></a>
   <figcaption>Cross section showing LiDAR point cloud data (above) and the
   corresponding landscape profile (below). Graphic: Leah A. Wasser
   </figcaption>
</figure>


{:.output}
    <class 'pandas.core.frame.DataFrame'>



## Study Site Location

To answer the question above, let's look at some data from a study site location
in California - the San Joaquin Experimental range field site. You can see the field
site location on the map below.


{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_8_0.png">

</figure>




## Study Area Plots

At this study site, we have both lidar data - specifically a canopy height model
that was processed by NEON (National Ecological Observatory Network). We also
have some "ground truth" data. That is we have measured tree height values collected
at a set of field site plots by technicians at NEON. We will call these measured
values *in situ* measurements.

A map of our study plots is below overlaid on top of the canopy height mode.


{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_10_0.png">

</figure>




### Compare Lidar Derived Height to In Situ Measurements

We can compare maximum tree height values at each plot to the maximum pixel value
in our `CHM` for each plot. To do this, we define the geographic boundary of our plot
using a polygon - in the case below we use a circle as the boundary. We then extract
the raster cell values for each circle and calculate the max value for all of the
pixels that fall within the plot area.

Then, we calculate the max height of our measured plot tree height data.

Finally we compare the two using a scatter plot to see how closely the data relate.
Do they follow a 1:1 line? Do the data diverge from a 1:1 relationship?

<figure>
    <img src="{{ site.url }}/images/courses/earth-analytics/spatial-data/buffer-circular.png" alt="buffer circular">
    <figcaption>The extract function in R allows you to specify a circular buffer
    radius around an x,y point location. Values for all pixels in the specified
    raster that fall within the circular buffer are extracted. In this case, we
    will tell R to extract the maximum value of all pixels using the fun=max
    command. Source: Colin Williams, NEON
    </figcaption>
</figure>


{:.output}
{:.execute_result}



    (0, 30)





{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_12_1.png">

</figure>






### How different are the data?





{:.output}
{:.display_data}

<figure>

<img src = "{{ site.url }}//images/courses/earth-analytics-python/05-raster-vector-extract-data/in-class/2016-12-06-uncertainty01-understand-uncertainty_14_0.png">

</figure>




## View interactive scatterplot

<a href="https://plot.ly/~leahawasser/170/" target="_blank">View scatterplot plotly</a>



## View interactive difference barplot

<a href="https://plot.ly/~leahawasser/158/chm-minus-insitu-differences/" target="_blank">View scatterplot differences</a>


