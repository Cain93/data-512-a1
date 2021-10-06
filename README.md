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

#### 2. Data Processing
The data from the api requests in stage is collected and combined, merging on Year and Month. The data is then pivoted to be intabular format, with one column for each API data type. Finally, the "mobile-site" and "mobile-app" counts from the pageview api are combined into just "mobile", and the total number of views, desktop + mobile, is calculated for the pageview api and legacy api. The resulting data is saved in the 'en-wikipedia_traffic_200712-202108.csv' file

#### 3. Analysis
Analysis involved graphing the values created in the processing step. Using the csv file created in Stage 2, the values are graphed on a line chart using pandas and matplotlib. Year and month are combined into dates for the x-axis, and other values are converted into billions to display on the y-axis. API (Pageview or Legacy) are encoded as blue and green lines respectively, while the different sites accessed (All, Desktop, Mobile) are encoded with line style. The result is saved as "english_wikipedia_traffic.png".

For clarity,

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
All files in the data folder contain the exact responses of the API requests in JSON format. Files are named "apiname_accesstype_firstmonth-lastmonth.json" 

* #### Processed Data
The processed data contains 164 rows and 6 columns, and is stored in the csv file en-wikipedia_traffic_200712-202108.csv
 1.  **year**: The year in YYYY format
 1. **month**: The month in MM format
 1. **pageview_desktop_views**: The number of page views for that month accessed from a desktop computer, from the pageview API, excluding crawlers and beginning in July 2015
 1. **pagecount_desktop_views**: The number of page views for that month accessed from a desktop computer, from the legacy API, including crawlers and spanning from January 2008 to July 2016
 1. **pagecount_mobile_views**: The number of page views for that month accessed from a mobile phone, from the legacy API, including crawlers and spanning from January 2008 to July 2016
 1. **pageview_mobile_views**: The number of page views for that month accessed from a mobile phone or app, from the pageview API, excluding crawlers and beginning in July 2015
 1. **pagecount_all_views**: The number of page views for that month accessed in any form, from the legacy API, including crawlers and spanning from January 2008 to July 2016
 1. **pageview_all_views**: The number of page views for that month accessed fin any form, from the pageview API, excluding crawlers and beginning in July 2015



