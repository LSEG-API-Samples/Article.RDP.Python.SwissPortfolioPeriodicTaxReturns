# Getting Swiss Portfolio periodic tax returns using RDP Libraries

## <a id="Introduction"></a>Introduction

A Swiss Portfolio Manager is required to make periodic tax returns to the Swiss Federal Tax Authority. In order to calculate the appropriate taxation rates on these tax returns, the portfolio manager needs some key attributes alongside the basic instrument reference data that they already have.
In this article, we're going to retrieve the Swiss Tax Data attributes provided by Refinitiv, for each instrument of a mixed-asset portfolio (bonds, equities, and funds) of 2,000 instruments
  -  Instrument ID
  -  Issuer Domicile Text
  -  Swiss Stamp Duty Flag
  -  Swiss Stamp Tax Rate
  -  Taxation Comment
  -  Taxation Type

We're using Refinitiv Data Platform Libraries (RDP Libraries) to retrieve the data from these RDP APIs
  -  [Symbology API](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-platform-apis/documentation#symbology-user-guide): To convert the identifiers supplied in the instrument list into PermIDs
  -  Data Store GraphQL API: To request Swiss Tax Data for the instruments requested

To find how to form an API call, search for an endpoint in [RDP API Playground](https://apidocs.refinitiv.com/Apps/ApiDocs) then check Playground tab and Reference tab

## <a id="Prerequisite"></a>Prerequisite
The code can be run on Jupyter Notebook that has Refinitiv Data Platform (RDP) Python library installed and ready to be used. To run examples in this article,
-  Access Credentials are required to use RDP libraries. For more detail, please check this page RDP libraries - Access Credentials. In this article, the authentication is being done using Platform session that allows you to access content directly within the cloud utilizes the OAuth 2.0 specification to ensure secure communication.  While the libraries will shield the user from OAuth token management, the following credentials will be required to access content using the Platform Session:
   - **User ID / Machine ID**	A User ID or Machine ID provided to you.
   - **Password**	The User / Machine Password provided to you.
   - **App Key**	An Application Key used to monitor the application. Users can generate/manage their application ID's here.

To acquire your Platform credentials, you will need to reach out to your Refinitiv Account Manager.

### Required python libraries and their version:
Python version 3.9.6 is being used here
You may download requirements.txt from this repo then use the command `pip install -r requirements.txt` to install required libraries
-  refinitiv.dataplatform==1.0.0a10
-  pandas==1.3.5
-  logging==0.5.1.2
-  asyncio==3.4.3
-  json==2.0.9
-  datetime==4.3

## <a id="InputFiles"></a>Input files
1. credentials.ini: Credentials file that contains RDP credentials
2. Portfolio.csv CSV file containing the instrument types (Isin, Wpk, ValorenNumber, Sedol) and instrument codes
![swiss-tax-input-csv](https://user-images.githubusercontent.com/89068039/158467611-13dc1aab-092f-4fdb-bf53-a5448181e0f7.png)

## <a id="ExampleOutput"></a>Example output
 - Here's the output dataframe of Swiss Tax Data
![swiss-tax-output-df](https://user-images.githubusercontent.com/89068039/158467529-488eee58-fb09-4dd5-ba1e-67d0aea3ddf2.PNG)
 - Output CSV files are saved with date and timestamp of the run in swiss_tax_result folder
![swiss-tax-output-folder](https://user-images.githubusercontent.com/89068039/158467562-cf5db149-199e-44d0-85ff-20b147961a64.PNG)
![swiss-tax-output-csv](https://user-images.githubusercontent.com/89068039/158467587-2651ff78-37fd-427d-8160-90e1b3be671c.PNG)

## <a id="Conclusion"></a>Conclusion
From this code, we can retrieve Swiss Tax data from the input instruments provided in a CSV file using RDP Libraries.

## <a id="References"></a>References
•  [Refinitiv Data Platform Libraries - quickstart](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-platform-libraries/quick-start)
•  [Refinitiv Data Platform APIs - Symbology User Guide](https://developers.refinitiv.com/en/api-catalog/refinitiv-data-platform/refinitiv-data-platform-apis/documentation#symbology-user-guide)
•  [Refinitiv Data Platform APIs Playground](https://apidocs.refinitiv.com/Apps/ApiDocs)
•  [Swiss Tax Data | Refinitiv](https://www.refinitiv.com/en/market-data/regulatory-services/swiss-tax)
