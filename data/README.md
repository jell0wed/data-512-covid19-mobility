# HOWTO: Gather the data
In order to keep the size of this directory small, we excluded the data used in this project. 

In case you wish to run this analysis locally, please place the data file here according to the following file structure:

```
data/mask-mandates-by-country.csv  # https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i
data/make-use-by-county.csv        # https://github.com/nytimes/covid-19-data/tree/master/mask-use
data/RAW_us_confirmed_cases.csv    # https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?sel=
data/COVID19_mobility              # git clone https://github.com/ActiveConclusion/COVID19_mobility
```

## Mobility reports
After cloning the following repo in `data/COVID19_mobility`, please following the following steps in order to scrape and gather the data. 
If you encounter any issue, please refer to the instructions provided in the GitHub repo: https://github.com/ActiveConclusion/COVID19_mobility

```
cd data/COVID19_mobility
pip install -r requirements.txt
python scraper.py run-all
```