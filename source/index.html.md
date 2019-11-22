---
title: Mevia REST API

language_tabs:
  - json: JSON

toc_footers:
  - <a href='http://www.mevia.se'>Mevia</a>

includes:
  - flag_types
  - triggers
  - releases

search: true
---
# Overview

The API aims to take care of all data related to the MIA module itself, which is sending and receiving information from modules. Developers that use the API can, for instance, obtain all events from a module for a given patient, or register a prescription for a patient which then automatically will set reminders and other logic that interacts with the patient's mobile phone. This page contains general information about the API, what models are available and what the latest changes are. Documentation about all available resources can be found at [the resource page](resources.html)

The purpose of this setup is that API users will be able to concentrate on their business logic, henceforth not on how the modules work, which is abstracted away through the API. A benefit of this is also that, if the physical module changes, then there will be no impact on API users due to this abstraction.

We follow [JSON API 1.0](http://jsonapi.org). Details about sorting, filtering, resource inclusion and so on will be easiest to find at their site.

The api is available under <span class="red-text">https://api.mevia.se</span>. Current version is scoped under V2.

## Authentication and security

All API calls are done via HTTPS requests, which means that all data obtained and retrieved from the API is delivered through an encrypted connection. Moreover, JSON Web Tokens("jwt") are used for authorization, and a jwt must be included with each request in order to authorize with the API. The token is used to idenfify which user that is connecting to the API and is initially handed out manually by Mevia.

In order to authorize with the API, the jwt must be sent with each request as a request parameter in the request header.

The jwt should be specified in the header of every request, in the following fashion:

<span class="red-text">Authorization: Bearer *your_jwt*</span>

# Resources

## Flag Policies
A flag policy is used to monitor a specific type of [Event](#flag-types) in the system. All such events generates a [Flag](#flags), if the type of the flag matches the value of flag_type in a flag policy, all recipients will be notified.

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
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

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
  }
}
```

Name      | Format/Type  | Description
--------- | ------------ | -----------
id        | Integer      | ID of the flag policy
message   | String/Text  | Message sent to recipients when flag of matching flag_type occurs. If not specified, a default message will be sent.
flag_type | String       | Type of flag to listen for. See [Flag Types](#flag-types)

### Relationships
Name         | Relation    | Comments
------------ | ---------   | -----------
prescription | belongs_to  |
recipients   | has_many    | Recipients to notify when a flag of flag_type occurs
flags        | has_many    | All flags of flag_type belonging to prescription

### Filters
Name       | Type
---------- | ----------
message    | Equal to
flag_type  | Equal to

### Available resources
* get/
* get/:id
* post/
* put/:id
* delete/:id

## Flags
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
  "meta": {
    "record_count": 1
  },
}
```

### Attributes

Name        | Format/Type  | Description
---------   | ------------ | -----------
id          | Integer      | ID of the flag policy
description | String/Text  | Description of what has happened.
flag_type   | String       | See [Flag Types](/#flag-types)

### Relationships
Name          | Relation    | Comments
------------  | ---------   | -----------
prescription  | belongs_to  |
flagable      | belongs_to  | The object that was flagged, i.e, the device with low battery, the dose that was taken early, etc.
flag_policies | has_many    | All policies of matching type belonging to the same prescription

### Filters
Name        | Type
----------  | ----------
flag_type   | Equal to
severity    | Equal to
description | Equal to
created_at  | Equal to

### Available resources
* get/
* get/:id

## Mia Modules
The following resources explains basic interaction with MIA Modules.

### Attributes


> Example fetch payload (for GET v2/mia_modules)

```json
{
  "data": [{
    "id": 1337,
    "type": "mia_modules",
    "attributes": {
      "name": "GAA001",
      "is_connected_to_package": true,
      "created_at": "2016-09-13T10:50:26.339Z",
      "updated_at": "2019-04-27T01:59:01.629Z",
      "battery_percentage": 100
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

Name                    | Format/Type  | Description
---------               | ------------ | -----------
id                      | Integer      | ID of the mia module
name                    | String/Text  | Name of the mia module
is_connected_to_package | Boolean      | If the device is currently connected to a package
battery_percentage      | Integer      | Battery status of the device (at last communication cycle)

### Relationships

> Example post request

```json
{
  "data": {
    "type": "mia_modules",
    "attributes": {
      "name": "GAA001",
      "is_connected_to_package": true
    }
  }
}
```

Name                 | Relation    | Comments
------------         | ---------   | -----------
prescription         | belongs_to  |
api_user             | belongs_to  | Owner of the device
packages             | has_many    | All packages that has ever been connected to the device
taken_pods           | has_many    | All pods taken with the device connected
mia_module_schedules | has_many    | All active/future schedules

### Filters
Name                    | Type               | Description
----------              | ---------          | -------------
is_connected_to_package | Equal to           |
name                    | Equal to           |
module_number           | Equal to           |
battery_percentage      | Equal to           |
Available               | Equal to (Boolean) | True if device is not connected to an active prescription

### Available resources
* get/
* get/:id

## Notification Policies
A notification policy is a rule for how to send reminders to a list of recipients. Reminders are sent for every scheduled dose, as long as the dose is not marked as muted/taken when the reminder is supposed to be sent.

> Example fetch payload (for GET v2/notification_policies)

```json
{
  "data": [{
    "id": 1337,
    "type": "notification_policies",
    "attributes": {
      "message": "Your message goes here",
      "trigger": "BEFORE_DOSE_END",
      "offset": 15,
      "notification_type": "EMAIL",
      "dispatchable": true
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

> Example post payload (POST v2/flag_policies)

```json
{
  "data": {
    "type": "flag_policies",
    "attributes": {
      "message": "Your message goes here",
      "trigger": "BEFORE_DOSE_END",
      "offset": 15,
      "notification_type": "EMAIL"
    },
    "relationships": {
      "prescription": {
        "data": { "type": "prescriptions", "id": "1" }
      },
      "recipients": {
        "data": [{ "type": "recipients", "id": 1 }, { "type": "recipients", "id": 2 }]
      }
    }
  }
}
```

Name              | Format/Type  | Description
---------         | ------------ | -----------
id                | Integer      | ID of the notification policy
message           | String/Text  | Message sent to recipients at offset (attribute) from trigger (attribute) for every dose beloning to the same prescription.
notification_type | String       | How to dispatch the reminder. Currently, only SMS and EMAIL are supported.
trigger           | String       | When to dispatch the reminder. See [triggers](#notification-triggers)
offset            | Integer      | How long before/after trigger (attribute) to send reminder. A reminder with offset 5 and trigger BEFORE_DOSE_START will be dispatched 5 minutes before the dose begins, etc.
dispatchable      | Boolean      | Only fetchable. True if the policy is able to dispatch reminders - when there is at least one recipient connected to the policy with data enough to recieve the reminder. If notification_type is set to SMS, a phone is needed. If notification_type is set to EMAIL, an email adress is needed.

### Relationships
Name            | Relation    | Comments
--------------  | ---------   | -----------
prescription    | belongs_to  |
recipients      | has_many    | Recipients to notify when dose is not taken/muted at specified time
notifications   | has_many    | All notifications dispatched by the policy
scheduled_doses | has_many    | All doses for which the recipients will be notified (currently: all doses beloning to the same prescription)

### Filters
Name               | Type
-----------------  | ----------
trigger            | Equal to
message            | Equal to
offset             | Equal to
notification_type  | Equal to

### Available resources
* get/
* get/:id
* post/
* put/:id
* delete/:id

## Notifications
A notification is simply a reminder sent from the system, via a notification policy. One notification is created for every pair of dose schemas, recipients and doses.
* Warning: notifications will be drastically changed in the future. Be careful when using. *

> Example fetch payload (for GET v2/notifications)

```json
{
  "data": [{
    "id": 1337,
    "type": "notifications",
    "attributes": {
      "message": "Your message goes here",
      "sent_at": "2018-02-14T06:45:04.589Z",
      "phone": "0761133316",
      "email": null
    }
  }],
  "meta": {
    "record_count": 1
  },
}
```

### Attributes

Name              | Format/Type  | Description
---------         | ------------ | -----------
id                | Integer      | ID of the notification
message           | String/Text  | Message sent to recipient. Inherited from its notification policy
email             | String       | The email to which it was dispatched. A notification will have either a phone number or an email, never both
phone             | String       | The phone to which it was dispatched. A notification will have either a phone number or an email, never both
sent_at           | Timestamp    | Time at which the notification was sent. Null for notifications that have not been dispatched

### Relationships
None

### Filters
Name           | Type
----------     | ----------
id             | Equal to
message        | Equal to
email          | Equal to
phone          | Equal to
sent_at_after  | Equal to | Returns notifications have attribute sent_at higher than given timestamp
sent_at_before | Equal to | Returns notifications have attribute sent_at lower than given timestamp

### Available resources
* get/
* get/:id

## Packages
A package is automatically generated whenever a device detects that a new package has been inserted. Packages are read-only, and is mainly used to group taken_pods.

> Example fetch payload (for GET v2/packages)

```json
{
  "data": [{
    "id": 1337,
    "type": "packages",
    "attributes": {
      "created_at": "2018-02-14T06:45:04.589Z",
      "is_current": true,
      "number": 1,
      "nr_of_taken_pods": 14
    }
  }],
  "meta": {
    "record_count": 1
  },
}
```

### Attributes

Name              | Format/Type  | Description
---------         | ------------ | -----------
id                | Integer      | ID of the package
created_at        | Timestamp    | Timestamp of when the package was generated
is_current        | Boolean      | Indicates if the package is the latest generated from its device (i.e., it's currently inserted and in use)
number            | Integer      | Index of the package in the list of all packages generated by the device

### Relationships
Name            | Relation    | Comments
--------------  | ---------   | -----------
prescription    | belongs_to  |
recipients      | has_many    | Recipients to notify when dose is not taken/muted at specified time
notifications   | has_many    | All notifications dispatched by the policy
scheduled_doses | has_many    | All doses for which the recipients will be notified (currently: all doses beloning to the same prescription)

### Filters
Name             | Type
----------       | ----------
id               | Equal to
created_at       | Equal to
number           | Equal to
nr_of_taken_pods | Equal to

### Available resources
* get/
* get/:id

## Prescriptions
A prescription is easiest to think of as a patient. A prescription is the owner of dose schedules, reminder policies and recipients.

> Example fetch payload (for GET v2/prescriptions)

```json
{
  "data": [{
    "id": "105",
    "type": "prescriptions",
    "links": {
      "self": "http://api.mevia.se/v2/prescriptions/105"
    },
    "attributes": {
      "starts_at": "2017-11-06T00:00:00.000Z",
      "ends_at": "2018-08-31T21:59:00.000Z",
      "module_activity_starts_at": "2017-11-06T00:00:00.000Z",
      "module_activity_ends_at": "2018-08-31T21:59:00.000Z",
      "pod_sequence": "[0,1,2,3,4,5,6,7,8,9,10,11,12,13]",
      "patient_reference": "Bertil",
      "language": "sv"
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

> Example post payload (for POST v2/prescriptions)

```json
{
  "data": {
    "type": "prescriptions",
    "attributes": {
      "starts_at": "2017-11-06T00:00:00.000Z",
      "ends_at": "2018-08-31T21:59:00.000Z",
      "module_activity_starts_at": "2017-11-06T00:00:00.000Z",
      "module_activity_ends_at": "2018-08-31T21:59:00.000Z",
      "pod_sequence": "[0,1,2,3,4,5,6,7,8,9,10,11,12,13]",
      "patient_reference": "Bertil",
      "language": "sv"
    }
  }
}
```

Name                      | Format/Type  | Description
---------                 | ------------ | -----------
id                        | Integer      | ID of the prescription
starts_at                 | Timestamp    | Indicator of when the prescriptions turns active - doses and reminders starts to generate etc.
ends_at                   | Timestamp    | Indicator of when the prescriptions turns inactive - doses and reminders no longer generate etc.
module_activity_starts_at | Timestamp    | If users want data of device activity before start of prescription, this attribute can be set to an earlier time. Doses and reminders will not start, but a log of taken_pods will be created by the device, if such activity occurs.
module_activity_ends_at   | Timestamp    | Same as above, but after prescriptions end.
pod_sequence              | String(array)| The order of which taken_pods are to be taken. If sequence does not matter (all pods contain same dose for example), leave empty.
patient_reference         | String       | The name of the patient. Used in some of the default flag messages
language                  | String       | The language the patient prefers. Current supports only sv and en. Default flag descriptions will be sent using this language.

### Relationships
Name                   | Relation   | Comments
---------------------  | ---------- | -----------
organization           | belongs_to | Owner of the prescription
mia_modules            | has_many   | All devices used by the prescription.
flag_policies          | has_many   | All flag policies in use. If a recipient is present on the policy, all flags of matching type under the prescription will be dispatched to the recipient
notification_policies  | has_many   | All notification policies in use. If a recipient is present on the policy, all doses that are not taken/muted under the prescription will dispatch a reminder to the recipient
scheduled_doses        | has_many   | All doses generated by the prescriptions dose schemas
scheduled_dose_schemas | has many   | All dose schemas beloning to the prescription.
recipients             | has_many   | All recipients belonging to the prescription. Recipients are not in use unless also connected to a flag_policy or notification_policy.
packages               | has_many   | All packages created by the prescriptions mia_modules.
taken_pods             | has_many   | All taken_pods generated by the prescriptions mia_modules
notifications          | has_many   | All notifications sent under the prescription (for doses, notification_policies and recipients belonging to the prescription)
flags                  | has_many   | All flags that has occured under the prescription. Will be created even if no matching flag_policy exists (can be displayed without being dispatched)
mia_module_schedules   | has_many   | All mia_module_schedules belonging to the prescriptions mia_modules. Used to manage temporary module ownerships.

### Filters
Name                        | Type       Description
-----------------           | ---------- |
starts_at                   | Equal to   |
ends_at                     | Equal to   |
module_activity_starts_at   | Equal to   |
module_activity_ends_at     | Equal to   |
pod_sequence                | Equal to   |
patient_reference           | Equal to   |
language                    | Equal to   |
active                      | Equal to   | A prescription is active when current time is within starts_at and ends_at of the prescription
with_patient_reference_like | Matches    | Search for matches. "Be" matches "Bertil", "Bertil!" does not, and so on.
starts_at_after             | Equal to   | Returns prescriptions have attribute starts_at higher than given timestamp
starts_at_before            | Equal to   | Returns prescriptions have attribute starts_at lower than given timestamp
ends_at_after               | Equal to   | Returns prescriptions have attribute ends_at higher than given timestamp
ends_at_before              | Equal to   | Returns prescriptions have attribute ends_at lower than given timestamp

### Available resources
* get/
* get/:id
* put/:id
* post
* delete/:id

## Recipients
A recipient is a receiver of notifications and flags. A prescription can have several. Easiest to think of as a contact in a contact list.

> Example fetch payload (for GET v2/recipients)

```json
{
  "data": [{
    "id": "105",
    "type": "recipients",
    "links": {
      "self": "http://api.mevia.se/v2/recipients/105"
    },
    "attributes": {
      "name": "Bertil",
      "phone": "123456789",
      "email": "example@mevia.se"
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

> Example post payload (for POST v2/recipients)

```json
{
  "data": {
    "type": "recipients",
    "attributes": {
      "name": "Bertil",
      "phone": "123456789",
      "email": "example@mevia.se"
    }
  }
}
```

Name    | Format/Type  | Description
--------| ------------ | -----------
id      | Integer      | ID of the recipient
name    | String       | Name of the recipient. Used for display purposes only (never used in default messages etc.).
phone   | String       | Phone number used to receive sms messages
email   | String       | Email address used to receive emails

### Relationships
Name                   | Relation   | Comments
---------------------  | ---------- | -----------
prescription           | belongs_to | Owner of the recipient
flag_policies          | has_many   | Recipient will be notified when a flag is created matching the flag_type of the policy
notification_policies  | has_many   | Recipient will be reminded when a dose matches the criteria of the policy

### Filters
Name   | Type
------ | ----------
phone  | Equal to
name   | Equal to
email  | Equal to


### Available resources
* get/
* get/:id
* put/:id
* post
* delete/:id

## Scheduled dose schemas
A dose schema is a set of rules on how to generate scheduled doses for its prescription.
Several attributes will be added in the next version of the API. Keep them in mind when building stuff using schemas :)

> Example fetch payload (for GET v2/scheduled_dose_schemas)

```json
{
  "data": [{
    "id": "220",
    "type": "scheduled_dose_schemas",
    "links": {
      "self": "http://api.mevia.se/v2/scheduled_dose_schemas/220"
    },
    "attributes": {
      "start_time": "14:30",
      "end_time": "15:00",
      "pod_amount": 1,
      "start_date": "2017-11-06",
      "end_date": "2017-12-31",
      "days_between_doses": 1,
      "prescription_id": 105
    },
    "relationships": {
      "scheduled_doses": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_dose_schemas/220/relationships/scheduled_doses",
          "related": "http://api.mevia.se/v2/scheduled_dose_schemas/220/scheduled_doses"
        }
      },
      "prescription": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_dose_schemas/220/relationships/prescription",
          "related": "http://api.mevia.se/v2/scheduled_dose_schemas/220/prescription"
        }
      }
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

Name              | Format/Type  | Description
----------------- | ------------ | ----------------------------------------------------------------------------------------------
id                | Integer      | ID of the dose schema
start_time        | String(HH:MM)| Specifies at what time generated doses should start
end_time          | String(HH:MM)| Specifies at what time generated doses should end
pod_amount        | Integer      | Specifies what amount of pods/doses should be taken during the dose period.
start_date        | Date         | First day to apply scheduling rules on
end_date          | Date         | Last day to apply scheduling rules on
days_between_doses| Integer      | Days between doses. 2 will generate a dose every other day, 7 will generate a weekly dose etc.


### Relationships

> Example post payload (for POST v2/scheduled_dose_schemas)

```json
{
  "data": {
    "type": "scheduled_dose_schemas",
    "attributes": {
      "start_time": "14:30",
      "end_time": "15:00",
      "pod_amount": 1,
      "start_date": "2017-11-06",
      "end_date": "2017-12-31",
      "days_between_doses": 1,
      "prescription_id": 105
    }
  }
}
```

Name            | Relation    | Comments
--------------- | ----------- | -----------
prescription    | belongs_to  |
recipients      | has_many    | Recipients to notify when dose is not taken/muted at specified time
notifications   | has_many    | All notifications dispatched by the policy
scheduled_doses | has_many    | All doses for which the recipients will be notified (currently: all doses beloning to the same prescription)

### Filters
Name               | Type
------------------ | ----------
id                 | Equal to
start_time         | Equal to
end_time           | Equal to
pod_amount         | Equal to
start_date         | Equal to
end_date           | Equal to
days_between_doses | Equal to
start_date_after   | Equal to   | Returns scheduled_dose_schemas that have attribute start_date higher than given timestamp
start_date_before  | Equal to   | Returns scheduled_dose_schemas that have attribute start_date lower than given timestamp
end_date_after     | Equal to   | Returns scheduled_dose_schemas that have attribute end_date higher than given timestamp
end_date_before    | Equal to   | Returns scheduled_dose_schemas that have attribute end_date lower than given timestamp

### Available resources
* get/
* get/:id
* post
* put/:id
* delete/:id

## Scheduled doses
A scheduled dose is a planned period of time during which its prescription is supposed to take one or more pods/doses.

> Example fetch payload (for GET v2/scheduled_doses)

```json
{
  "data": [{
    "id": "15154",
    "type": "scheduled_doses",
    "links": {
      "self": "http://api.mevia.se/v2/scheduled_doses/15154"
    },
    "attributes": {
      "period_starts_at": "2017-11-06T13:30:00.000Z",
      "period_ends_at": "2017-11-06T14:00:00.000Z",
      "taken": true,
      "completed_at": "2017-11-06T13:49:22.245Z",
      "nr_remaining_pods": 0,
      "expected_pods": null,
      "muted": false,
      "nr_remaining_pods_until_mute": 0,
      "scheduled_dose_schema_id": 220,
      "prescription_id": 105
    },
    "relationships": {
      "scheduled_dose_schema": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_doses/15154/relationships/scheduled_dose_schema",
          "related": "http://api.mevia.se/v2/scheduled_doses/15154/scheduled_dose_schema"
        }
      },
      "prescription": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_doses/15154/relationships/prescription",
          "related": "http://api.mevia.se/v2/scheduled_doses/15154/prescription"
        }
      },
      "notifications": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_doses/15154/relationships/notifications",
          "related": "http://api.mevia.se/v2/scheduled_doses/15154/notifications"
        }
      },
      "taken_pods": {
        "links": {
          "self": "http://api.mevia.se/v2/scheduled_doses/15154/relationships/taken_pods",
          "related": "http://api.mevia.se/v2/scheduled_doses/15154/taken_pods"
        }
      }
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

Name                         | Format/Type   | Description
-----------------            | -----------   | ----------------------------------------------------------------------------------------------
id                           | Integer       | ID of the dose
period_starts_at             | Datetime      | Specifies at what time the dose starts
period_ends_at               | Datetime      | Specifies at what time the dose ends
taken                        | Boolean       | True if the dose has been taken correctly, otherwise false
completed_at                 | Datetime      | Time at which the dose was completed *correctly*
nr_remaining_pods            | Integer       | How many doses left until dose is taken *correctly*
nr_remaining_pods_until_mute | Boolean       | How many doses left until dose is marked as muted (doesn't care if the pods/doses were taken correctly). A dose with this set to 0 will not send any more notifications
expected_pods                | String(array) | The pods that are supposed to be taken during this dose period. Only set if prescription has a pod_sequence.
muted                        | Boolean       | Same behaviour as if nr_remaining_pods_until_mute reaches zero, but manually toggled.


### Relationships
Name                  | Relation   | Comments
--------------------- | ---------- | --------------------------------------------------------------------------------------------
prescription          | belongs_to |
taken_pods            | has_many   | All pods related to this dose. Decided either by timestamp of the pod or by its sequence number
notifications         | has_many   | All notifications/reminders sent regarding this dose
scheduled_dose_schema | belongs_to | The schema which generated this dose

### Filters
Name                         | Type                     | Description
---------------------------- | ------------------------ | --------------------
id                           | Equal to                 |
period_starts_at             | Equal to                 |
period_ends_at               | Equal to                 |
taken                        | Equal to                 |
completed_at                 | Equal to                 |
nr_remaining_pods            | Equal to                 |
nr_remaining_pods_until_mute | Equal to                 |
expected_pods                | Equal to                 |
muted                        | Equal to                 |
pod_number                   | Matches                  | Given a list of numbers, returns all doses in which all numbers are expected
date_to                      | Less than or equal to    | Given a datetime, returns all doses ending before that datetime
date_from                    | Greater than or equal to | Given a datetime, returns all doses starting after that datetime

### Available resources
* get/
* get/:id
* post
* put/:id
* delete/:id

## Taken pods
A taken pod is generated by a mia_module whenever its owner removes a pill/dose/pod from its package.

> Example fetch payload (for GET v2/taken_pods)

```json
{
  "data": [{
    "id": "13590",
    "type": "taken_pods",
    "links": {
      "self": "http://api.mevia.se/v2/taken_pods/13590"
    },
    "attributes": {
      "number": 4,
      "taken_at": "2017-11-06T12:28:56.000Z",
      "prescription_id": 105,
      "scheduled_dose_id": null,
      "package_id": 4893
    },
    "relationships": {
      "prescription": {
        "links": {
          "self": "http://api.mevia.se/v2/taken_pods/13590/relationships/prescription",
          "related": "http://api.mevia.se/v2/taken_pods/13590/prescription"
        }
      },
      "scheduled_dose": {
        "links": {
          "self": "http://api.mevia.se/v2/taken_pods/13590/relationships/scheduled_dose",
          "related": "http://api.mevia.se/v2/taken_pods/13590/scheduled_dose"
        }
      },
      "package": {
        "links": {
          "self": "http://api.mevia.se/v2/taken_pods/13590/relationships/package",
          "related": "http://api.mevia.se/v2/taken_pods/13590/package"
        }
      }
    }
  }],
  "meta": {
    "record_count": 1
  }
}
```

### Attributes

Name                         | Format/Type | Description
-----------------            | ----------- | ----------------------------------------------------------------------------------------------
id                           | Integer     | ID of the pod
number                       | Integer     | The index (in its package) of the pod. Used to match against its prescriptions pod_sequence, if used
taken_at                     | Datetime    | Specifies at what time the pod was taken

### Relationships
Name           | Relation   | Comments
-------------- | ---------- | --------------------------------------------------------------------------------------------
prescription   | belongs_to |
package        | belongs_to |
mia_module     | belongs_to |
scheduled_dose | belongs_to |

### Filters
Name            | Type
--------        | ---------
taken_at        | Equal to
Number          | Equal to
taken_at_after  | Equal to | Returns taken_pods that have attribute taken_at higher than given timestamp
taken_at_before | Equal to | Returns taken_pods that have attribute taken_at lower than given timestamp

### Available resources
* get/
* get/:id
