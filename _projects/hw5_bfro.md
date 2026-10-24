---
layout: page
name: "HW5: Bigfoot Report Patterns"
tools: [Python, Altair, Vega-Lite]
description: "Exploring geographic and seasonal patterns in Bigfoot reports."
permalink: /hw5/
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

<script src="{{ '/assets/js/vega.min.js' | relative_url }}"></script>
<script src="{{ '/assets/js/vega-lite.min.js' | relative_url }}"></script>
<script src="{{ '/assets/js/vega-embed.min.js' | relative_url }}"></script>
<script src="{{ '/assets/js/justcharts.js' | relative_url }}"></script>

# Patterns in Bigfoot Sighting Reports

The project used the BFRO report dataset provided for IS445.
The visualizations have described records in the dataset.
However, the report counts do not verify the reports or measure population-adjusted sighting rates.

## Visualization 1: Reports by State

<vegachart schema-url="{{ '/assets/json/hw5_plot1.json' | relative_url }}" style="display:block;width:100%"></vegachart>

This horizontal bar chart compares 15 states with the largest numbers of reports.
State is represented as a nominal variable on the vertical axis, and the report count is represented as a quantitative variable through horizontal bar length.
Descending sorting makes the ranking easy to read.
Single color is used because bar length already communicates magnitude, so an additional color scale is unnecessary.
Also, in Python, I selected the relevant columns, removed records with missing state, counted records by state, and kept the 15 largest counts.

## Visualization 2: Season and Classification

<vegachart schema-url="{{ '/assets/json/hw5_plot2.json' | relative_url }}" style="display:block;width:100%"></vegachart>

The heatmap showed how report counts vary across different seasons and report classifications.
Season and classification are nominal variables, displayed on the horizontal and vertical axes.
Seasons are in the calendar order, with Unknown in the last.
Quantitative report counts are represented using a sequential Blues color scheme that darker cells indicate larger counts.
In Python, missing season or classification were remained as Unknown, records were grouped by state, season, and classification, and combinations with no records were assigned zero counts.
Vega-Lite will sums these counts after applying the selected state filter.

### Interactivity

User can use the State dropdown to switch between all states and an individual state.
This filtering helps readers examine local seasonal and classification patterns that may be obscured in the national totals.
Also, hover over a cell can see its exact count. 
The color scale updates with the selected state, so exact counts should be used when comparing different states.

## Data and Analysis

[The Data](https://github.com/UIUC-iSchool-DataViz/is445_data/blob/main/bfro_reports_fall2022.csv)

[The Analysis](https://github.com/HeyGordon/HeyGordon.github.io/blob/main/python_notebooks/Workbook.ipynb)
