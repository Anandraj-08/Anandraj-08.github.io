---
name: Building Inventory Dataset
tools: [Python, HTML, vega-lite, altair]
image: assets/pngs/scatter.png
description: This notebook displays two different visualizations for the Building Inventory dataset.
custom_js:
 - vega.min
 - vega-lite.min
 - vega-embed.min
 - justcharts
permalink: /projects/hw5
---

## The Data  
[Dataset](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv)  

## The Analysis  
[Notebook](https://github.com/Anandraj-08/is445-building-viz/blob/main/building_visualizations.ipynb) 

##  Visualization 1: Building Age vs. Size Distribution (Scatter Plot)
<iframe src="/assets/plots/Chart_1.html" width="100%" height="700" style="border:none;"></iframe>

**What is being visualized:**  
This interactive scatter plot shows the relationship between when a building was constructed and its total square footage. Each point represents a building in the dataset. This allows us to analyze whether new buildings tend to be larger, and how different agencies compare in terms of building size and construction periods.

**Design choices – encodings:**  
- The **x-axis** encodes the `Year Constructed` (quantitative), and the **y-axis** encodes `Square Footage` (quantitative).
- The **color** is mapped to `Agency Name` using the `category20` scheme, which helps differentiate agencies and spot clustering.
- The points have a semi-transparent fill with a **white border** to ensure good visibility even when data points overlap.
- The plot includes **tooltips** for `Building Name`, `Year`, `Square Footage`, `Agency`, and `Decade Built` on hover.

**Design choices – colormaps:**  
The `category20` color scheme was selected to clearly distinguish between up to 20 agencies. categorical palette makes it easy to scan the visualization.

**Data transformations:**  
- The Non-numeric entries in `Year Constructed` and `Square Footage` were coerced 
- The outliers were removed for both `Square Footage` and `Year Constructed`.
- Missing values were dropped, and a new column `Decade Built` was added by flooring the year to the nearest decade.

**Overlap with Homework #5:**  
This plot is inspired by the original scatter plot from Homework #5 but has been **rebuilt using Altair**, Intially it was in streamlit Compared to HW5, this version adds interactive tooltips, color encodings, axis formatting, and outlier filtering to improve clarity and usability.

---

##  Visualization 2: Building Construction by Decade (Area Chart)
<iframe src="/assets/plots/Chart_2.html" width="100%" height="700" style="border:none;"></iframe>

**What is being visualized:**  
This area chart shows how many buildings were constructed in each decade between 1900 and 2020. It helps visualize construction trends over time, highlighting periods of growth and stagnation.

**Design choices – encodings:**  
- The **x-axis** is `Decade Built` (ordinal), and the **y-axis** is the number of buildings (quantitative).
- The chart uses a  (`monotone`) to make the trend visually appealing and easier to interpret.
- The area is filled with a **vertical blue gradient** (from light to dark) to emphasize the growth over time.
- Interactive **tooltips** provide precise decade and building count on hover.

**Design choices – colormaps:**  
The vertical gradient (light blue to dark blue) was chosen to indicate volume and flow over time, while maintaining a clean and professional aesthetic. A **white line border** was added to define the area boundary more clearly.

**Data transformations:**  
- A new `Decade Built` column was created from `Year Constructed`.
- The dataset was grouped by `Decade Built`, and missing decades were filled with 0 to maintain consistent spacing on the x-axis.
- The y-axis was scaled to fit slightly above the max value for visual clarity.

**Overlap with Homework #5:**  
This chart is **entirely new** and not present in Homework #5. While the dataset is the same, the chart type, transformations, and focus are completely different.

---

## Interactivity

This submission includes interactive features beyond zoom and pan:

- **Visualization 1 (scatter plot)** includes full zoom/pan via `.interactive()` as well as detailed hover tooltips.
- **Visualization 2 (area chart)** includes hover tooltips for each decade showing the exact count of buildings.These features make the plots easier to explore and provide additional insights without cluttering the visual design.

---

<div class="left">
{% include elements/button.html link="https://github.com/spatel54/spatel54.github.io/blob/725f63d7ebc40c615a8ff2f72891eef93d7db924/assets/json/bfro_reports_fall2022.json" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/Anandraj-08/is445-building-viz/blob/master/building_visualizations.ipynb" text="The Analysis" %}
</div>
