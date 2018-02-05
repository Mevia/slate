# Prescriptions
These methods are used to manage prescriptions in the API.

## Get All Prescriptions

> Response structure:

```json
{
    "data": [
        {
            "id": Integer,
            "type": "prescriptions",
            "attributes": {
                "starts_at": String Timestamp (Formated in ISO 8601),
                "ends_at": String Timestamp (Formated in ISO 8601),
                "start_date": String (YYYY-MM-DD),
                "end_date": String (YYYY-MM-DD),
                "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
                "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
                "pod_sequence": String: "[1,2,3,4]" - can be null,
                "patient_reference": String,
                "language": String
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

This endpoint retrieves all prescriptions.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions`

### Query Parameters

Parameter | Format  | Description
--------- | ------- | -----------
active    | Boolean | Filter prescriptions on its active status. A prescription is considered active if retrieved between its starts_at and ends_at
with_patient_reference_like | String | Filter prescriptions containing the argument as a substring. Case insensitive.

## Get a Specific Prescription

> Example response:

```json
{
    "data": {
        "id": Integer,
        "type": "prescriptions",
        "attributes": {
            "starts_at": String Timestamp (Formated in ISO 8601),
            "ends_at": String Timestamp (Formated in ISO 8601),
            "start_date": String (YYYY-MM-DD),
            "end_date": String (YYYY-MM-DD),
            "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
            "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
            "pod_sequence": String: "[1,2,3,4]" - can be null,
            "patient_reference": String,
            "language": String
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

This endpoint retrieves a specific prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:id`

## Create a Prescription

> Request structure

```json
{
   "prescription": {
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
      "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
      "ends_at": String Timestamp (Formated in ISO 8601),
      "starts_at": String Timestamp (Formated in ISO 8601),
      "patient_birthdate": String (YYYY-MM-DD) (optional),
      "patient_gender": String ("male"|"female") (optional),
      "pod_sequence": String ("[1,2,3,4,5...]") (Optional),
      "language": String
    }
}
```

> Response structure

```json
{
    "data": {
        "id": Integer,
        "type": "prescriptions",
        "attributes": {
            "starts_at": String Timestamp (Formated in ISO 8601),
            "ends_at": String Timestamp (Formated in ISO 8601),
            "start_date": String (YYYY-MM-DD),
            "end_date": String (YYYY-MM-DD),
            "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
            "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
            "pod_sequence": String: "[1,2,3,4]" - can be null,
            "patient_reference": String,
            "language": String
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

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/`

## Update a Prescription

> Request structure

```json
{
   "prescription": {
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
      "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
      "ends_at": String Timestamp (Formated in ISO 8601),
      "starts_at": String Timestamp (Formated in ISO 8601),
      "patient_birthdate": String (YYYY-MM-DD) (optional),
      "patient_gender": String ("male"|"female") (optional),
      "pod_sequence": String ("[1,2,3,4,5...]") (Optional),
      "language": String
    }
}
```

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:id`

> Response structure

```json
{
    "data": {
        "id": Integer,
        "type": "prescriptions",
        "attributes": {
            "starts_at": String Timestamp (Formated in ISO 8601),
            "ends_at": String Timestamp (Formated in ISO 8601),
            "start_date": String (YYYY-MM-DD),
            "end_date": String (YYYY-MM-DD),
            "module_activity_starts_at": String Timestamp (Formated in ISO 8601),
            "module_activity_ends_at": String Timestamp (Formated in ISO 8601),
            "pod_sequence": String: "[1,2,3,4]" - can be null,
            "patient_reference": String,
            "language": String
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

## Delete a Prescription

Delete a given prescription, removing all of its related data.

### HTTP Request

`DELETE https://api.mevia.com/v1/prescriptions/:id`
