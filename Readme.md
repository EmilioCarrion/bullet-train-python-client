<img width="100%" src="https://raw.githubusercontent.com/SolidStateGroup/bullet-train-frontend/master/hero.png"/>

# Bullet Train Client

The SDK clients for Python [https://bullet-train.io/](https://www.bullet-train.io/). Bullet Train allows you to manage feature flags and remote config across multiple projects, environments and organisations.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See running in production for notes on how to deploy the project on a live system.

## Installing

### VIA pip

```
pip install bullet-train
```
	
## Usage
**Retrieving feature flags for your project**

**For full documentation visit [https://docs.bullet-train.io](https://docs.bullet-train.io)**

```
from bullet_train import BulletTrain;

bt = BulletTrain(environment_id="<YOUR_ENVIRONMENT_KEY>")

if bt.has_feature("header", '<My User Id>'):
  if bt.feature_enabled("header"):
    # Show my awesome cool new feature to the world
 
if bt.has_feature("header"):
  if bt.feature_enabled("header"):
    # Show my awesome cool new feature to the world

value = bt.get_value("header", '<My User Id>')

value = bt.get_value("header")

bt.set_trait("accept-cookies", "true", "ben@bullet-train.io"))
bt.get_trait("accept-cookies", "ben@bullet-train.io"))
```

**Available Options**

| Property        | Description           | Required  | Default Value  |
| ----- |:-------------| -----:| -----:|
| ```environment_id```     | Defines which project environment you wish to get flags for. *example ACME Project - Staging.* | **YES** | None
| ```api```     | Use this property to define where you're getting feature flags from, e.g. if you're self hosting. |  **NO** | https://api.bullet-train.io/api/

**Available Functions**

| Function        | Description |         
| ------------- |:-------------:|
| ```has_feature(key)```     | Get the value of a particular feature e.g. ```bt.has_feature("powerUserFeature") // true```
| ```has_feature(key, user_id)```     | Get the value of a particular feature for a user e.g. ```bt.has_feature("powerUserFeature", 1234) // true```
| ```get_value(key)```     | Get the value of a particular feature e.g. ```bt.get_value("font_size") // 10```
| ```get_value(key, userId)```     | Get the value of a particular feature for a specified user e.g. ```bt.get_value("font_size", 1234) // 15```
| ```get_flags()```     | Trigger a manual fetch of the environment features, returns a list of flag objects, see below for returned data
| ```get_flags_for_user(1234)```     | Trigger a manual fetch of the environment features with a given user id, returns a list of flag objects, see below for returned data


**Identifying users**

Identifying users allows you to target specific users from the [Bullet Train dashboard](https://www.bullet-train.io/).
You can include an optional user identifier as part of the `has_feature` and `get_value` methods to retrieve unique user flags and variables.

**Flags data structure**

| Field | Description | Type |
| ---- | ------------ | ---- |
| id | Internal id of feature state | Integer |
| enabled | Whether feature is enabled or not | Boolean |
| environment | Internal ID of environment | Integer | 
| feature_state_value | Value of the feature | Any - determined based on data input on [bullet-train.io](https://bullet-train.io). |
| feature | Feature object - see below for details | Object |


**Feature data structure**

| Field | Description | Type |
| ---- | --------------- | --- |
| id | Internal id of feature | Integer |
| name | Name of the feature (sometimes referred to as key or ID) | String |
| description | Description of the feature | String |
| type | Feature Type. Can be FLAG or CONFIG | String |
| created_date | Date feature was created | Datetime |
| inital_value | The initial / default value set for all feature states on creation | String |
| project | Internal ID of the associated project | Integer |  


## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/kyle-ssg/c36a03aebe492e45cbd3eefb21cb0486) for details on our code of conduct, and the process for submitting pull requests to us.

## Getting Help

If you encounter a bug or feature request we would like to hear about it. Before you submit an issue please search existing issues in order to prevent duplicates. 

## Get in touch

If you have any questions about our projects you can email <a href="mailto:projects@solidstategroup.com">projects@solidstategroup.com</a>.

## Useful links

[Website](https://bullet-train.io)

[Documentation](https://docs.bullet-train.io/)

[Code Examples](https://github.com/SolidStateGroup/bullet-train-docs)

[Youtube Tutorials](https://www.youtube.com/channel/UCki7GZrOdZZcsV9rAIRchCw)
