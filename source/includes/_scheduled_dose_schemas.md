# Scheduled Dose Schemas
These methods are used to set a schedule schema, used for generating a daily schedule of dose intervals.

## Get all scheduled dose schemas

> Response structure:

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "links": {
        "scheduled_doses": [id1, id2, id3...],
        "notification_policies": [id1, id2, id3...]
      }
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all scheduled dose schemas belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_dose_schemas`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

<aside class="success">
Remember — Include your api key in every request!
</aside>

## Get specific scheduled dose schemas

> Response structure:

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "links": {
        "scheduled_doses": [id1, id2, id3...],
        "notification_policies": [id1, id2, id3...]
      }
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves specific scheduled dose schemas belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_dose_schemas/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | IDs of the scheduled dose schemas to fetch

## Create a scheduled dose schema

> Request structure:

```json
{
  "scheduled_dose_schema": [
    {
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
    }
  ]
}
```

> Response structure:

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "links": {
        "scheduled_doses": [id1, id2, id3...],
        "notification_policies": [id1, id2, id3...]
      }
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint creates a scheduled dose schema to the given prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Update a schduled dose schema

> Request structure:

```json
{
  "scheduled_dose_schema": [
    {
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
    }
  ]
}
```

> Response structure:

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "links": {
        "scheduled_doses": [id1, id2, id3...],
        "notification_policies": [id1, id2, id3...]
      }
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint updates a scheduled dose schema belonging to the given prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | IDs of the scheduled dose schema to update

## Delete through Prescription

> Response structure:

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "links": {
        "scheduled_doses": [id1, id2, id3...],
        "notification_policies": [id1, id2, id3...]
      }
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint deletes specific scheduled dose schemas belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_dose_schemas/:id`

### Query Parameters
Parameter       | Format         | Description
---------       | -------        | -----------
prescription_id | Integer        | ID of the prescription
id              | id1, id2, id3..| IDs of the scheduled dose schemas to delete
