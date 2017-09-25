# Scheduled Dose Schemas
These methods are used to set a schedule schema, used for generating a daily schedule of dose intervals.

## Get all scheduled dose schemas

```json
{
  "scheduled_dose_schemas": [
    {
      "id": Integer,
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "days_between_doses": Integer,
      "prescription_id": Integer
    }
  ],
  "meta": {...}
}
```

This endpoint retrieves all scheduled dose schemas belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_dose_schemas`

## Get specific scheduled dose schemas

> Response structure:

```json
{
  "scheduled_dose_schema": {
    "id": Integer,
    "start_time": String, // In the format of "10:00"
    "end_time": String, // In the format of "10:00"
    "pod_amount": Integer,
    "start_date": String (YYYY-MM-DD),
    "end_date": String (YYYY-MM-DD),
    "days_between_doses": Integer,
    "prescription_id": Integer
  },
  "meta": {...}
}
```

This endpoint retrieves a single specific scheduled dose schema

### HTTP Request

`GET https://api.mevia.com/v1/scheduled_dose_schemas/:id`

## Create a scheduled dose schema

> Request structure:

```json
{
  "scheduled_dose_schema": [
    {
      "start_time": String, // In the format of "10:00"
      "end_time": String, // In the format of "10:00"
      "pod_amount": Integer,
      "start_date": Date, // Optional - Format: YYYY-MM-DD
      "end_date": Date, // Optional - Format: YYYY-MM-DD
      "days_between_doses": Integer // Optional
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
      "start_date": String (YYYY-MM-DD),
      "end_date": String (YYYY-MM-DD),
      "days_between_doses": Integer,
      "prescription_id": Integer
    }
  ],
  "meta": {...}
}
```

This endpoint creates a scheduled dose schema to the given prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses`

## Update a schduled dose schema

> Request structure:

```json
{
  "scheduled_dose_schema": {
    "start_time": String, // In the format of "10:00"
    "end_time": String, // In the format of "10:00"
    "pod_amount": Integer,
    "start_date": Date, // Optional - Format: YYYY-MM-DD
    "end_date": Date, // Optional - Format: YYYY-MM-DD
    "days_between_doses": Integer // Optional
  }
}
```

> Response structure:

```json
{
  "scheduled_dose_schema": {
    "id": Integer,
    "start_time": String, // In the format of "10:00"
    "end_time": String, // In the format of "10:00"
    "pod_amount": Integer,
    "start_date": String (YYYY-MM-DD),
    "end_date": String (YYYY-MM-DD),
    "days_between_doses": Integer,
    "prescription_id": Integer
  },
  "meta": {...}
}
```

This endpoint updates a scheduled dose schema belonging to the given prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/scheduled_doses/:id`

## Delete through Prescription

> Response structure:

```json
{
  "scheduled_dose_schema": {
    "id": Integer,
    "start_time": String, // In the format of "10:00"
    "end_time": String, // In the format of "10:00"
    "pod_amount": Integer,
    "start_date": String (YYYY-MM-DD),
    "end_date": String (YYYY-MM-DD),
    "days_between_doses": Integer,
    "prescription_id": Integer
  },
  "meta": {...}
}
```

This endpoint deletes specific scheduled dose schemas belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/scheduled_dose_schemas/:id`
