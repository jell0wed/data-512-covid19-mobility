# Impact of Mobility on the COVID-19 pandemic
This final project is part of the **DATA 512 - Human-Centered Data Science (HCDS)** class from the **University of Washington**. 

The goal of this project was to explore the impact of mobility on the spread of COVID-19. We are hoping to provide more of a definitive answer as to the effectiveness of the
masking mandates employed by New Jersey’s officials as well as analyze how the mobility and
the stay-at-home orders impacted the COVID-19 infection rates throughout the pandemic.

This analysis covers **Bergen County, NJ**. 

## Pre-requisites
- python
- Jupyter notebook
- `pandas`
- `numpy`
- `matplotlib`

## Instructions
Follow these steps to reproduce the analysis locally:
- Clone this repository
- Install any missing pre-requisites
- Follow instructions on how to gather the raw data sources from [data/README.md](data/README.md)
- Launch and explore the Jupyter Notebook under `./src/`

## Folder structure
```
./
    ./data_clean    # output location for processed data
    ./data          # output location for raw data
    ./src           # jupyter notebook file location
```

## Data sources
- [Official COVID-19 data from John Hopkins University](https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv) \
 This dataset aggregates the total number of confirmed COVID-19 cases daily throughout the world. The data comes from different sources online and you can find a list of the official sources in the references. The data is refreshed daily and reports the confirmed cases of COVID-19, not necessarily the suspected cases or infections. We mainly use this report to get an accurate picture of whether the number of cases is increasing or worsening daily.

- [U.S. State and Territorial Public Mask Mandates](https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i) \
This reports the states and territorial executive orders, administrative orders, resolutions, and proclamations collected from the various US government websites. It reports the date at which such orders were issued and when they expired. At the time of writing, the dataset was last updated on September 10th, 2021. We used this data in the first part of our analysis to check whether the masking mandates were effective in countering the spread of COVID-19 in New Jersey.

- [Mask-Wearing Survey Data from the New York Times](https://github.com/nytimes/covid-19-data/tree/master/mask-use) \
This data estimates the mask use by counties in the United States. It aggregates survey data in which each participant was asked “How often do you wear a mask in public when you expect to be within six feet of another person?”. We use data to gauge whether masking mandates were uniformly respected by the population in Bergen County, NJ.

- [COVID-19 Mobility Data Aggregator (Github: ActiveConclusion/COVID19_Mobility)](https://github.com/ActiveConclusion/COVID19_mobility) \
This is a data scraper of mobility reports in different formats. As mentioned above, big technology companies such as Google and Apple released different “mobility reports” which aim to provide insights into what has changed in response to the work from home, shelter in place orders. In this analysis, we used data from the Google COVID-19 Community Mobility Reports (reports mobility trends across different categories) as well as the Apple COVID-19 Mobility Trends Reports (reports mobility trends in terms of driving, walking, and public transit). Those two reports provide the percentage change in mobility according to a baseline that was established in the pre-pandemic era.

## Data cleaning
The raw data was processed using `pandas` and the output can be found in `data_clean/` after executing the cells in the notebook. 

Final processed data schemas:

```
# day of year aggregated data of COVID-19 cases augmented with mobility data in 14d buckets
data_clean/doy_cases.csv

column                          value
------------------------------------------
doy                             datetime
dod_increase                    floating point
dod_increase_slope              floating point
retail_rec                      floating point
grocery_pharmacy                floating point
parks                           floating point
workplaces                      floating point
residential                     floating point
driving                         floating point
walking                         floating point
transit                         floating point
```

```
# cleaned RAW cases data for Bergen County NJ
data_clean/cases.csv

column              value
---------------------------
doy                 datetime
cases_count         number
```

```
# cleaned RAW mandate data for Bergen County NJ
data_clean/mandates.csv

column                          value
------------------------------------------
date                            datetime
order_code                      number
Face_Masks_Required_in_Public   boolean
```


```
# cleaned RAW masking survery data for Bergen County NJ
data_clean/masking.csv

column              value
---------------------------
COUNTYFP            number
NEVER               floating point
RARELY              floating point
SOMETIMES           floating point
FREQUENTLY          floating point
ALWAYS              floating point
```

## Analysis
The analysis itself can be found in the PDF included in this repository: [jepoisso-data512-project_report.pdf](./jepoisso-data512-project_report.pdf)

## Limitations & Future Work
Please refer to this section in the final report included in this repository. 

## Licensing
This project is under an MIT license.

- Data from John Hopkins follows the CreativeCommons Attribution 4.0
- Data from the CDC follows the official CDC privacy guidelines found here: https://www.cdc.gov/Other/privacy.html
- Data from the NYT: https://github.com/nytimes/covid-19-data/blob/master/LICENSE
- Google mobility data follows Google's Terms of Service: https://policies.google.com/terms
- Apple mobility data follows Apple's Terms of Service: https://covid19.apple.com/mobility