# Mia Modules
The following resources explains basic interaction with MIA Modules.

## Attributes

> Example fetch payload (for GET v2/mia_modules)

```json
{
  "data": [{
    "id": 1337,
    "type": "mia_modules",
    "attributes": {
      "name": "GAA001",
      "is_connected_to_package": true
    }
  }],
  "jsonapi": {
    "version": "1.0"
  },
  "meta": {
    "API": {
      "version": "2.0.0"
    }
  }
}
```

Name                    | Format/Type  | Description
---------               | ------------ | -----------
id                      | Integer      | ID of the mia module
nane                    | String/Text  | Name of the mia module
is_connected_to_package | Boolean      | If the device is currently connected to a package

    has_one :prescription
    has_one :api_user
    has_many :packages
    has_many :taken_pods
    has_many :mia_module_schedules

## Relationships
Name                 | Relation    | Comments
------------         | ---------   | -----------
prescription         | belongs_to  |
api_user             | belongs_to  | Owner of the device
packages             | has_many    | All packages that has ever been connected to the device
taken_pods           | has_many    | All pods taken with the device connected
mia_module_schedules | has_many    | All active/future schedules

## Filters
Name                    | Type               | Description
----------              | ---------          | -------------
is_connected_to_package | Equal to           |
name                    | Equal to           |
module_number           | Equal to           |
battery_percentage      | Equal to           |
Available               | Equal to (Boolean) | True if device is not connected to an active prescription

## Available resources
* get/
* get/:id
