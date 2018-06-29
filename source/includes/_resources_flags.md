# Flags
Flags are created automatically in response to various events occurring in the system. In order to register as a listener to a certain flag, users should create [flag policies](#flag-policies). To find what flags exists, please read the [flag types](/#flag-types)> section of this documentation.


> Example fetch payload (for GET v2/flags)

```json
{
  "data": [{
    "id": 1337,
    "type": "flags",
    "attributes": {
      "flag_type": "LOW_BATTERY",
      "severity": 1,
      "description": "A descriptive message that can be passed to users if wanted",
      "created_at": "2018-06-29"
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

## Attributes

Name        | Format/Type  | Description
---------   | ------------ | -----------
id          | Integer      | ID of the flag policy
description | String/Text  | Description of what has happened.
flag_type   | String       | See [Flag Types](/#flag-types)

## Relationships
Name          | Relation    | Comments
------------  | ---------   | -----------
prescription  | belongs_to  |
flagable      | belongs_to  | The object that was flagged, i.e, the device with low battery, the dose that was taken early, etc.
flag_policies | has_many    | All policies of matching type belonging to the same prescription

## Filters
Name        | Type
----------  | ----------
flag_type   | Equal to
severity    | Equal to
description | Equal to
created_at  | Equal to

## Available resources
* get/
* get/:id
