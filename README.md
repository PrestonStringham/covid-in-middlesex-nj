# The Effects of COVID in Middlesex County, New Jersey by Preston Stringham
DATA512 - Human-Centered Data Science

# Introduction 

COVID-19 has impacted us all in various ways, but I feel there has been no group of people more negatively impacted by COVID-19 than the hospital and healthcare workers who risk their lives to take care of people with severe cases of the virus. My problem statement addresses the impact of hospitalization rates in Middlesex County, New Jersey and how the introduction of vaccination in the United States impacted this. I intend to investigate the change  of hospitalization rate in Middlesex County, New Jersey. In particular, I am interested in the correlation in the change of  hospitalization rate and vaccination rates. In addition, I am also interested in how the hospitalization rates of JFK Medical Center in Middlesex compare to the county as a whole. The reason this is a human-centered problem is that it focuses on the impact of both healthcare and non-healthcare workers. From the perspective of non-healthcare workers, more hospital beds and resources could be used to support those suffering from non-COVID related illnesses. From the perspective of the healthcare worker, their work would be less risky as they would interact with less COVID patients than usual. During my research, I was unable to find analysis of this problem so I felt that these topics would be particularly interesting to look into and present in a reproducible manner.

# Project Structure

```
covid-in-middlesex-nj
├── 512FinalAnalysis.ipynb
├── LICENSE
├── README.md
├── data
│   └── raw
│       ├── RAW_us_confirmed_cases.csv
│       ├── hospitalizations.csv
│       ├── mandates.csv
│       ├── mask-use-by-county.csv
│       └── vaccinations.csv
└── docs
    ├── A4 - Common Analysis.pdf
    ├── A5 - Extension Plan.pdf
    ├── A6 - Presentation.pptx
    └── A7 - Project Report.pdf
```

# Data Description

5 Datasets were used to complete all analysis in my notebook.

* [COVID-19 Data Repository by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University](https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv)

This data is collected on a daily basis. Each day has its own column in the data, but I transposed it so that it is one column which I labeled as "cases." The cleaned data has the following columns.

| column  | column description   |
|-------|------------------------------|
| date  | date the data was gathered   |
| cases | number of cases for that day |

* [U.S. State and Territorial Public Mask Mandates From April 10, 2020 through August 15, 2021 by County by Day](https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i)

This data is collected on a daily basis and identifies the mask mandate policy put into place for Middlesex County. The cleaned data has the following columns.

| column  | column description   |
|-------|------------------------------|
| date  | date the data was gathered   |
| order_code | mask mandate code |

* [Mask-Wearing Survey Data, The New York Times](https://github.com/nytimes/covid-19-data/tree/master/mask-use) 

This data was collected by The New York Times about how effective mask mandates are. The cleaned data has the following columns.

| column  | column description   |
|-------|------------------------------|
| COUNTYFP | county FIPS code |
| NEVER  | percent of population that never wear masks   |
| RARELY | percent of population that rarely wear masks |
| SOMETIMES  | percent of population that sometimes wear masks   |
| FREQUENTLY | percent of population that frequently wear masks |
| ALWAYS | percent of population that always wear masks |

* [COVID-19 Reported Patient Impact and Hospital Capacity by Facility](https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/anag-cw7u) 

This data is collected weekly and contains significant information about the capacity of hospitals by facility. I needed to filter down the facilities using zip codes. The relevant data used before processing was

| column  | column description   |
|-------|------------------------------|
| collection_week  | the starting date of the week that the data was collected   |
| icu_beds_used_7_day_avg | The average number of beds used within the collection_week |

The relevant data used after processing was

| column  | column description   |
|-------|------------------------------|
| collection_week  | the starting date of the week that the data was collected   |
| daily_icu_beds_used_7_day_avg_sum_change | The change in the rate of beds used within the collection_week |

* [COVID-19 Vaccinations in the United States,County](https://data.cdc.gov/Vaccinations/COVID-19-Vaccinations-in-the-United-States-County/8xkx-amqh)

This data is collected on a daily basis. The columns relevant to my analysis are listed below.

| column  | column description   |
|-------|------------------------------|
| Date  | The date which the data was collected   |
| Administered_Dose1_Recip_18Plus | The count of the number of doses administered to people who are at least 18 years old |

# Licenses

* The COVID-19 Data Repository by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University is licensed under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license
* The U.S. State and Territorial Public Mask Mandates From April 10, 2020 through August 15, 2021 by County by Day has a terms of use provided by the CDC found  [here](https://www.cdc.gov/other/agencymaterials.html)
* The Mask-Wearing Survey Data was provided by The New York Times and the license for this data can be found [here](https://github.com/nytimes/covid-19-data/blob/master/LICENSE)
* The COVID-19 Reported Patient Impact and Hospital Capacity by Facility data was provided by healthdata.gov. I was unable to find a license or terms of use for this dataset.
* The COVID-19 Vaccinations in the United States, County dataset was obtained from the CDC and the license for this data is found [here](https://www.cdc.gov/other/agencymaterials.html)
