# Postman Exercises
Repository is used for various exercises with Postman

## Exercise 1 (Welcome Flow)
This exercise is designed to get familiar with Welcome Flow setup. 

### Step 1 - Creating Email Trigger Task on SAS 360
* Crete any email content
* Specify trigger (Orchestration -> Trigger). 
  * Select External event - "Welcome Flow". 
  * Select Event attribute - "emailEventName" and specify your unique email name / id value. 
* Specify Header details: 
  * Email Subject - select "emailSubject" from "Trigger Event" folder
  * To - select "emailAddress" from "Trigger Event" folder
  * From / Reply-to - specify valid email address.
* Personalize email content - select relevant merged tags from "Trigger Event" folder
* Save, publish and activate newly created email task. 

### Step 2 - Connect to CIDB database and query Welcome flow table
* Connect to mct-cidb-test database
* Select TOP 1000 rows from [DMT_360].[dbo].[WelcomeFlow]
  
### Step 3 - POST data to Welcome Flow API
* Find and try-out API via Swagger: https://mct-test-resp.danskenet.net/swagger/index.html
* Add API definion via Postman and POST your data. Attribute "**emailEventName**" should match trigger name defined on SAS 360 Trigger Email Task. 
  * API URL: https://mct-test-resp.danskenet.net/mct/api/CI360Event/welcomeflow
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
*  Check data on [DMT_360].[dbo].[WelcomeFlow] after POST'ing requests to API.
*  Validate that you have received email on "**emailAddress**" (part of the JSON body). 
