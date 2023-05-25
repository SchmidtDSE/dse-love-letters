# BioTIME SQLite repackaging

_A Samuel Pottinger_ and _Giulia Zarpellon_
March 29, 2023

## Background

**BioTIME is an open "global database of assemblage time series for quantifying and understanding biodiversity change"**
([BioTIME website](https://biotime.st-andrews.ac.uk/)).
- Indeed, it claims to be the "largest compilation of biodiversity time series containing raw data on species identities and 
abundances from ecological assemblage" ([BioTIME Consortium](https://biotime.st-andrews.ac.uk/downloads/interactBioTIME.html#using-the-mysql-database)).
- The full dataset is available on [Zenodo](https://zenodo.org/record/5026943#.ZCTxHrzMJyo)
  - The dataset is packaged as a `.sql` file (see [BioTIMESQL_24_06_2021.zip](https://zenodo.org/record/5026943/files/BioTIMESQL_24_06_2021.zip?download=1))
  - Licence is CC-BY-4.0: https://creativecommons.org/licenses/by/4.0/legalcode
  - Citation: Dornelas M, Antão LH, Moyes F, Bates, AE, Magurran, AE, et al. BioTIME: A database of biodiversity time series for the Anthropocene. Global Ecol Biogeogr. 2018; 27:760 - 786. https://doi.org/10.1111/geb.12729

## Purpose

**This micro-project repackages the BioTIME dataset as a SQLite file.** 
- To use the full BioTIME dataset, one needs to spin up and secure a MySQL database server in addition to loading a sql dump, 
downloading / using db-specific software in the process.
- In contrast, SQLite does not require a server (providing a better security footprint) and can be downloaded / used directly from file storage.
- Often SQLite can be used without additional software installations, like in Python with `sqlite3`. 
- The database contains multiple tables, some quite large. So a database (as opposed to a CSV) may be appropriate.

## Usage

**Download:** TODO: CHECK LINK WRT LICENCING
- Licence / credits: [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)
  - A Samuel Pottinger, Giulia Zarpellon, and Regents of University of California
  - Dornelas M, Antão LH, Moyes F, Bates, AE, Magurran, AE, et al. BioTIME: A database of biodiversity time series for the Anthropocene. Global Ecol Biogeogr. 2018; 27:760 - 786. https://doi.org/10.1111/geb.12729
- Load into your environment of choice
  - Pandas can read sqlite pretty easily: https://pythonspot.com/sqlite-database-with-pandas/
  - DBeaver is a great UI: https://dbeaver.io/
  - Also plugging SQLite browser: https://sqlitebrowser.org/

## Reproducing

**The dataset can be used without these steps by downloading from the link above, but the SQLite database can be reproduced using the following method.**
- Get the data: https://zenodo.org/record/5026943/files/BioTIMESQL_24_06_2021.zip?download=1
- Spin up a mysql database
  - Because this was small enough, we could grab one from pythonanywhere (since local can be a bit of a security bummer): 
  https://help.pythonanywhere.com/pages/UsingMySQL/
  - You can run local easily on Linux
- Connect to the database
  - Most remote databases require ssh tunneling
  - Connecting to pythonanywhere MySQL: https://help.pythonanywhere.com/pages/AccessingMySQLFromOutsidePythonAnywhere/
- Load the dump
  - You will need MySQL client: `apt-install mysql-client`
  - Connect to the port forwarded db: `mysql -u [pythonanywhere username] -p localhost`
  - Choose database: `USE [default db name]`
  - Load the dump file: `SOURCE [path to sql file]`
- Translate to SQLite
  - DBeaver uses the JDBC to support this, and it's one of the few open sources tools we've seen offer this kind of data migration function
  - The DBeaver community is open source: https://dbeaver.io/
  - Used data migration feature to move between db engines / sql dialects: https://github.com/dbeaver/dbeaver/wiki/Data-migration

## Notes

- Running Postgres local on Mac is a bit more fun: https://postgresapp.com/
- MySQL on Mac is sometimes a little less fun but possible: https://medium.com/macoclock/mysql-on-mac-getting-started-cecb65b78e