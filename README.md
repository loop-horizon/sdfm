# Simplified Data for Marketing (SDfM) Schema

The Simplified Data for Marketing (SDfM) model is designed to enable rapid activation of customer data across multiple digital touchpoints.  The SDfM schema can be deployed within your data warehouse and has been architected to provide all the required data points to integrate customer data with the following endpoints: 

```bash
* Adobe Experience Cloud
* Google Ads
* Facebook Ads
....
```



This repositary contains the source code and specification of the SDfM model, using data definition langauge.





| Category            | Sub-Category  | Field                  | Description |
| ------------------- | ------------- | ---------------------- | ----------- |
| IDENTITY            | CRM           | CUSTOMER\_ID           | The primary customer ID used for syncing data (Adobe Analytics/GA)            |
|                     |               | EMAIL\_ADDRESS         | Email address include @           |
|                     |               | FIRST\_NAME            | First name of customer         |
|                     |               | LAST\_NAME             | Surname of customer           |
|                     |               | TEL\_NUMBER            | Mobile or landline number - use E.164 format Remove symbols, letters, and any leading zeroes. You should prefix the country code  |
|                     |               | GENDER                 |  M = Male F = Female          |
|                     |               | DOB                    |  DD/MM/YYYY Format          |
|                     |               | ZIP\_CODE              |             |
|                     |               | CITY                   |             |
|                     |               | COUNTRY                |             |
|                     | PLATFORMS     | ECID                   |             |
|                     |               | MOBILE\_ADVERTISER\_ID |             |
|                     |               | FBP                    |             |
|                     |               | FBCLID                 |             |
|                     |               | GCLID                  |             |
|                     | CONSENT       | OPT\_IN\_MARKETING     |             |
|                     |               | OPT\_IN\_SERVICE       |             |
|                     |               | OPT\_IN\_COOKIES       |             |
| CUSTOMER            |               | CUSTOMER\_STATUS       |             |
|                     |               | CUSTOMER\_START\_DT    |             |
|                     |               | CUSTOMER\_END\_DT      |             |
|                     |               | TENURE                 |             |
|                     |               | MARKETING\_CHAN        |             |
| PRODUCT HOLDING     |               | PRODUCT\_NAME          |             |
|                     |               | PRODUCT\_STATUS        |             |
|                     |               | PRODUCT\_START\_DT     |             |
|                     |               | PRODUCT\_END\_DT       |             |
|                     |               | MARKETING\_CHAN        |             |
| PLATFORM ENGAGEMENT | WEB           | VISIT\_COUNT           |             |
|                     |               | LAST\_VISIT\_DT        |             |
|                     | APP           | VISIT\_COUNT           |             |
|                     |               | LAST\_VISIT\_DT        |             |
|                     | EMAIL         | EMAIL\_OPENS           |             |
|                     |               | EMAIL\_CLICKS          |             |
|                     |               | LAST\_EMAIL\_OPEN\_DT  |             |
|                     | VOICE         | CALL\_VOLUME           |             |
|                     |               | LAST\_CALL\_DT         |             |
| INTELLIGENCE        | MODEL\_SCORES | MODEL\_NAME1           |             |
|                     |               | MODEL\_NAME2           |             |
|                     | SEGMENTATIONS | SEGMENT1               |             |
|                     |               | SEGMENT2               |             |
