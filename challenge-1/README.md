#Challenge 1 - Fork and Git Clone + Dev Org Setup

## Learning Objectives

* Get comfortable with CLI tools
* Cloning a git repo into your local machine
* Deploy a sfdx repo using a sfdx source command into a Salesforce Org

**Time to Complete** : 15 Mins

## Steps

### Setup

1. Fork the Dreamhouse-lwc repo to your Github Account

* https://github.com/trailheadapps/dreamhouse-lwc

_Hint: Instructions on how to fork a repo are available at the below:_
* [fork-a-repo](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo)

1. Clone the forked repo from your GitHub account to a local repo
2. Open up the project in **VS Code**
3. Authenticate your SFDX CLI in the terminal to a previously created dev org

### Deploy the repo to the authenticated org

* Use [sfdx force:source:deploy](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference_force_source.htm#cli_reference_force_source_deploy) in your terminal (use the -h flag to understand usage) to deploy this code base to the org

```
sfdx force:source:deploy -u YOUR_AUTHENTICATED_ORG -p TARGET_FOLDER
```

* Assign the dreamhouse permission set to the default user using [sfdx force:user:permset:assign](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_user.htm#cli\_reference\_permset\_assign)

```
sfdx force:user:permset:assign -u YOUR_AUTHENTICATED_ORG -n dreamhouse
```

* Import the data using [sfdx force:data:tree:import](https://developer.salesforce.com/docs/atlas.en-us.sfdx\_cli\_reference.meta/sfdx\_cli\_reference/cli\_reference\_force\_data.htm#cli\_reference\_tree\_import)

```
sfdx force:data:tree:import -p ./data/sample-data-plan.json -u YOUR_AUTHICATED_ORG
```

## Challenge Complete you have successfully setup your own developer workspace!
