# Data exploration process - _Guiding template_ 

Questions to guide our datasets/tools exploration and output creation process. 

_Note: this guiding template is part of ongoing discussions in our team on how to best approach data and how we can refine our internal processes.
Our hope is to keep improving!_

------

**What is this?** The following questions are designed as a tool to be used in our data exploration adventures. 
While they were written with data exploration in mind, many steps should hopefully be applicable to the process of exploring
a tool/algorithm/model too. Sometimes we engage with a dataset because we just want to know more about it, and some other 
times we work with it to analyze a particular question: while these starting points are different and might influence the 
extent of our exploration and what we learn about the data, there should be something useful for both purposes.

**How do I use this tool?** In the way that best serves your process! 
For example, one could use it as a series of prompts to keep on the side when opening a dataset and feeling lost, 
another could use it to structure messy outputs in a Jupyter Notebook. You could also fill it out retroactively for 
knowledge-transfer and archival purposes, or even use it as a guide when writing a piece/presentation about your exploration. 

**Why a template?** The reason behind having a template is to provide general guidelines on what is important to us when 
approaching new data and tools. It’s also an opportunity to provide some level of consistency to our outputs. 
Guidelines are not mandates: we don’t expect this process to work flatly across all our explorations, and we aim for this 
to be a flexible tool. So take what works and leave what does not, and add your own thoughts! 

-----

## Preliminary

### 1. Why did you choose to explore this dataset among many others?
- Is it known by the community? 
- Is it used by the community? Did you see it used somewhere else (e.g., in a paper, a repository)?
- What is it about and why is it relevant? 

### 2. Where did you find this data?
- Is it publicly available? 
- How did you access it?
- In what format(s) is it available?

### 3. Who is behind the data?
- Do we know who maintains it?
- Do we know who contributes to it (people and actual sources)?
- Which labor was involved in this project? Which labor might be not recognized?

### 4. Is the dataset static or living?
- When was it last released?
- How often is it updated? 
- Are changes documented? If yes, how?
- What version are you using?

## First impressions

### 5. What does the data look like?
- Could you find documentation for it? In what format(s)?
- What is the size of the data (byte size/records/columns)?
- What tools do you plan to use (or did you/others use) to work with it?
- What kind of data types are prevalent/relevant? What does a record look like? (e.g., geospatial coordinates, 
text-based taxonomy, categorical and boolean features, numeric values)

### 6. What is the data coverage and resolution?
- What axes does this data cover (spatial/temporal/taxonomic/etc)? 
- To what extent are they covered (e.g., year range, geographic range)? 
- What is the resolution along these axes?

### 7. Does this data need cleaning?
- Is there missing and/or incomplete data? If so, to what extent? Does this hinder the relevance and/or usability of the dataset?
- Is a cleaning step needed before starting to use this data? 

## Measure and visualize

### 8. What are some questions that this data can help answer?
- Is there an example question/task that you are using to explore this data? 
- What preprocessing steps are necessary to look into this question (e.g., normalizations, re-formatting, projection scale adjustments)?
- What story does the data tell? What does it suggest with respect to the question(s)? 
- What are the current limitations to gathering more insights (e.g., in terms of tools / data coverage / granularity / visualization options)?

### 9. What are the gaps and biases in the data?
- Are there gaps and biases in this data that are acknowledged by the maintainers and the community?
- Could we quantify (measure, visualize) these biases in some way?
- How do these considerations affect the answers that this dataset provides (e.g., to the exploration question above)?
- Do these considerations affect the way we should use this dataset?
- Are these considerations limited to and/or influenced by the example you explored? 
- What are the unequal social relations that might underlie the data? Who benefits from this data? Who is harmed by this data? How might we challenge this unequal power structure?


### 10. What assumptions might there be in the data/this exploration?
- What type of data is represented?
- What perspectives might be excluded from this data? How might we incorporate those other perspectives?
- What binaries, classifications, and hierarchies might the data be endorsing? How might we challenge or rethink these binaries, classifications, and hierarchies?
- What predicted future does the data endorse and what assumptions underlie this predicted future?
- What mistakes might be in the data?

## Reflection and future opportunities

### 11. What lessons could be learned from exploring this dataset?
- What should we keep in mind when utilizing this dataset in the future?
- What were the major issues/bottlenecks/limitations in using this data?
- Are there best-practices that we should adopt internally and share with the rest of the community? 
- How can we communicate the limitations of our work with this data?

### 12. What future directions does this data open?
- What are other questions/explorations this dataset could be useful for?
- Are there other datasets that could be combined to this one, e.g., to correct biases, enhance coverage, add more layers to the analysis?

### 13. What future opportunities does this data bring?
- Is there space to work further on/with this dataset? 
- What outcomes/future is this data and our (chosen or potential) methodology privileging or foregoing?
- What would be nice-to-have tools that we could contribute to for this data, or that use this data?
- Would it be useful to circle back to the people maintaining/contributing to this data with some of our finds and/or proposals for collaborations?
