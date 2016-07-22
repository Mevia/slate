# Prescriptions
These methods are used to register a prescription in the API. When prescriptions are registered, reminders and statusen will automatically be handled in the API.

## Get All Prescriptions

> Response structure:

```json
{
   "prescriptions":[
      {
         "id": Integer,
         "start_date": String (YYYY-MM-DD),
         "end_date": String (YYYY-MM-DD),
         "created_at": String Timestamp (Formated in ISO 8601),
         "updated_at": String Timestamp (Formated in ISO 8601)
         "links":{
            "mia_modules":[id1, id2, id3...],
            "mia_module_schedules":[id1, id2, id3...],
            "packages":[id1, id2, id3...],
            "taken_pods":[id1, id2, id3...],
            "events":[id1, id2, id3...],
            "scheduled_dose_schemas":[id1, id2, id3...],
            "scheduled_doses":[id1, id2, id3...],
            "notification_policies":[id1, id2, id3...],
            "notifications":[id1, id2, id3...],
            "recipients":[id1, id2, id3...],
            "flag_policies":[id1, id2, id3...],
            "flags":[id1, id2, id3...]
         }
      },
      "linked": [
          "events": [],
          .
          .
          "This is what is included with parameter include.
             E.g. events, packages etc."
          .
          .
       ],
   ],
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

This endpoint retrieves all prescriptions.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions`

### Query Parameters

Parameter | Format        | Description
--------- | -------       | -----------
include   | include=x,y,z | Specify what resources to include. Available options are: mia_modules, mia_module_schedules, packages, taken_pods, events, scheduled_dose_schemas, scheduled_doses, notification_policies, notifications, recipients, flag_policies, flags
date_from | YYYY-MM-DD    | Filters all resources included via the include parameter to those relevant after the specified date. Resources that will be filtered are: flags, scheduled_doses, events, notifications
date_to   | YYYY-MM-DD    | Filters all resources included via the include parameter to those relevant before the specified date. Resources that will be filtered are: flags, scheduled_doses, events, notifications

## Get a Specific Prescription

> Example response:

```json
{
   "prescriptions": {
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "created_at": String Timestamp (Formated in ISO 8601),
      "updated_at": String Timestamp (Formated in ISO 8601),
       "links":{
          "mia_modules":[id1, id2, id3...],
          "mia_module_schedules":[id1, id2, id3...],
          "packages":[id1, id2, id3...],
          "taken_pods":[id1, id2, id3...],
          "events":[id1, id2, id3...],
          "scheduled_dose_schemas":[id1, id2, id3...],
          "scheduled_doses":[id1, id2, id3...],
          "notification_policies":[id1, id2, id3...],
          "notifications":[id1, id2, id3...],
          "recipients":[id1, id2, id3...],
          "flag_policies":[id1, id2, id3...],
          "flags":[id1, id2, id3...]
       }
   },
   "linked": [
      "events": [],
      .
      .
      "This is what is included with parameter include.
         E.g. events, packages etc."
      .
      .
   ],
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

This endpoint retrieves a specific prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:id`

### URL Parameters

Parameter | Format        | Description
--------- | -------       | -----------
id        | Integer       | ID of the wanted prescription.
include   | include=x,y,z | Specify what resources to include. Available options are: mia_modules, mia_module_schedules, packages, taken_pods, events, scheduled_dose_schemas, scheduled_doses, notification_policies, notifications, recipients, flag_policies, flags
date_from | YYYY-MM-DD    | Filters all resources included via the include parameter to those relevant after the specified date. Resources that will be filtered are: flags, scheduled_doses, events, notifications
date_to   | YYYY-MM-DD    | Filters all resources included via the include parameter to those relevant before the specified date. Resources that will be filtered are: flags, scheduled_doses, events, notifications


## Create a Prescription

> Request structure

```json
{
   "prescriptions":{
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "patient_birthdate": String (YYYY-MM-DD) (optional),
      "patient_gender": String ("male"|"female") (optional)
   },
   "linked":{
      "mia_modules":[
         {
            "id": Integer,
            "module_number": String,
            "mia_module_schedules":[
               {
                  "id": Integer,
                  "start_date": String (YYYY-MM-DD),
                  "end_date": String (YYYY-MM-DD)
               }
            ],

         }
         .
         " To see what a certain resource should contain, look at that resource's part of this documentation"
         .
      ],
      "scheduled_dose_schemas":[...],
      "notification_policies":[...],
      "flag_policies":[...]
   },
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/`

### URL Parameters
No parameters

> Request structure

```json
{
   "prescriptions":{
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "patient_birthdate": String (YYYY-MM-DD) (optional),
      "patient_gender": String ("male"|"female") (optional),
      "pod_sequence": String ("[1,2,3,4,5...]") (Optional)
   },
   "linked":{
      "mia_modules":[
         {
            "id": Integer,
            "module_number": String,
            "name": "String",
            "mia_module_schedules":[
               {
                  "id": Integer,
                  "start_date": String (YYYY-MM-DD),
                  "end_date": String (YYYY-MM-DD)
               }
            ],

         }
         .
         " To see what a certain resource should contain, look at that resource's part of this documentation"
         .
      ],
      "scheduled_dose_schemas":[...],
      "notification_policies":[...],
      "flag_policies":[...]
   },
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

> Response structure

```json
{
   "prescriptions":{
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "pod_sequence": String ("[1,2,3,4,5...]") (Optional),
      "patient_reference": String,
      "patient_gender": String,
      "patient_birthdate": String (YYYY-MM-DD),
      "links":{
         "mia_modules":[...],
         "mia_module_schedules":[...],
         "packages":[...],
         "taken_pods":[...],
         "events":[...],
         "scheduled_dose_schemas":[...],
         "scheduled_doses":[...],
         "notification_policies":[...],
         "notifications":[...],
         "recipients":[...],
         "flag_policies":[...],
         "flags":[...]
      }
   },
   "meta":{
      "API":{
         "version": String
      }
   }
}
```


## Update a Prescription

> Request structure

```json
{
   "prescriptions":{
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "patient_birthdate": String (YYYY-MM-DD) (optional),
      "patient_gender": String ("male"|"female") (optional),
      "pod_sequence": String ("[1,2,3,4,5...]") (Optional)
   },
   "linked":{
      "mia_modules":[
         {
            "id": Integer,
            "module_number": String,
            "mia_module_schedules":[
               {
                  "id": Integer,
                  "start_date": String (YYYY-MM-DD),
                  "end_date": String (YYYY-MM-DD)
               }
            ],

         }
         .
         " To see what a certain resource should contain, look at that resource's part of this documentation"
         .
      ],
      "scheduled_dose_schemas":[...],
      "notification_policies":[...],
      "flag_policies":[...]
   },
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:id`

### URL Parameters

Parameter | Format        | Description
--------- | -------       | -----------
id        | Integer       | ID of the prescription to update.

> Response structure

```json
{
   "prescriptions":{
      "id": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "pod_sequence": String,
      "patient_reference": String,
      "patient_gender": String,
      "patient_birthdate": String (YYYY-MM-DD),
      "links":{
         "mia_modules":[...],
         "mia_module_schedules":[...],
         "packages":[...],
         "taken_pods":[...],
         "events":[...],
         "scheduled_dose_schemas":[...],
         "scheduled_doses":[...],
         "notification_policies":[...],
         "notifications":[...],
         "recipients":[...],
         "flag_policies":[...],
         "flags":[...]
      }
   },
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

## Delete a Prescription

Delete a given prescription, removing all of its related data.

### HTTP Request

`DELETE https://api.mevia.com/v1/prescriptions/:id`

### URL Parameters

Parameter | Format        | Description
--------- | -------       | -----------
id        | Integer       | ID of the prescription to delete.
