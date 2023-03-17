#Challenge 2 - Setup Scratch Org for Development

## Learning Objectives

* Get comfortable with CLI tools
* Create a Scratch Org environment for development
* Deploy a sfdx repo using a sfdx source command into a Scratch Org

**Time to Complete** : 10 Mins

## Steps

### Create a Scratch Org utilising your created Developer Org

* Paste the following into your project-scratch-def.json file:
```
{
    "orgName": "dreamhouse",
    "edition": "Developer",
    "features": ["Communities", "ServiceCloud"],
    "settings": {
        "communitiesSettings": {
            "enableNetworksEnabled": true
        },
        "mobileSettings": {
            "enableS1EncryptedStoragePref2": true
        },
        "omniChannelSettings": {
            "enableOmniChannel": true
        },
        "caseSettings": {
            "systemUserEmail": "support@acme.com"
        }
    }
}
```

* Use [sfdx force:org:create](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_force_org.htm#cli_reference_force_org_create) in your terminal (use the -h flag to understand usage) to create a new scratch org

```
sfdx force:org:create -s -f config/project-scratch-def.json -a dreamhouse-org -v devHubUserName
```
_Tip: Learn more about the scratch org configuration files here:_ 
* https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs_def_file.htm

### Deploy the repo to the scratch org

* Use [sfdx force:source:push](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_force_source.htm#cli_reference_force_source_push) in your terminal (use the -h flag to understand usage) to deploy all code to the scratch org

```
sfdx force:source:push -u YOUR_AUTHENTICATED_ORG
```

* Assign the dreamhouse permission set to the default user using [sfdx force:user:permset:assign](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_user.htm#cli\_reference\_permset\_assign)

```
sfdx force:user:permset:assign -u YOUR_AUTHENTICATED_ORG -n dreamhouse
```

* Import the data using [sfdx force:data:tree:import](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_data.htm#cli\_reference\_tree\_import)

```
sfdx force:data:tree:import -p ./data/sample-data-plan.json -u YOUR_AUTHICATED_ORG
```

## Challenge Complete you have successfully setup your scratch org workspace!
