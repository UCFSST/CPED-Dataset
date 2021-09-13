# CPED-Dataset
Dataset used for the Crash Prediction for Expedited Detection system (CPED)

## Notes on Standards Used

### Data Files
The dataset utilizes open file formats and does not contain any proprietary formats. The following file formats are utilized in the dataset:

- Traffic data, Event data, CCTV data:
  * csv: Comma Separated Value
- CCTV Snapshots:
  * jpeg: Joint Photographic Experts Group
- GIS data:
  * cpg: code page specification
  * dbf: attribute format
  * prj: GIS project description
  * sbn, sbx: spatial feature index
  * shp: feature geometry
  * shp.xml: geospatial metadata in extensible markup language (XML) format
  * shx: shape index format

Comma Separated Value (CSV) file format can be viewed or edited using any general text editor. However, csv files are best viewed using spreadsheet software, e.g., Microsoft Excel (https://www.microsoft.com/en-us/microsoft-365/excel). The GIS data can be viewed or edited using any commercial GIS software such as ArcGIS (https://www.arcgis.com) or QGIS (https://www.qgis.org).

### Metadata
The DCAT-US Schema v1.1 (Project Open Data Metadata Schema) (https://resources.data.gov/resources/dcat-us/) was used to create the dataset machine-readable metadata. Additionally, the JavaScript Object Notation (JSON) file format was used to create the metadata file.


## Data Dictionary
### Traffic Data
#### Traffic/C2C_Traffic.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| createdDate | Record Timestamp |	Date and time when the data was uploaded | Always |
| keySet | Roadway Identifier | A dictionary includes network id and link id | Always |
| occupancy | Average Occupancy	| Percent of time a point on the road is occupied by vehicles (%) |  Always (Zero: Occupancy is zero because volume is zero) |
| speed | Average Speed	| Average speed during last 1 minute (mph) | Always (Zero: Average speed is zero because volume is zero) |
| travelTime | Averagt Travel Time | Average travel time among all travel lanes (second) | Always (Zero: Travel time is zero because volume is zero) |
| volume | Total Volume | Number of vehicles counted within last 1 minute for the roadway link for all travel lanes | Always (Zero: Total volume is zero) |

#### Traffic/Inventory.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| zone_id	| Detector Station ID	| Unique IDs for each detector station |	Always |
| display_name	| Displayed | Detector Name	More detailed information of each detector helps users understand location, direction, and route |	If-Applicable |
| timezone	| Time zone	| Time zone of detector location |	If-Applicable |
| road	| Road Name	| Roadway name where the detector located |	Always |
| direction	| Roadway Direction	| Directional information helps users identify the direction of roadway |	Always |
| latitude	| Latitude |	Latitude of detector location |	Always |
| longitude	| Longitude |	Longitude of detector location | Always |
| interval	| Aggregation | Level	Aggregation level (seconds) |	Always |

#### Traffic/Zone_Readings.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| zone_id |	Detector Station ID |	Unique IDs for each detector station	| Always |
| measurement_start |	Measurement Start Time |	Timestamps help users identify the starting time of measurement | Always |
| speed |	Speed	Average | speed of each time period (mile/hour), 	| Always (Zero: Average speed is zero because volume is zero) |
| volume |	Volume |	Total volume of each time period (vehicles)	| Always (Zero: Total volume is zero) |
| occupancy |	Occupancy |	Occupancy of each time period (%) 	| Always (Zero: Occupancy is zero because volume is zero) |
| quality |	Data Quality |	The quality of raw data (1: good)	| If-Applicable |


### Event Data
#### Event/C2C_Event.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| id | Record Identifier | Event identification number. Each event maintains the same id across all of its new, update, and delete entries | Always |
| createdDate | Record Creation Timestamp | Entry creation timestamp | Always |
| latitude | Latitude | Event location latitude | Always |
| longitude	| Longitude | Event location longitude | Always |
| roadCond | Road Condition | Road condition (dry/wet) | If-Applicable |
| severity | Severity | Severity (major/minor) | If-Applicable |
| source | Source | Reporting agency | If-Applicable |
| startTimestamp | Event Start Timestamp | Event start timestamp | Always |
| status | Status | Event status | If-Applicable |
| type | Type | Event type | Always |
| typeDesc | Type Description | Event type description | Always |
| unconfirmedBlockages | Is Unconfirmed Road Blockage| Boolean field indicating unconfirmed road blockages | If-Applicable |
| updateTimestamp	| Event Update Timestamp | Event update timestamp | Always |
| updateType | Record Update Type | Record update type (new/update/delete) | Always |
| weatherCond	| Weather Condition | Weather condition at time of event | If-Applicable |

#### Event/Crash_Data.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| HSMV_Report_Number	| HSMV Report Number	Crash report number according to HSMV	| Always |
| Crash_Date	| Crash Date | Crash date	vAlways (Null: Missing value) |
| Crash_Time	| Crash Time |	Crash time	| Always (Null: Missing value) |
| County	| County |	County of crash location	| If-Applicable (Null: Missing value) |
| Crash_Street	| Crash Street |	Street name helps users identify roadway where the crash occurred	| Always (Null: Missing value) |
| Crash_Type	| Crash Type |	Crash Type (Rear end, Sideswipe, and Angle) 	| If-Applicable (Null: Missing value) |
| Weather_Condition	| Weather Condition |	Weather condition (Clear, Cloudy, Rain)	| If-Applicable (Null: Missing value) |
| Crash_Severity	| Crash Severity |	Crash severity (Fatal, Injury, and Property damage only) 	| If-Applicable (Null: Missing value) |
| Possible_Injuries	| The Number of Possible Injuries |	Information helps users categorize crash severity type into KABCO (C)	| If-Applicable (Zero: The number of possible injuries is zero) |
| Non_Incapacitating_Injuries	| The Number of Non-Incapacitating Injuries |	Information helps users categorize crash severity type into KABCO (B)	| If-Applicable (Zero: The number of non-incapacitating injuries is zero) |
| Incapacitating_Injuries	| The Number of Incapacitating Injuries |	Information helps users categorize crash severity type into KABCO (A)	| If-Applicable (Zero: The number of incapacitating injuries is zero) |
| Fatalities_30_Days | The Number of Fatal Injuries |	Information helps users categorize crash severity type into KABCO (K)	| If-Applicable (Zero: The number of fatal injuries is zero) |
| S4_Decimal_Degree_Longitude	| Longitude of Crash | Location	Longitude of Crash Location	| Always (Zero or Null: Missing value) |
| S4_Decimal_Degree_Latitude | Latitude of Crash | Location	Latitude of Crash Location	| Always (Zero or Null: Missing value) |


### CCTV Data
#### CCTV/I-4-Cameras.csv, CCTV/CFX-Cameras.csv, CCTV/TPK-Cameras.csv

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| Camera_Name | Camera Name	| Camera display name which includes roadway and milepost | Always |
| URL |	URL	| Livestream URL (RTSP/UDP) | Always |
| Latitude |	Latitude| Camera latitude value | Always |
| Longitude |	Longitude	| Camera longitude value | Always |


### GIS Data
#### Florida.shp

| Field |	Label |	Description   |	Required |
| ----- | ----- | ------------- | -------- |
| Tmc	| Traffic Message Channel | Unique link id based on TMC segment	| If-Applicable |
| RoadName | Road Name	| Route Name	| Always (Null: Missing value) |
| FirstName	| Detailed Location of Route | Detailed Location of Route	| Always (Null: Missing value) |
| Country	| Country	| Country	| If-Applicable |
| State	| State	| State where the link located	| If-Applicable |
| County | County	| County where the link located	| If-Applicable |
| Zip	| Zip Code | Zip code where the link located	| If-Applicable |
| Direction	| Roadway Direction	| Direction of link	| Always (Null: Missing value) |
| StartLat | Latitude of Start Point of Link	| Starting point helps users determine the sequence of links	| Always |
| StartLong	| Longitude of Start Point of Link	| Starting point helps users determine the sequence of links	| Always |
| EndLat | Latitude of End Point of Link	Ending | point helps users determine the sequence of links	| Always |
| EndLong	| Longitude of End Point of Link	Ending | point helps users determine the sequence of links	| Always |
| Miles	| Length of Link	| Length of link in miles	| Always |
| Urban_Code | Urban Code	| Helps users identify urban or rural	| If-Applicable |
| ThruLanes	| Number of Thru Lanes	| Identify the number of thru lanes	| If-Applicable |
| Route_Numb | Route Number	| Identify route number	| Always (Null: Missing value) |
| AADT | Annual Average Daily Traffic	| Annual average daily traffic for each link	| If-Applicable |

