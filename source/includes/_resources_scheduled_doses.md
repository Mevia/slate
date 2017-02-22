# Scheduled Doses
These methods are used to set a schedule for taking doses. The recommended way of creating scheduled doses are by scheduled dose schemas.

## Get all scheduled doses from a Prescription

> Response structure:

```json
{
  "scheduled_doses": [
    {
      "id": Integer,
      "period_starts_at": String Timestamp (Formated in ISO 8601),
      "period_ends_at": String Timestamp (Formated in ISO 8601),
      "is_taken": Boolean,
      "completed_at": String Timestamp (Formated in ISO 8601),
      "nr_remaining_pods": Integer,
      "expected_pods": [Integer],
      "is_muted": Boolean
    }
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all scheduled doses belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses`

## Get a single specific scheduled dose

> Response structure:

```json
{
  "scheduled_dose": {
    "id": Integer,
    "period_starts_at": String Timestamp (Formated in ISO 8601),
    "period_ends_at": String Timestamp (Formated in ISO 8601),
    "is_taken": Boolean,
    "completed_at": String Timestamp (Formated in ISO 8601),
    "nr_remaining_pods": Integer,
    "expected_pods": [Integer],
    "is_muted": Boolean
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves a single specific scheduled dose

### HTTP Request

`GET https://api.mevia.com/v1/scheduled_doses/:id`

## Update a scheduled dose

> Request structure:

```json
{
  "scheduled_doses": [
    {
      "period_starts_at": String Timestamp (Formated in ISO 8601),
      "period_ends_at": String Timestamp (Formated in ISO 8601),
      "completed_at": String Timestamp (Formated in ISO 8601),
      "nr_remaining_pods": Integer,
      "expected_pods": [Integer],
      "is_muted": Boolean,
    }
  ]
}
```

> Response structure:

```json
{
  "scheduled_doses": {
    "id": Integer,
    "period_starts_at": String Timestamp (Formated in ISO 8601),
    "period_ends_at": String Timestamp (Formated in ISO 8601),
    "is_taken": Boolean,
    "completed_at": String Timestamp (Formated in ISO 8601),
    "nr_remaining_pods": Integer,
    "expected_pods": [Integer],
    "is_muted": Boolean
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint updates a specific scheduled doses belonging to the given prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/scheduled_doses/:id`

## Delete a scheduled dose

> Response structure:

```json
{
  "scheduled_dose": {
    "id": Integer,
    "period_starts_at": String Timestamp (Formated in ISO 8601),
    "period_ends_at": String Timestamp (Formated in ISO 8601),
    "is_taken": Boolean,
    "completed_at": String Timestamp (Formated in ISO 8601),
    "nr_remaining_pods": Integer,
    "expected_pods": [Integer],
    "is_muted": Boolean
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint deletes a specific scheduled doses belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/scheduled_doses/:id`
