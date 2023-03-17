#Challenge 3 - Retrieve and Deploy Completed Work
## Learning Objectives

* Retrieving completed work from a scratch org
* Deploying completed work into another org

**Time to Complete** : 30 Mins

## Steps

### Create a New Feature Branch for this challenge

```
git checkout -b <new-branch>
```

* https://github.com/trailheadapps/dreamhouse-lwc

_Hint: Instructions on how to create a new branch are available at the below:_
* [Git Checkout](https://www.atlassian.com/git/tutorials/using-branches/git-checkout)


### Make the following changes in your scratch org

* Set **Compliance Categorization** as **PII** to all fields in **Property\_\_c** object
  * Open Scratch org
  * Setup --> Object Manager --> Search **Property** in Object finder--> Fields & Relationships --> Address --> Edit --> set Compliance Categorization as PII
  * Follow this step in **ALL** the fields in **Property** object
*   Create a field in property object and add it to layout

    * Setup --> Object Manager --> Search **Property** in Object finder--> Fields & Relationships --> New --> with below details

    | Field             | Value                                                                                                                                                                                                   |
    | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Data type         | Picklist (Multi-Select)                                                                                                                                                                                 |
    | Label             | Features                                                                                                                                                                                                |
    | Values            | <p>Air conditioning</p><p>Carport/Garage</p><p>Garden/Backyard</p><p>Solar panels</p><p>Deck/Pergola Dishwasher</p><p>Swimming pool</p><p>Built-in barbecue</p><p>Water feature</p><p>Garden gnomes</p> |
    | Restrict picklist | ✔️                                                                                                                                                                                                      |
    | Visible Lines     | 4                                                                                                                                                                                                       |

    * Edit property layout and add features field to information section under tags field
    * Edit dreamhouse permissionset and add feature field with edit access
* Add **daysOnMarket** component to property explorer
  * Open Dreamhouse app in App launcher
  * Open Property Explorer tab
  * Click Setup gear Icon --> Edit page --> search **daysOnMarket** in component finder --> add the component to right side panel
  * Save the changes and click back
* Create a new Apex class
  * Open Developer Console
  *   File --> New --> Apex class --> ContactController --> ok --> use below code and save the class

      ```
      public class ContactController {
          @AuraEnabled
          public static List<contact> getContacts(string searchKey){
              string key = '%'+ searchKey +'%' ;
              return [SELECT Id,Name FROM Contact WHERE Name LIKE :key ORDER BY Name LIMIT 50];
          }

      }
      ```

### Retrieve all the changes from the org


* Utlize [sfdx force:source:retrieve](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_mdapi.htm#cli\_reference\_retrieve) (The reference to documentation is attached or use the -h flag to understand usage) to deploy this code base to the org.
* Once retrieved, ensure you copy the metadata to the right segments in your repo

```
sfdx force:source:retrieve -m MetadataName -u <scratchOrgName>
```

### Redeploy your changes to the your dev org

* Utlize [sfdx force:source:deploy](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_mdapi.htm#cli\_reference\_deploy) in your terminal (The reference to documentation is attached or use the -h flag to understand usage) to deploy this code base to the org.

```
sfdx force:source:deploy -u <devOrg> -p force-app -w 30
```
Once the metadata is successfully deployed your work into your , commit and push your changes to your dreamouse-lwc repo.

## Challenge Complete!
