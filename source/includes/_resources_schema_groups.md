# Schema Groups
Schema groups are used to manage dose schedules were the scheduled is more complex than one or several identical daily doses. The most common use case is to build a weekly schedule. One example would be were the patient takes one pill every morning, but only on weekdays. Internally, a schema group simply handles a group of scheduled dose schemas, updating the group is just a easy way to update all schemas in said group.

## Get all schema_groups

> Response structure:

```json
{
    "data": [
        {
            "id": Integer,
            "type": "schema_groups",
            "attributes": {
                "prescription_id": Integer,
                "scheduled_dose_schemas": [
                    {
                        "id": Integer,
                        "start_time": String - In the format of "10:00",
                        "end_time": String - In the format of "10:00",
                        "pod_amount": Integer,
                        "start_date": String (YYYY-MM-DD),
                        "end_date": String (YYYY-MM-DD),
                        "days_between_doses": Integer,
                        "prescription_id": Integer,
                        "schema_group_id": Integer
                    }
                ]
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    },
    "meta": {
        "API": {
            "version": "1.8.0"
        }
    }
}
```

This endpoint retrieves all schema_groups with ability to specify both offset and limit

### HTTP Request

`GET https://api.mevia.com/v1/schema_groups?offset=0&limit=1`

### Query Parameters
Parameter        | Format         | Description
---------        | -------        | -----------
offset           | Integer        | Number of flags to offset with. Used for pagination
limit            | Integer        | Maximum number of flags to fetch.

## Get specific schema_group

> Response structure:

```json
{
    "data":
    {
        "id": Integer,
        "type": "schema_groups",
        "attributes": {
            "prescription_id": Integer,
            "scheduled_dose_schemas": [
                {
                    "id": Integer,
                    "start_time": String - In the format of "10:00",
                    "end_time": String - In the format of "10:00",
                    "pod_amount": Integer,
                    "start_date": String (YYYY-MM-DD),
                    "end_date": String (YYYY-MM-DD),
                    "days_between_doses": Integer,
                    "prescription_id": Integer,
                    "schema_group_id": Integer
                }
            ]
        }
    },
    "jsonapi": {
        "version": "1.0"
    },
    "meta": {
        "API": {
            "version": "1.8.0"
        }
    }
}
```

This endpoint retrieves a single schema_group

### HTTP Request

`GET https://api.mevia.com/v1/schema_groups/:id

## Create a schema_group

> Request structure

```json
{
   "schema_group": {
      "start_time": String (HH:MM),
      "end_time": String (HH:MM),
      "scheduled_dose_schemas": [
        {
          "start_date": String(YYYY-mm-dd), // Required
          "end_date": String(YYYY-mm-dd),   // Required
          "days_between_doses": Integer,  // Defaults to 7
          "pod_amount": Integer             // Defaults to 1
        }
      ]
   }
}
```

> Response structure

```json
{
    "data":
    {
        "id": Integer,
        "type": "schema_groups",
        "attributes": {
            "prescription_id": Integer,
            "scheduled_dose_schemas": [
                {
                    "id": Integer,
                    "start_time": String - In the format of "10:00",
                    "end_time": String - In the format of "10:00",
                    "pod_amount": Integer,
                    "start_date": String (YYYY-MM-DD),
                    "end_date": String (YYYY-MM-DD),
                    "days_between_doses": Integer,
                    "prescription_id": Integer,
                    "schema_group_id": Integer
                }
            ]
        }
    },
    "jsonapi": {
        "version": "1.0"
    },
    "meta": {
        "API": {
            "version": "1.8.0"
        }
    }
}
```

This endpoint creates a schema_group with a number of underlying scheduled_dose_schemas.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/schema_groups`


## Update a schema_group


> Request structure

```json
{
   "schema_group": {
      "start_time": String (HH:MM),
      "end_time": String (HH:MM)
   }
}
```

> Response structure

```json
{
    "data":
    {
        "id": Integer,
        "type": "schema_groups",
        "attributes": {
            "prescription_id": Integer,
            "scheduled_dose_schemas": [
                {
                    "id": Integer,
                    "start_time": String - In the format of "10:00",
                    "end_time": String - In the format of "10:00",
                    "pod_amount": Integer,
                    "start_date": String (YYYY-MM-DD),
                    "end_date": String (YYYY-MM-DD),
                    "days_between_doses": Integer,
                    "prescription_id": Integer,
                    "schema_group_id": Integer
                }
            ]
        }
    },
    "jsonapi": {
        "version": "1.0"
    },
    "meta": {
        "API": {
            "version": "1.8.0"
        }
    }
}
```

This endpoint updates a schema_group. Note that all underlying scheduled_dose_schemas will be updated as well - causing all future scheduled_doses to be updated to.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/schema_groups`


## Delete a schema_group

> Response structure:

```json
{
    "data":
    {
        "id": Integer,
        "type": "schema_groups",
        "attributes": {
            "prescription_id": Integer,
            "scheduled_dose_schemas": [
                {
                    "id": Integer,
                    "start_time": String - In the format of "10:00",
                    "end_time": String - In the format of "10:00",
                    "pod_amount": Integer,
                    "start_date": String (YYYY-MM-DD),
                    "end_date": String (YYYY-MM-DD),
                    "days_between_doses": Integer,
                    "prescription_id": Integer,
                    "schema_group_id": Integer
                }
            ]
        }
    },
    "jsonapi": {
        "version": "1.0"
    },
    "meta": {
        "API": {
            "version": "1.8.0"
        }
    }
}
```

This endpoint deletes a single schema_group

### HTTP Request

`DELETE https://api.mevia.com/v1/schema_groups/:id
