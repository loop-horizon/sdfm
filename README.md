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
| Category            | Sub-Category   | Field                                | DataType   | Description/Format                                                                                                                                                                                                                                              |
|---------------------|----------------|--------------------------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IDENTITY            | CRM            | CUSTOMER_ID(PK)                      | VARCHAR    | Primary key for the table - internal customer id                                                                                                                                                                                                                |
|                     |                | EMAIL_ADDRESS_<1>                    | VARCHAR    | Full email address including prefix and domain. If more than 1 email address per customer_id then add new field with the following format email_address_2, email_address_3 etc. Trim leading and trailing white space, and convert all characters to lowercase. |
|                     |                | FIRST_NAME                           | VARCHAR    | Use a-z only. Lowercase only, no punctuation. Special characters in UTF-8 format.                                                                                                                                                                               |
|                     |                | LAST_NAME                            | VARCHAR    | Use a-z only. Lowercase only, no punctuation. Special characters in UTF-8 format.                                                                                                                                                                               |
|                     |                | FB_TEL_NUMBER_<1>                    | VARCHAR    | Remove symbols, letters, and any leading zeroes. You should prefix the country code. (E.g 447851434341). If more than 1 tel_number per customer_id then add new field with the following format tel_number_2, tel_number_3 etc.                                 |
|                     |                | GA_TEL_NUMBER_<1>                    | VARCHAR    | Convert each phone number to E164 format (e.g. +447851135341)                                                                                                                                                                                                   |
|                     |                | GENDER                               | VARCHAR(1) | Use these values: m for male, f for female.                                                                                                                                                                                                                     |
|                     |                | DOB                                  | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     |                | DOBY                                 | VARCHAR    | YYYY                                                                                                                                                                                                                                                            |
|                     |                | DOBM                                 | VARCHAR    | MM                                                                                                                                                                                                                                                              |
|                     |                | DOBD                                 | VARCHAR    | DD                                                                                                                                                                                                                                                              |
|                     |                | AGE                                  | INT        | Age derived from DOB field                                                                                                                                                                                                                                      |
|                     |                | ZIP_CODE                             | VARCHAR    | Use lowercase, and no white space. For the US, use only the first 5 digits. For the UK, use the Area/District/Sector format.                                                                                                                                    |
|                     |                |                                      |            |                                                                                                                                                                                                                                                                 |
|                     |                | CITY                                 | VARCHAR    | Use a-z only. Lowercase only, with no punctuation, no special characters, and no white space.                                                                                                                                                                   |
|                     |                | STATE                                | VARCHAR    | Use the 2-character ANSI abbreviation code, lowercase. Normalize states outside the US in lowercase, with no punctuation, no special characters, and no white space.                                                                                            |
|                     |                | COUNTRY                              | VARCHAR    | Use lowercase, 2-letter country codes in ISO 3166-1 alpha-2.                                                                                                                                                                                                    |
|                     | PLATFORMS      | ECID                                 | VARCHAR    | (Most recent) Adobe Experience Cloud ID                                                                                                                                                                                                                         |
|                     |                | MOBILE_ADVERTISER_ID                 | VARCHAR    | (Most recent) Use all lowercase, and keep hyphens. Mobile device ID (advertising ID/IDFA).                                                                                                                                                                      |
|                     |                | FBP                                  | VARCHAR    | (Most recent) Facebook Cookie ID                                                                                                                                                                                                                                |
|                     |                | FBC                                  | VARCHAR    | (Most recent) Facebook Click ID                                                                                                                                                                                                                                 |
|                     |                | FB_EXTERNAL_ID                       | VARCHAR    | External_id used in advanced customer matching for Facebook Pixel                                                                                                                                                                                               |
|                     |                | USERID                               | VARCHAR    | (Most recent)Google Ads - Advertiser generated and assigned user ID. Accessible to whitelisted Google clients only.                                                                                                                                             |
|                     |                | GCLID                                | VARCHAR    | (Most recent) Google Ads Click ID                                                                                                                                                                                                                               |
|                     | CONSENT        | GLOBAL_MARKETING_CONSENT_OPT_IN      | INT        | Use these values: 1 for consent 0 for no consent                                                                                                                                                                                                                |
|                     |                | EMAIL_CONSENT                        | INT        | Use these values: 1 for consent 0 for no consent                                                                                                                                                                                                                |
|                     |                | TEL_CONSENT                          | INT        | Use these values: 1 for consent 0 for no consent                                                                                                                                                                                                                |
|                     |                | SMS_CONSENT                          | INT        | Use these values: 1 for consent 0 for no consent                                                                                                                                                                                                                |
|                     |                | DM_CONSENT                           | INT        | Use these values: 1 for consent 0 for no consent                                                                                                                                                                                                                |
| CUSTOMER            |                | CUSTOMER_STATUS                      | VARCHAR    | The status of the customer. Example: 'Active', 'Prospect', 'Lapsed'                                                                                                                                                                                             |
|                     |                | CUSTOMER_START_DT                    | DATE       | DD-MM-YYYY - Date the customer/prospect was acquired                                                                                                                                                                                                            |
|                     |                | CUSTOMER_END_DT                      | DATE       | DD-MM-YYYY - Date customer/prospect went from Active to Inactive                                                                                                                                                                                                |
|                     |                | CUSTOMER_TENURE_DAYS                 | INT        | Number of days as a customer                                                                                                                                                                                                                                    |
|                     |                | CUSTOMER_ACQUISITION_CHAN            | VARCHAR    | Last touch channel (E.g. Google PPC)                                                                                                                                                                                                                            |
| PRODUCT HOLDING     | CURRENT        | <PRODUCT_NAME>                       | VARCHAR    | Product holding. One field per product holding. For example: Motor_Insurance, Travel_Insurance                                                                                                                                                                  |
|                     |                | <PRODUCT_NAME>_STATUS                | VARCHAR    | Status of the product e.g. 'Active' , 'Lapsed'.                                                                                                                                                                                                                 |
|                     |                | <PRODUCT_NAME>_START_DT              | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_END_DT                | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_ACQUISITION_CHAN      | VARCHAR    | Last touch channel (E.g. Google PPC)                                                                                                                                                                                                                            |
|                     | HISTORY        | <PRODUCT_NAME>_HIST                  | VARCHAR    | Previous product holding (last product status change)                                                                                                                                                                                                           |
|                     |                | <PRODUCT_NAME>_HIST_STATUS           | VARCHAR    | Previous product holding status                                                                                                                                                                                                                                 |
|                     |                | <PRODUCT_NAME>_HIST_START_DT         | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_HIST_END_DT_HIST      | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     |                | <PRODUCT_NAME>_HIST_ACQUISITION_CHAN | VARCHAR    | Last touch channel of previous product holding (E.g. Google PPC)                                                                                                                                                                                                |
| PLATFORM ENGAGEMENT | WEB            | WEB_VISIT_COUNT_30_DAYS              | INT        | Totla number of web visits in the last 30 days.                                                                                                                                                                                                                 |
|                     |                | WEB_LAST_VISIT_DT                    | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     | APP            | APP_VISIT_COUNT_30_DAYS              | INT        | Total number of app visits in the last 30 days                                                                                                                                                                                                                  |
|                     |                | APP_LAST_VISIT_DT                    | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     | EMAIL          | EMAIL_OPENS_30_DAYS                  | INT        | Total number of email opens in the last 30 days                                                                                                                                                                                                                 |
|                     |                | EMAIL_CLICKS_30_DAYS                 | INT        | Total number of email clicks in the last 30 days                                                                                                                                                                                                                |
|                     |                | EMAIL_LAST_OPEN_DT                   | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
|                     | CONTACT_CENTRE | CC_CALL_COUNT_30_DAYS                | INT        | Total number of calls to the contact centre in the last 30 days                                                                                                                                                                                                 |
|                     |                | CC_LAST_CALL_DT                      | DATE       | DD-MM-YYYY                                                                                                                                                                                                                                                      |
| INTELLIGENCE        | MODEL_SCORES   | MODEL_<MODEL_NAME>                   | DECIMAL    | Raw model output scores. One field per model.                                                                                                                                                                                                                   |
|                     | DECILES        | DECILE_<PRODUCT_NAME>                | INT        | Product deciles. One field per product.                                                                                                                                                                                                                         |
|                     | SEGMENTATIONS  | SEGMENTATION_<SEGMENT_NAME>          | VARCHAR    | Customer segmentations. One field per segmentation                                                                                                                                                                                                              |
| NBA                 |                | NBA_VOLUME_<1>                       | VARCHAR    | Next best action(s) to drive sales volume.                                                                                                                                                                                                                      |
|                     |                | NBA_VALUE_<1>                        | VARCHAR    | Next best action(s) to drive sales value                                                                                                                                                                                                                        |
| CAMPAIGNS           |                | EMAIL_<CAMPAIGN_NAME>                | INT        | Use these values: 1 = included in campaign 0 = excluded from email campaign. One field per campaign name e.g email_christmas2020                                                                                                                                |
|                     |                | SMS_<CAMAPAIGN_NAME>                 | INT        | Use these values: 1 = included in campaign 0 = excluded from email campaign.                                                                                                                                                                                    |
|                     |                | DM_<CAMPAIGN_NAME>                   | INT        | Use these values: 1 = included in campaign 0 = excluded from email campaign.                                                                                                                                                                                    |
|                     |                | OTHER_<CAMPAIGN_NAME>                | INT        | Use these values: 1 = included in campaign 0 = excluded from email campaign.                                                                                                                                                                                    |
| CUSTOM              |                | CUSTOM_<FIELD_NAME>                  | VARCHAR    | Custom fields (prefix with CUSTOM_)                                                                                                                                                                                                                             |
