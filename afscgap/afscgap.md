### <font color='grey' style='font-family:Georgia'>_Data Love Letter_</font>

# <font color='green' style='font-family:Georgia'>NOAA AFSC GAP</font>

> To: _DSE_ <br> From: _A Sam Pottinger_ <br> _March 2023_

## <font color='grey' style='font-family:Georgia'>Preliminary</font>

### 1. Why did you choose this dataset among many others?
- *Is it known by the community?* Yes! This dataset is used extensively for fisheries management in Alaska.
- *Is it used by the community?* Yep! This is leveraged frequently in papers doing biodiversity or food security research in the area.
Here’s an example: https://onlinelibrary.wiley.com/doi/full/10.1111/fog.12422 
- *What is it about and why is it relevant?* This provides catch (presence) data in the region and is one of the leading 
region specific longitudinal datasets of biodiversity in the area. It touches on both food security and biodiversity interest areas for the center.

### 2. Where did you find this data?
- *Is it publicly available?* Yes
- *How did you access it?* It is available at https://www.fisheries.noaa.gov/contact/groundfish-assessment-program
- *In what format(s) is it available?* It is available as an API or CSV download as generated from a UI.

### 3. Who is behind the data?
- *Do we know who maintains it?* It appears that different folks at NOAA Fisheries have maintained these data over the years, but it changes.
- *Do we know who contributes to it (people and actual sources)?* Yes the current maintainers are available at https://www.fisheries.noaa.gov/inport/item/22008.

### 4. Is the dataset static or living?
- *When was it last released?* Unclear but 2022.
- *How often is it updated?* Yearly
- *Are changes documented? If yes, how?* Yes on In-Port but the metadata do appear to trail (https://www.fisheries.noaa.gov/inport/item/22008).
- *What version are you using?* It is not explicitly versioned but, from git activity, appears to be continually released.

## <font color='grey' style='font-family:Georgia'>First impressions</font>

### 5. What does the data look like?
- *Could you find documentation for it? In what format(s)?* There is approximate documentation at https://github.com/afsc-gap-products/metadata 
- *What is the size of the data (byte size / records / columns)?* Many gigabytes to terabytes with negative records included. A full download is no longer available.
- *What tools do you plan to use (or did you/others use) to work with it?* Plain Python... 
I do use Pandas but only after aggregation of the data due to its size and only as a library demonstration. 
The raw data in its entirety with negative inference do not fit in memory.
- *What kind of data types are prevalent/relevant? What does a record look like?* See https://github.com/SchmidtDSE/afscgap#data-structure 

### 6. What is the data coverage and resolution?
- *What axes does this data cover (spatial / temporal / taxonomic / etc)?* Multiple regions of Alaska with some surveys 
dating back into before 2000 (my analysis and questions only looked 2000 and onwards).
- *To what extent are they covered (e.g., year range, geographic range)?* Different regions have different coverage but yearly and biyearly are common.
- *What is the resolution along these axes?* Not explicitly given but the API reports highly precise latitudes and longitudes. It is sub 5 letter geohash.

### 7. Does this data need cleaning?
- *Is there missing and/or incomplete data? If so, to what extent? Does this hinder the relevance and/or usability of the dataset?* 
Yes the data on their own are presence only which limits their utilization. There are also “bad” records as discussed at https://github.com/SchmidtDSE/afscgap#data-quality-and-completeness 
- *Is a cleaning step needed before starting to use this data?* Yes, if you are not using my newly created Python library: https://github.com/SchmidtDSE/afscgap 

## <font color='grey' style='font-family:Georgia'>Measure and visualize</font>

### 8. What are some questions that this data can help answer?
- *What are you having fun with right now?* What question(s) are you exploring and/or attempting to visualize? Pacific cod example: https://github.com/SchmidtDSE/afscgap/blob/main/notebooks/cod.ipynb 
- *What preprocessing steps are necessary to look into this question (e.g., normalizations, re-formatting, projection scale adjustments)?* 
I ultimately built a library: https://github.com/SchmidtDSE/afscgap 
- *What story does the data tell? What does it suggest with respect to the question(s)?* See https://github.com/SchmidtDSE/afscgap/blob/main/notebooks/cod.ipynb 
- *What are the current limitations to gathering more insights (e.g., in terms of tools / data coverage / granularity / visualization options)?* 
There are limitations as explored at https://github.com/SchmidtDSE/afscgap/blob/main/notebooks/cod.ipynb in discussion section, but I was still able to corroborate prior literature results.

### 9. What are the gaps and biases in the data?
- *Are there gaps and biases in this data that are acknowledged by the maintainers and the community?* 
The exact haul paths do vary from year to year as documented in the hauls table (available from Python library, newly 
created community site at https://pyafscgap.org, or from the official webpage https://www.fisheries.noaa.gov/inport/item/22008). 
These variations do not extend outside a 4 letter geohash as best as I can tell from year to year except old surveys which 
had different geographic coverage. There are biases in the “stations” examined in the survey... it’s best to think of these 
data as “catch relevant” prevalence and not absolute abundance for species. It’s important to note that this is ultimately 
a dataset for a fisheries management agency and some of its design may reflect that.
- *Could we quantify (measure, visualize) these biases in some way?* Yes by bounding box intersection over union from year 
to year or area coverage within a geohash for example.
- *How do these considerations affect the answers that this dataset provides (e.g., to the exploration question above)?* 
There has to be some aggregation by “catch per unit effort” which is a common approach in the space and documented in the metadata repo linked above. 
This does mean though that absolute presence estimations are likely to be less accurate than those CPUEs. 
There are also some considerations involved in ground trawl surveys that have to do with the physical collection.
- *Do these considerations affect the way we should use this dataset?* Yes and no... 
This is one of the more longitudinally consistent datasets available in the region. That said, CPUEs are not absolute quantification 
estimates and the surveys cover specific geographic regions. It’s best to think of this as catch relevant prevalence predicated and not overall prevalence.

### 10. Did you have an example question ot task you used to explore the data? 
A lot of this work was influenced by my cod example which is specifically examining geohash based CPUE prevalence: 
https://github.com/SchmidtDSE/afscgap/blob/main/notebooks/cod.ipynb. I’d be uncomfortable answering for other uses or functions like https://onlinelibrary.wiley.com/doi/full/10.1111/fog.12422. 

## <font color='grey' style='font-family:Georgia'>Reflection and future opportunities</font>

### 11. What lessons could be learned from exploring this data?
- *What should we keep in mind when utilizing this dataset in the future?* I strongly recommend using my new library. 
Unless you work for NOAA, it’s otherwise not possible to get absence data without considerable effort: https://github.com/SchmidtDSE/afscgap#absence-vs-presence-data 
- *What were the major issues / bottlenecks / limitations in using this data?* The presence only nature slowed things down 
while I built out zero catch inference. The API service also uses ORDS which is not well documented, especially in the Python community.
- *Are there best-practices that we should adopt internally and share with the rest of the community?* 
Yes! I have determined how to work with ORDS via Python and have formalized an algorithm for zero catch inference. See https://pyafscgap.org. 

### 12. What future directions does this data open?
- *What are other questions/explorations this dataset could be useful for?* I looked at cod presence but there’s federal 
fisheries management policy set every year as administrative law by NOAA using these data. 
This information is also cited in biodiversity papers and may be able to help direct fishing activity geographically.
- *Are there other datasets that could be combined to this one, e.g., to correct biases, enhance coverage, add more layers to the analysis?* 
This dataset also provides temperature data and, combined with modeling on temperature changes, may provide assistance in modeling future expected prevalence.

### 13. What future opportunities does this data bring?
- *Is there space to work further on/with this dataset?* Yes! I am submitting to PyOpenSci, contacting NOAA, and releasing a visualization tool which supplants a prior one that is semi-retired from the agency.
- *What would be nice-to-have tools that we could contribute to for this data, or that use this data?* Comparative visualization tool. 
It takes a lot of work to generate these geographic plots even in Python and requires using native libs.
- *Would it be useful to circle back to the people maintaining/contributing to this data with some of our finds and/or proposals for collaborations?* Yes!
