# Flag Policies
A flag policy is used to monitor a specific type of [Event](/#flag-types) in the system. All such events generates a [Flag](#flags), if the type of the flag matches the value of flag_type in a flag policy, all recipients will be notified.

> Example fetch payload (for GET v2/flag_policies)

```json
{
  "data": [{
    "id": 1337,
    "type": "flag_policies",
    "attributes": {
      "message": "Your message goes here",
      "flag_type": "LOW_BATTERY"
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

> Example post payload (POST v2/flag_policies)

```json
{
  "data": {
    "type": "flag_policies",
    "attributes": {
      "message": "Your message goes here",
      "flag_type": "LOW_BATTERY"
    },
    "relationships": {
      "prescription": {
        "data": { "type": "prescriptions", "id": "1" }
      }
    }
  },
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

Name      | Format/Type  | Description
--------- | ------------ | -----------
id        | Integer      | ID of the flag policy
message   | String/Text  | Message sent to recipients when flag of matching flag_type occurs. If not specified, a default message will be sent.
flag_type | String       | Type of flag to listen for. See [Flag Types](/#flag-types)

## Relationships
Name         | Relation    | Comments
------------ | ---------   | -----------
prescription | belongs_to  |
recipients   | has_many    | Recipients to notify when a flag of flag_type occurs
flags        | has_many    | All flags of flag_type belonging to prescription

## Filters
Name       | Type
---------- | ----------
message    | Equal to
flag_type  | Equal to

## Available resources
* get/
* get/:id
* post/
* put/:id
* delete/:id