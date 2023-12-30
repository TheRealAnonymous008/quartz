# Telling a Story
* Data visualization helps make an argument more persuasive by being easier to digest. *Data visualization is a means to tell a story about the world.* 
	* The story may or may not be true. *Data visualization can be used to lie*.
* Sketch a **data story** with this four-part process: 
	* Define the problem to be solved ("We need to X because Y")
	* Frame the problem as a question. 
		* Use this question to facilitate the search for data.
		* Be open to changing this question when evidence points to a more meaningful direction.
		* Always state the question before the answer. 
		* Make sure the question is aligned with the problem being solved.
	* Define the means to answer the question.
	* Plan a data visualization to tell the story.
* Choose an appropriate data visualization tool. (see [here](https://handsondataviz.org/tool-factors.html))
* *Data and numbers are not necessarily neutral. When working with data, ask whose story is being told*. [[Doublespeak|Data can be used to lie or obfuscate]].
* **Tell, Show, Why**
	* Tell the interesting aspects of the data. Tell it in the most succinct way possible.
	* Show visual evidence to support this argument
	* Remind the reader why it matters. 
* *Do not leave it up to the audience to guess what the data means*. Data visualizations do not speak for themselves.
# Data Preprocessing
* Consider what kind of data are out there, where and how they can be obtained, and whether the data raise privacy issues or should not be published.
* *Source your data* by having a descriptive file name, detailed notes, and a backup of the data. Also explain any blank or null values.
* *Clean your data*. Look out for missing or incorrect values within the data. 
	* If the data are too messy, it is at the analyst's discretion whether or not to continue using these data.
	* Most of the work in data analysis is often just making sure the data is clean.
	* *Automate this process*: 
		* Use Find and Replace liberally
		* Use Histograms to find outliers or weird entries.
		* Transpose the data for data visualization purposes.
		* Split data into more columns by splitting on some delimiter (i.e., spaces or commas).
		* Use Formulas (as in spreadsheets) liberally to get derived values
		* Automate data extraction through OCR or Tabula
* *Question your data*. Understand how to interpret the data and any inherent methodological or sociopolitical biases within the data. Know which aspects are unanswerable from the data alone.
* *Know the limitations of the data*. Specify these in the actual data story.
# Data Processing
* *Data are only useful if you use it in comparison to something else*.
	* *Be precise*. Use the correct terminologies. Be wary of data phrased in a misleading way.
	* *Causation != correlation*. Phrase with this in mind.
	* Prefer to **normalize** the data to make meaningful comparisons. *Prefer to normalize data when it is not formatted in a common scale or metric to allow for direct comparison*.
		* Adjust to rescale data appropriately. Compare rates not values.
		* Adjust to account for seasonality or change over time.
		* Use a standard score or index for the data.
	* Account for biases in the data when making a comparison.
> "It's unrealistic to pretend that we can create a perfect model. But we can certainly come up with a good enough one"  [^1]
# Techniques
### Charts
* [What chart type should you use?](https://handsondataviz.org/chart.html)
* *Before creating a chart ask: Does a visualized data pattern really matter to the story?* 
	* Judge a chart based on its goals. (for more on this, see [here](https://lisacharlottemuth.com/datavisrules#part3))
#### Rules of Thumb
* The title should tell a story of its own. This may be combined with a more technical subtitle.
* Use legends and annotations to provide more context.
* Specify Data Sources and Credits to give context on where the data came from.
* Specify uncertainties within the data.
* Make sure all essential information is visible without any user interaction.
* Bar, Column and Area charts always start at the zero baseline. *The baseline of the chart should be obvious as this is one way to lie with the data*.
* *Pie charts represent 100% of the quantity*.
* *Line charts are judged based on the shape of the line*. Use appropriate scales.
* Use only one vertical axis. Any more than this will confuse the reader.
#### Aesthetic Guidelines
* *Add elements as they are needed to convey the story*. Do not add bloat to the chart.
	* Avoid decorative elements as these can mislead the viewer.
* Sort the slices in a pie chart from largest to smallest starting at 12 o clock.
	* Favor rendering the data as a bar chart instead if there are many slices.
* Do not make people turn their heads to read labels. Orient the labels horizontally.
* Order the categories appropriately.
* Choose natural increments that space equally. Keep typography simple
* Choose an appropriate color palette. Consider as well the inherent symbology of some colors (i.e., red means loss, green means profit) 
### Maps
* *The main consideration here is the data format and the data story being told*.
	* Before using a map, ask if your data can be mapped as points or polygons. *These data should have a spatial component*
	* Maps should correspond to only one variable. Any more and the map becomes overloaded.
	* Choropleths should use smaller geographies to better visualize the polygons.
	* Use the appropriate scale for the data story. (beware the [Modifiable Areal Unit Problem](https://en.wikipedia.org/wiki/Modifiable_areal_unit_problem))
	* *Normalize all the values*. 
* [What Map Type should you use?](https://handsondataviz.org/map.html)
* Choose the appropriate color palettes to help readers correctly interpret the information. 
	* Use linear interpolation to emphasize outliers.
	* Use quantiles and non-linear groupings to reveal diversity in the middle ranges.
	* Use a continuous color palette to show nuances in the data unless the data story has a compelling reason to display discrete steps.
* Use **cartograms** to remove biases due to map area or map projection at the cost of the map becoming more abstract.
### Tables
* Tables make sense when readers want to look up a specific row of data that is highly relevant to them.
* Use tables when there are no visual patterns or spatial data. 
#### Rules of Thumb
* Make column headers stand out above data.
* Use light shading to separate rows or columns.
* Left align text and right align numbers for easier reading.
* Avoid repetition by placing labels only on the first row.
* Group and sort data to highlight meaningful patterns.
* Use color to highlight key items or outliers.
* Place independent variables at the column headers, and dependent variables on the side of each row
* Percentages go vertically downward not horizontally.
# Data Visualization as Interpretative
* Visualizations are **wrong** if they misstate the evidence or violate design rules for good visualization.
* Visualizations are **misleading** if they follow good design rules, but unreasonably hide or twist the appearance of relevant data.
* Visualizations are **truthful** if they both follow the design rules, and also show accurate data.
### Lying with Charts
* Exaggerate change by truncating the baseline and zooming in.
* Diminish change by lengthening the vertical axis or warping its aspect ratio.
* Add more data and a dual vertical axis to mislead the reader.
### Lying with Maps
* Changing the color ranges and scales can create the wrong impression about the data.
### Lying with the Data Itself
* Be aware of the biases present within the data such as the following:
	* Sampling biases 
	* Cognitive biases 
	* Algorithmic biases
	* Intergroup biases
	* **Map Area bias**  - the tendency to focus on large regions than smaller ones.
	* **Projection bias** - biases due to how a map is projected.
	* **Disputed Territory bias** - the tendency for map providers to display different view of the world.
	* **Map exclusion bias** - the tendency to fail to represent people or land by omitting them or aggregating them as part of another territory.

# Tools
* [OpenRefine](https://openrefine.org/download.html) - automate cleanup of messy tabular data.
* [Tabula](https://tabula.technology) - extract tables from text-based PDFs.
* [DataWrapper](https://www.datawrapper.de) - offers sophisticated charts.
* [Tableau Public](https://public.tableau.com/app/discover) -data visualization tool that also allows one to make dashboards.
* [Geojson.io](https://geojson.io/#map=2/0/20) - for creating GeoJSON files for geospatial data.
# Links  
* [Hands on Data Visualization](https://handsondataviz.org/index.html)
	* [Ten Factors When Considering Tools](https://handsondataviz.org/tool-factors.html)
	* [What chart type should you use?](https://handsondataviz.org/chart.html)
	* [What Map Type should you use?](https://handsondataviz.org/map.html)
* [What to consider when considering data vis rules](https://lisacharlottemuth.com/datavisrules#part3)
* [Your Friendly Guide to Colors in Data Visualisation](https://blog.datawrapper.de/colorguide/)
* [[How To Lie With Statistics by Huff]]

[^1]: Alberto Cairo, The Truthful Art: Data, Charts, and Maps for Communication_(Pearson Education, 2016),