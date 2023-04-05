### Exploring the
# _Living Planet Index_ Database

## About this exploration

The **Living Planet Index Database** is the data behind the calculation of the [Living Planet Index](https://www.livingplanetindex.org/) (LPI), 
which aims to be _"a measure of the state of the world’s biological diversity based on population trends of vertebrate species"_. 
The LPI is a popular biodiversity indicator used in many policy-making settings, and there's some debate about how the LPI 
is computed and interpreted (and the data from which it is calculated). 
Given the relevance of the LPI for the biodiversity field, it’ll be important to try to understand the potential limitations of the index 
and those of the data behind it.

## Reproducibility notes

Most data in the LPI Database is public and can be downloaded from the LPI [data portal](https://www.livingplanetindex.org/data_portal). 
Note however that the [data use policy](https://www.livingplanetindex.org/documents/data_agreement.pdf) prohibits the publishing of the data online or on any other media. 
For this reason, in order to explore the data you will need to download it locally on your machine and place the unzipped folder in the `/lpi/data` directory.

This also means that we cannot deploy a Binder link for `lpi.ipynb`, but will need to run this love letter locally. 
Following the instructions below, create a conda environment from `environment.yml`. 
After activating it, add to it `nodejs` and `jupyterlab` (we need `nodejs` to use the Plotly extension in Jupyter).

```
conda env create -f environment.yml
conda activate lpi-env

conda install -c conda-forge nodejs --repodata-fn=repodata.json
conda install -c conda-forge jupyterlab
python -m ipykernel install --user --name=ipy-lpi-env

jupyter labextension install @jupyter-widgets/jupyterlab-manager jupyterlab-plotly
```
