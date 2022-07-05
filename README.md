## dietaryindex

### Overview
___
The main goal of this package **dietaryindex** is for calculating different dietary pattern indexes or scores easily and conveniently. 

**dietaryindex** calculates dietary indexes by 2 steps:
1. Calculate the serving size of each food and nutrient category
2. Calculate the individual dietary index

Currently, **dietaryindex** can calculate AHEI, HEI2015, AHEIP, DASH, DASHI, MED, MEDI for the BLOCK FFQ and HEI2015 for NIH-AARP, NHANES, and ASA24. However, if you manually calculate the serving sizes, by using the second step of the **dietaryindex**, it would work for all existing dietary assessment tools (e.g. FFQ, ASA24, food record) to calculate all dietary indexes. 

The **dietaryindex** package relies on the **dplyr** and **readr** packages. Please install them ahead.

### Installation
___

**dietaryindex** is currently not available on [CRAN]


To install the development version hosted on this GitHub repository, use the **devtools** package and the following:

```
# install.packages("devtools")
devtools::install_github("jamesjiadazhan/dietaryindex")
```

To install the **dplyr** and **readr** packages if you are new to R or don't have them, use the following:
```
install.packages("dplyr")
install.packages("readr")
```

### Getting Started
___
```
library(dietaryindex)
library(dplyr)
library(readr)
```

The **dietaryindex** package currently contains 14 key functions:
>`HEI2015()`, Healthy Eating Index 2015 (https://www.fns.usda.gov/how-hei-scored)

>`AHEI()`, alternative healthy eating index (https://pubmed.ncbi.nlm.nih.gov/22513989/)

>`AHEIP()` , alternative healthy eating index - pregnancy (https://pubmed.ncbi.nlm.nih.gov/19465182/)

>`DASH()`, Dietary Approaches to Stop Hypertension (https://pubmed.ncbi.nlm.nih.gov/18413553/)

>`DASHI()`, Dietary Approaches to Stop Hypertension Index (modified from multiple sources to provide most updated serving size-based DASH index, including https://www.nhlbi.nih.gov/education/dash-eating-plan, https://pubmed.ncbi.nlm.nih.gov/17324731/, https://www.dietaryguidelines.gov/sites/default/files/2020-12/Dietary_Guidelines_for_Americans_2020-2025.pdf, https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/414155, https://www.nejm.org/doi/full/10.1056/nejm199704173361601)

>`MED()`, Mediterranean diet (https://pubmed.ncbi.nlm.nih.gov/33574608/)

>`MEDI()`, Mediterranean diet index, serving size-based (https://pubmed.ncbi.nlm.nih.gov/28160450/)

>`HEI2015_SERV()`, Calculate the serving sizes needed for calculating the HEI2015 dietary index per 1 day

>`AHEI_SERV()`, Calculate the serving sizes needed for calculating the AHEI dietary index per 1 day

>`AHEIP_SERV()` ,Calculate the serving sizes needed for calculating the AHEIP dietary index per 1 day

>`DASH_SERV()`, Calculate the serving sizes needed for calculating the DASH dietary index per 1 day

>`DASHI_SERV()`, Calculate the serving sizes needed for calculating the DASHI dietary index per 1 day

>`MED_SERV()`, Calculate the serving sizes needed for calculating the MED dietary index per 1 day

>`MEDI_SERV()`, Calculate the serving sizes needed for calculating the MEDI dietary index per 1 day

>`HEI2015_NHANES_FPED()`, Calculating the serving sizes for HEI2015 with 1 step using the NHANES_FPED data (after 2005)

>`HEI2015_ASA24()`, Calculating the serving sizes for HEI2015 with 1 step using the ASA24 data

### Examples:
___
#### Calculating AHEI for BLOCK
```
DATA_PATH <- "/Users/james/Desktop/data.csv"
RAW_DATA <- read_csv(DATA_PATH)

AHEI_DATA = AHEI_SERV(RAW_DATA, TYPE="BLOCK")
AHEI_DATA2 = AHEI(AHEI_DATA,   
                  VEG_SERV,
                  FRT_SERV,
                  WGRAIN_SERV,
                  NUTSLEG_SERV,
                  N3FAT_SERV,
                  PUFA_SERV,
                  SSB_FRTJ_SERV,
                  REDPROC_MEAT_SERV,
                  TRANS_SERV,
                  SODIUM_SERV,
                  ALCOHOL_SERV)
AHEI_DATA2
```

#### Calculating HEI2015 for NHANES_FPED
```
FPED_PATH = "/Users/james/Desktop/FPED.csv"
NUTRIENT_PATH = "/Users/james/Desktop/NUTRIENT.csv"
DEMO_PATH = "/Users/james/Desktop/DEMO.csv"

HEI2015RESULT = HEI2015(FPED_PATH, NUTRIENT_PATH, DEMO_PATH)
```

### Related Work
___

**dietaryindex** is mainly intended as a tool to help for calculating different dietary indexes with given food/nutrient serving sizes. It is designed to be flexible to work for almost all types of dietary assessment tools, including food frequency questionnaires, 24-hours dietary recalls, and even food records. Please follow the instruction of your specific dietary assessment tools and relevant articles regarding how to accurately define the serving size (see above) if it is not provided in our package, as they are the key to obtain high-quality dietary indexes. **dietaryindex** also provides some help in defining the serving size in the help file, argument section. 

This package requires the **dplyr** and **readr** packages to be installed. Library statements of the dplyr and readr packages are included for your convenience. 

### Contributing

**dietaryindex** is licensed under the [MIT License]. Please check out the [Contribution guide](https://github.com/jamesjiadazhan/dietaryindex/blob/main/CONTRIBUTING.md) for questions, feature requests and bug reports. The maintainer will review pull requests and incorporate contributions at his discretion. You may also reach out to the maintainer, James Jiada Zhan, via his email: jzha832@emory.edu.
