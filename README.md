# Official README for Natural Disaster Sentiment Analysis
##### By Scott Burstein

### Context 

The United States experience a large variety of natural disasters each year: devastating hurricanes, seasonal tornadoes, and scorching wild fires are among the events that endanger many lifes and cause billions of dollars in damages. The Federal Emergency Management Agency ([FEMA](https://www.fema.gov/)) is in charge of [\"helping people before, during, and after disasters\"](https://www.fema.gov/about-agency) by coordinating disaster response and providing relief funds ([see also wikipedia](https://en.wikipedia.org/wiki/Federal_Emergency_Management_Agency)). Original Kaggle developer will update the master dataset regularly.

Note, that the data also includes biological disasters, in particular declarations made in response to the ongoing Covid-19 pandemic.

### Content

This summary dataset is a high-level summary of all federally declared disasters since 1953. It was downloaded from the [FEMA website](https://www.fema.gov/openfema-dataset-disaster-declarations-summaries-v2) and applied a few simple data cleaning and formatting measures. The features of the main dataset will be described in detail right below. 

In addition, I provide a sub-dataset that is tailored to the parameters of the ongoing effort to forecast
Google trends data in relation to climate catastrophe; which is outlined below the main one.
Navigating climate tragedies in the near-term future is a likely reality 
([see Deep Adaptation](https://mahb.stanford.edu/wp-content/uploads/2018/08/deepadaptation.pdf)).

* `us_disaster_declarations.csv`: the full dataset with all rows and columns. The geographical resolution is the county level, with [FIPS codes](https://en.wikipedia.org/wiki/FIPS_county_code) being used to encode the counties. In addition to the fips and timing features, the data provides the type of disaster and also binary flags that indicate whether specific aid programs were triggered in response.
- `us_disasters_m5.csv`: the M5-specific subset. Constrained to the 3 states CA, TX, and WI; as well as to the time range of Jan 2011 - June 2016. Original creator also removed a few columns that they considered unnecessary for more tailored analysis.
- `small_FEMA`: Constrained data frame I made to analyze FEMA declarations from the most recent 5 years (tabulated when knit), in the top n states and territories that recorded the most natural disasters (FEMA declarations) during that time period.
Can be modified to only view statewide emergencies, as opposed to also including regional and small-scale emergencies.

### Column Description

Most of those descriptions have been taken verbatim from the [FEMA website](https://www.fema.gov/openfema-dataset-disaster-declarations-summaries-v2). Small clarifications have been added to some of them:

Full dataset `us_disaster_declarations.csv`:

* `fema_declaration_string`: Agency standard method for uniquely identifying Stafford Act declarations. Concatenation of `declaration_type`, `disaster_number` and `state`.
- `disaster_number`: Sequentially assigned number used to designate an event or incident declared as a disaster.
- `state`: US state, district, or territory.
- `declaration_type`: One of \"DR\" (= major disaster), \"EM\" (= emergency management), or \"FM\" (= \"fire management\")
- `declaration_date`: Date the disaster was declared.
- `fy_declared`: Fiscal year in which the disaster was declared.
- `incident_type`: Type of incident such as \"Fire\", \"Flood\", or \"Hurricane\". The incident type will affect the types of assistance available.
- `declaration_title`: \tTitle for the disaster. This can be a useful identifier such as \"Hurricane Katrina\" or \"Covid-19 Pandemic\".
- `ih_program_declared`: Binary flag indicating whether the \"Individuals and Households program\" was declared for this disaster.
- `ia_program_declared`: Binary flag indicating whether the \"Individual Assistance program\" was declared for this disaster.
- `pa_program_declared`: Binary flag indicating whether the \"Public Assistance program\" was declared for this disaster.
- `hm_program_declared`: Binary flag indicating whether the \"Hazard Mitigation program\" was declared for this disaster.
- `incident_begin_date`: Date the incident itself began.
- `incident_end_date`: Date the incident itself ended. This feature has about 14% NA entries.
- `disaster_closeout_date`: Date all financial transactions for all programs are completed. This column has 98% NA entries.
- `fips`: 5-digit FIPS county code; used to identify counties and county equivalents in the United States, the District of Columbia, US territories, outlying areas of the US and freely associated states. Concatenated from the 2 source columns \"fipsStateCode\" and \"fipsCountyCode\".
- `place_code`: A unique code system FEMA uses internally to recognize locations that takes the numbers '99' + the 3-digit county FIPS code. There are some declared locations that don't have recognized FIPS county codes in which case a unique identifier was assigned.
- `designated_area`: The name or phrase describing the U.S. county that was included in the declaration. Can take the value \"Statewide\".
- `declaration_request_number`: Unique ID assigned to request for a disaster declaration.
- `hash`: MD5 Hash of the fields and values of the record.
- `last_refresh`: Date the record was last updated by FEMA.
- `id`: Unique ID assigned to the record. Those last 4 columns are primarily for bookkeeping.

M5-specific dataset `us_disasters_m5.csv`: **[NOT USED FOR THIS ANALYSIS]**

* `disaster_number`: Sequentially assigned number used to designate an event or incident declared as a disaster.
- `state`: One of the three states \"CA\", \"TX\", or \"WI\".
- `declaration_type`: One of \"DR\" (= major disaster), \"EM\" (= emergency management), or \"FM\" (= \"fire management\")
- `declaration_date`: Date the disaster was declared.
- `incident_type`: Type of incident such as \"Fire\", \"Flood\", or \"Biological\". The incident type will affect the types of assistance available.
- `declaration_title`: \tTitle for the disaster.
- `ih_program_declared`: Binary flag indicating whether the \"Individuals and Households program\" was declared for this disaster.
- `ia_program_declared`: Binary flag indicating whether the \"Individual Assistance program\" was declared for this disaster.
- `pa_program_declared`: Binary flag indicating whether the \"Public Assistance program\" was declared for this disaster.
- `hm_program_declared`: Binary flag indicating whether the \"Hazard Mitigation program\" was declared for this disaster.
- `incident_begin_date`: Date the incident itself began.
- `incident_end_date`: Date the incident itself ended. The M5 constraint is that the disaster must have begun before the start of the evaluation time period on 2016-05-23 and ended on or after the begin of the training data range on 2011-01-29. This feature has about 14% NA entries, which were considered under the assumption that start data = end date.
- `fips`: 5-digit FIPS county code; used to identify counties and county equivalents in the United States, the District of Columbia, US territories, outlying areas of the US and freely associated states. Concatenated from the 2 source columns \"fipsStateCode\" and \"fipsCountyCode\".
- `designated_area`: The name or phrase describing the U.S. county that was included in the declaration.

### Acknowledgements

All the credit goes to FEMA for building and maintaining this dataset.

### Source Description

Kaggle Data Source accessible [here](https://www.kaggle.com/headsortails/us-natural-disaster-declarations)

This code book is a modified version of user *Heads or Tails'* 

**US Natural Disaster Declarations:**
County-level data from the Federal Emergency Management Agency: 1953 - today

data set (Version 15 updated as of 11/14/2020) accessible [here](view-source:https://www.kaggle.com/headsortails/us-natural-disaster-declarations)

### Licence

Data and content created by government employees within the scope of their employment are not subject to domestic copyright protection under 17 U.S.C. § 105. Government works are by default in the U.S. Public Domain. ","url":"https://www.kaggle.com/headsortails/us-natural-disaster-declarations","sameAs":"","version":15,"keywords":["subject, people and society, business","subject, people and society, law, government","subject, health and fitness, health, health conditions, diseases, covid19","subject, people and society, law, government, public safety","subject, earth and nature, environment, natural disasters"],"license":{"@type":"CreativeWork","name":"U.S. Government Works","url":"https://www.usa.gov/government-works/"},"identifier":["619729"],"includedInDataCatalog":{"@type":"DataCatalog","name":"Kaggle","url":"https://www.kaggle.com"},"creator":{"@type":"Person","name":"Heads or Tails","url":"https://www.kaggle.com/headsortails","image":"https://storage.googleapis.com/kaggle-avatars/thumbnails/1014468-kg.jpg"},"distribution":[{"@type":"DataDownload","requiresSubscription":true,"encodingFormat":"zip","fileFormat":"zip","contentUrl":"https://www.kaggle.com/headsortails/us-natural-disaster-declarations/download","contentSize":"15985285 bytes"}],"commentCount":0,"dateModified":"2020-11-14T21:08:01.637","discussionUrl":"https://www.kaggle.com/headsortails/us-natural-disaster-declarations/discussion","alternateName":"County-level data from the Federal Emergency Management Agency: 1953 - today","isAccessibleForFree":true,"thumbnailUrl":"https://storage.googleapis.com/kaggle-datasets-images/619729/1106528/539f2881e8132cb536c4ddeb685356d5/dataset-card.jpg?t=2020-04-25-02-03-50","interactionStatistic":[{"@type":"InteractionCounter","interactionType":"http://schema.org/CommentAction","userInteractionCount":0},{"@type":"InteractionCounter","interactionType":"http://schema.org/DownloadAction","userInteractionCount":575},{"@type":"InteractionCounter","interactionType":"http://schema.org/ViewAction","userInteractionCount":3991},{"@type":"InteractionCounter","interactionType":"http://schema.org/LikeAction","userInteractionCount":45}]}
    

    