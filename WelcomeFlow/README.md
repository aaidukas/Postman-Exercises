## Exercise 1 (Welcome Flow)
This exercise is designed to get familiar with Welcome Flow setup. 

### Step 1 - Creating Email Trigger Task on SAS 360
* Create any email content
* Specify trigger (Orchestration -> Trigger). 
  * Select External event - "**WelcomeFlow**". 
  * Select Event attribute - "**emailEventName**" and specify your unique email name / id value. 
* Specify Header details: 
  * Email Subject - select "**emailSubject**" from "**Trigger Event**" folder
  * To - select "**Customer Email Address**" - **%%email_contact%%** OR as alternative "**emailAddress**" from "**Trigger Event**" folder
  * From / Reply-to - specify valid email address.
* Personalize email content - select relevant merged tags from "**Trigger Event**" folder
* Save, publish and activate newly created email task. 

### Step 2 - Connect to CIDB database and query Welcome flow table
* Connect to cidb database
* Select TOP 1000 rows from **[DMT_360].[dbo].[WelcomeFlow]**
  
### Step 3 - POST data to Welcome Flow API
* Find and try-out API via Swagger: <API URL>/swagger/index.html
* Add API definion via Postman and POST your data. Attribute "**emailEventName**" should match trigger name defined on SAS 360 Trigger Email Task. 
  * API URL: <API URL>/mct/api/CI360Event/welcomeflow
  * Body:
```json
{
  "customerNumber": "string",
  "emailAddress": "string",
  "emailEventName": "string",
  "emailSubject": "string",
  "customerName": "string",
  "advisorName": "string"
}
```
* Find "WelcomFlow" Event on SAS 360 and compare it's attributes with JSON body.
* Check data on **[DMT_360].[dbo].[WelcomeFlow]** after POST'ing requests to API.
* Validate that you have received email on "**emailAddress**" (part of the JSON body). 
* Validate that new subject id is created via Diagnostics page. 
