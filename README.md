# Simplified Data for Marketing (SDfM) Schema

The Simplified Data for Marketing (SDfM) model is designed to enable rapid activation of customer data across multiple digital touchpoints.  The SDfM schema can be deployed within your data warehouse and has been architected to contain all required variables to integrate customer data with the following endpoints : 

```bash
* Adobe Experience Cloud
* Google Ads
* Facebook Ads
* SFMC
* TikTok
* Twitter
* LinkedIn
* Sky AdSmart
* Infosum
```


| Category            | Sub-Category   | Field                                | DataType   | Nullable | Exclude from UI (Builder) | UI Category Name | Description/Format                                                                                                                                                                                                              |
|---------------------|----------------|--------------------------------------|------------|----------|---------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IDENTITY            | CRM            | CUSTOMER_ID(PK)                      | VARCHAR    | 0        | X                         | -                | Primary key for the table - internal customer id                                                                                                                                                                                |
|                     |                | EMAIL_ADDRESS_<1>                    | VARCHAR    | 0        | X                         | -                | Full email address including prefix and domain. If more than 1 email address per customer_id then add new field with the following format email_address_2, email_address_3 etc.                                                 |
|                     |                | FIRST_NAME                           | VARCHAR    | 1        | X                         | -                | Use a-z only. Lowercase only, no punctuation. Special characters in UTF-8 format.                                                                                                                                               |
|                     |                | LAST_NAME                            | VARCHAR    | 1        | X                         | -                | Use a-z only. Lowercase only, no punctuation. Special characters in UTF-8 format.                                                                                                                                               |
|                     |                | TEL_NUMBER_<1>                       | VARCHAR    | 1        | X                         | -                | Remove symbols, letters, and any leading zeroes. You should prefix the country code. (E.g 447851434349). If more than 1 tel_number per customer_id then add new field with the following format tel_number_2, tel_number_3 etc. |
|                     |                | GENDER                               | VARCHAR(1) | 1        |                           | DEMOGRAPHICS     | Use these values: m for male, f for female.                                                                                                                                                                                     |
|                     |                | DOB                                  | DATE       | 1        | X                         | -                | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     |                | BIRTHDAY_DAYS                        | INT        | 1        |                           | DEMOGRAPHICS     | Number of days until Biirthday. 0 = Birthday                                                                                                                                                                                    |
|                     |                | AGE                                  | INT        | 1        |                           | DEMOGRAPHICS     | Age derived from DOB field                                                                                                                                                                                                      |
|                     |                | ZIP_CODE                             | VARCHAR    | 1        | X                         | -                | Use lowercase, and no white space                                                                                                                                                                                               |
|                     |                | CITY                                 | VARCHAR    | 1        |                           | LOCATION         | Use a-z only. Lowercase only, with no punctuation, no special characters, and no white space.                                                                                                                                   |
|                     |                | STATE                                | VARCHAR    | 1        |                           | LOCATION         | Use the 2-character ANSI abbreviation code, lowercase. Normalize states outside the US in lowercase, with no punctuation, no special characters, and no white space.                                                            |
|                     |                | COUNTRY                              | VARCHAR    | 1        |                           | LOCATION         | Use lowercase, 2-letter country codes in ISO 3166-1 alpha-2.                                                                                                                                                                    |
|                     | PLATFORMS      | ECID                                 | VARCHAR    | 1        | X                         | -                | (Most recent) Adobe Experience Cloud ID                                                                                                                                                                                         |
|                     |                | MOBILE_ADVERTISER_ID                 | VARCHAR    | 1        | X                         | -                | (Most recent) Use all lowercase, and keep hyphens. Mobile device ID (advertising ID/IDFA).                                                                                                                                      |
|                     |                | FBP                                  | VARCHAR    | 1        | X                         | -                | (Most recent) Facebook Cookie ID                                                                                                                                                                                                |
|                     |                | FBC                                  | VARCHAR    | 1        | X                         | -                | (Most recent) Facebook Click ID                                                                                                                                                                                                 |
|                     |                | FB_EXTERNAL_ID                       | VARCHAR    | 1        | X                         | -                | External_id used in advanced customer matching for Facebook Pixel                                                                                                                                                               |
|                     |                | USERID                               | VARCHAR    | 1        | X                         | -                | (Most recent)Google Ads - Advertiser generated and assigned user ID. Accessible to whitelisted Google clients only.                                                                                                             |
|                     |                | GCLID                                | VARCHAR    | 1        | X                         | -                | (Most recent) Google Ads Click ID                                                                                                                                                                                               |
|                     | CONSENT        | GLOBAL_MARKETING_CONSENT_OPT_IN      | INT        | 0        | X                         | -                | Use these values:  1  for consent 0 for no consent                                                                                                                                                                              |
|                     |                | EMAIL_CONSENT                        | INT        | 1        |                           | CONSENT          | Use these values:  1  for consent 0 for no consent                                                                                                                                                                              |
|                     |                | TEL_CONSENT                          | INT        | 1        |                           | CONSENT          | Use these values:  1  for consent 0 for no consent                                                                                                                                                                              |
|                     |                | SMS_CONSENT                          | INT        | 1        |                           | CONSENT          | Use these values:  1  for consent 0 for no consent                                                                                                                                                                              |
|                     |                | DM_CONSENT                           | INT        | 1        |                           | CONSENT          | Use these values:  1  for consent 0 for no consent                                                                                                                                                                              |
| CUSTOMER            |                | CUSTOMER_STATUS                      | VARCHAR    | 1        |                           | CUSTOMER         | The status of the customer. Example: 'Active', 'Prospect', 'Lapsed'                                                                                                                                                             |
|                     |                | CUSTOMER_START_DT                    | DATE       | 1        |                           | CUSTOMER         | DD-MM-YYYY   - Date the customer/prospect was acquired                                                                                                                                                                          |
|                     |                | CUSTOMER_END_DT                      | DATE       | 1        |                           | CUSTOMER         | DD-MM-YYYY  - Date customer/prospect went from Active to Inactive                                                                                                                                                               |
|                     |                | CUSTOMER_TENURE_DAYS                 | INT        | 1        |                           | CUSTOMER         | Number of days as a customer                                                                                                                                                                                                    |
|                     |                | CUSTOMER_ACQUISITION_CHAN            | VARCHAR    | 1        |                           | CUSTOMER         | Last touch channel (E.g. Google PPC)                                                                                                                                                                                            |
| PRODUCT HOLDING     | CURRENT        | <PRODUCT_NAME>                       | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Product holding.  One field per product holding. For example: Motor_Insurance, Travel_Insurance                                                                                                                                 |
|                     |                | <PRODUCT_NAME>_STATUS                | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Status of the product  e.g. 'Active' , 'Lapsed'.                                                                                                                                                                                |
|                     |                | <PRODUCT_NAME>_START_DT              | DATE       | 1        |                           | PRODUCT HOLDING  | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_END_DT                | DATE       | 1        |                           | PRODUCT HOLDING  | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_ACQUISITION_CHAN      | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Last touch channel (E.g. Google PPC)                                                                                                                                                                                            |
|                     | HISTORY        | <PRODUCT_NAME>_HIST                  | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Previous product holding (last product status change)                                                                                                                                                                           |
|                     |                | <PRODUCT_NAME>_HIST_STATUS           | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Previous product holding status                                                                                                                                                                                                 |
|                     |                | <PRODUCT_NAME>_HIST_START_DT         | DATE       | 1        |                           | PRODUCT HOLDING  | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_HIST_END_DT_HIST      | DATE       | 1        |                           | PRODUCT HOLDING  | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_HIST_ACQUISITION_CHAN | VARCHAR    | 1        |                           | PRODUCT HOLDING  | Last touch channel  of previous product holding (E.g. Google PPC)                                                                                                                                                               |
| PLATFORM ENGAGEMENT | WEB            | WEB_VISIT_COUNT_30_DAYS              | INT        | 1        |                           | ENGAGEMENT       | Totla number of web visits in the last 30 days.                                                                                                                                                                                 |
|                     |                | WEB_LAST_VISIT_DT                    | DATE       | 1        |                           | ENGAGEMENT       | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     | APP            | APP_VISIT_COUNT_30_DAYS              | INT        | 1        |                           | ENGAGEMENT       | Total number of  app visits in the last 30 days                                                                                                                                                                                 |
|                     |                | APP_LAST_VISIT_DT                    | DATE       | 1        |                           | ENGAGEMENT       | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     | EMAIL          | EMAIL_OPENS_30_DAYS                  | INT        | 1        |                           | ENGAGEMENT       | Total number of email opens in the last 30 days                                                                                                                                                                                 |
|                     |                | EMAIL_CLICKS_30_DAYS                 | INT        | 1        |                           | ENGAGEMENT       | Total number of email clicks in the last 30 days                                                                                                                                                                                |
|                     |                | EMAIL_LAST_OPEN_DT                   | DATE       | 1        |                           | ENGAGEMENT       | DD-MM-YYYY                                                                                                                                                                                                                      |
|                     | CONTACT_CENTRE | CC_CALL_COUNT_30_DAYS                | INT        | 1        |                           | ENGAGEMENT       | Total number of calls to the contact centre in the last 30 days                                                                                                                                                                 |
|                     |                | CC_LAST_CALL_DT                      | DATE       | 1        |                           | ENGAGEMENT       | DD-MM-YYYY                                                                                                                                                                                                                      |
| INTELLIGENCE        | MODEL_SCORES   | MODEL_<MODEL_NAME>                   | DECIMAL    | 1        | X                         | -                | Raw model output scores. One field per model.                                                                                                                                                                                   |
|                     | DECILES        | DECILE_<PRODUCT_NAME>                | INT        | 1        |                           | ANALYTICS        | Product deciles. One field per product.                                                                                                                                                                                         |
|                     | SEGMENTATIONS  | SEGMENTATION_<SEGMENT_NAME>          | VARCHAR    | 1        |                           | ANALYTICS        | Customer segmentations. One field per segmentation                                                                                                                                                                              |
| NBA                 |                | NBA_VOLUME_<1>                       | VARCHAR    | 1        |                           | ANALYTICS        | Next best action(s)  to drive sales volume.                                                                                                                                                                                     |
|                     |                | NBA_VALUE_<1>                        | VARCHAR    | 1        |                           | ANALYTICS        | Next best action(s) to drive sales value                                                                                                                                                                                        |
| CAMPAIGNS           |                | EMAIL_<CAMPAIGN_NAME>                | INT        | 1        |                           | CAMPAIGNS        | Use these values: 1 = included in campaign  0 = excluded from email campaign.  One field per campaign name e.g email_christmas2020                                                                                              |
|                     |                | SMS_<CAMAPAIGN_NAME>                 | INT        | 1        |                           | CAMPAIGNS        | Use these values: 1 = included in campaign  0 = excluded from email campaign.                                                                                                                                                   |
|                     |                | DM_<CAMPAIGN_NAME>                   | INT        | 1        |                           | CAMPAIGNS        | Use these values: 1 = included in campaign  0 = excluded from email campaign.                                                                                                                                                   |
|                     |                | OTHER_<CAMPAIGN_NAME>                | INT        | 1        |                           | CAMPAIGNS        | Use these values: 1 = included in campaign  0 = excluded from email campaign.                                                                                                                                                   |
| CUSTOM              |                | CUSTOM_<FIELD_NAME>                  | VARCHAR    | 1        |                           | CUSTOM           | Custom fields (prefix with CUSTOM_)                                                                                                                                                                                             |

