# Taken pods
The following resources are used to fetch taken pods. A taken pod is simply representation of the event when a medicine is taken. Contains the number of the pod, and the time at which it was taken.

## Get all taken pods from a prescription

> Response structure:

```json
{
    "data": [
        {
            "id": Integer,
            "type": "taken_pods",
            "attributes": {
                "number": Integer,
                "taken_at": String Timestamp (Formated in ISO 8601),
                "package_id": Integer,
                "scheduled_dose_id": Integer,
                "prescription_id": Integer
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

This endpoint retrieves all taken pods for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/taken_pods`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

## Get specific taken pods from a prescription

> Response structure:

```json
{
    "data": {
        "id": Integer,
        "type": "taken_pods",
        "attributes": {
            "number": Integer,
            "taken_at": String Timestamp (Formated in ISO 8601),
            "package_id": Integer,
            "scheduled_dose_id": Integer,
            "prescription_id": Integer
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

This endpoint retrieves a specific taken_pod.

### HTTP Request

`GET https://api.mevia.com/v1/taken_pods/id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | id of the taken pod to fetch