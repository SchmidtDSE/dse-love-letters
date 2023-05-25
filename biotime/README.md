### Exploring the
# _BioTIME_ Database

Full citation of materials:
> Dornelas M, Antão LH, Moyes F, Bates, AE, Magurran, AE, et al. BioTIME: A database of biodiversity time series for the Anthropocene. Global Ecol Biogeogr. 2018; 27:760 - 786. https://doi.org/10.1111/geb.12729

## About this exploration

The **BioTIME database** is an open _"global database of assemblage time series for quantifying and understanding biodiversity change"_
([BioTIME website](https://biotime.st-andrews.ac.uk/)). Here we explore its structure and content, 
discussing potential opportunities and other interesting investigations it could serve. 

## Reproducibility notes

BioTIME data is open and can be access through a custom search or in its entirety via the BioTIME [download page](https://biotime.st-andrews.ac.uk/download.php). 
The dataset is also [hosted in Zenodo](https://zenodo.org/record/5026943#.ZC8o7ezMLdp). 
[Data usage guidelines](https://biotime.st-andrews.ac.uk/usageGuidelines.php) require respecting the licenses associated to the datasets for each study included in the database, 
which can vary across the database but should generally be on the open side (Creative Commons and Open Licences, as discussed [here](https://biotime.st-andrews.ac.uk/usageGuidelines.php)). 
For BioTIME itself, licence is CC-BY-4.0 (see details [here](https://creativecommons.org/licenses/by/4.0/legalcode)). 

Following the instructions below, create a conda environment from `environment.yml`. After activating it, add to it `nodejs` and `jupyterlab` 
(we need `nodejs` to use the Plotly extension in Jupyter).
```
conda env create -f environment.yml
conda activate biotime-env

conda install -c conda-forge nodejs --repodata-fn=repodata.json
conda install -c conda-forge jupyterlab
python -m ipykernel install --user --name=ipy-lpi-env

jupyter labextension install @jupyter-widgets/jupyterlab-manager jupyterlab-plotly
```
Data is available in different formats:
1. **Full database SQL zip file** (1.01 GB unzipped). This `.sql` file is meant to be loaded into a MySQL database. 
2. **Raw data in `.csv` zip file** (1.22 GB unzipped). 

We downloaded both, but repackaged the MySQL into a sqlite database. Instructions to reproduce this step 
(and direct download link to the newly created `.db` file) can be found in `sqlite-repackaging.md`.
To run the `biotime.ipynb` notebook, local data should be placed in `biotime/data`.
