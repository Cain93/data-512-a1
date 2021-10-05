# Wikipedia Page View History

## Goal
This project displays the monthly page views of all English Wikipedia pages over time. Data is split out between the site it was accessed on, such as mobile or desktop, and also joins the newer pageview tracking numbers with older legacy tracking.

## Setup

### Environment
All scripts are run in Jupyter Notebook using python 3.7.9. The full list of dependencies can be found in the requirements.txt file

### How to Run
All code used is contained in the hcds-a1-data-curation.ipynb notebook. Running all cells will collect and process all data. See the description in the notebook to skip the data acquisition or processing stages.

### Stages

#### 1. Data Acquisition
Five different API requests are made, requesting desktop and mobile usage from the legacy endpoint, and desktop, mobile-site and mobile-app usage from the pageviews endpoint. All responses are saved as json files in the data folder.


## Data

### Permissions
All data is collected from the [Wikimedia REST API](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions) using the [Creative Commons Attribution-ShareAlike 3.0](https://en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License) license.

### Source
Data was collected through two API Endpoints:

* #### [Pageviews](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
This API makes available the pageviews from July 2015 and onward. Data is broken out between desktop,mobile-site and mobile-app access, and is can be filtered to exclude automated views such as web crawlers.


* #### [Legacy Pagecounts](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)
This API makes available the pagecounts from January 2008 to July 2016. Data is broken out between desktop and mobile access, and is not filtered for web crawlers or bots.

### Description

* #### Raw Data
All files in the data folder contain the exact responses of the API requests in JSON format. Files are named "<apiname>_<accesstype>_<firstmonth>-<lastmonth>.json" 

* #### Processed Data

