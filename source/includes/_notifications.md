# Notifications
These methods are used to obtain, update and create the reminders thats beeing sent by the API. Notifications are stored even after beeing sent, and can be fetched like any other.

## Get all Notifications from a Prescription

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all notifications belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notifications`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Get all Notifications from a Notification Policy

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all notifications belonging to the given prescription and notification policy.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:notification_policy_id/notifications`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_policy_id | Integer | ID of the notification policy

## Get all through notifications from a Scheduled Dose

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all notifications belonging to the given prescription and scheduled dose.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/notifications`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription
scheduled_dose_id | Integer | ID of the scheduled dose

## Get specific notifications from a Prescription

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves specific notifications belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | IDs of the notifications to fetch


## Get specific notifications from a Notification Policy

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves specific notifications belonging to the given prescription and notification policy.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:notification_policy_id/notifications/:id`

### Query Parameters
Parameter              | Format        | Description
---------              | -------       | -----------
prescription_id        | Integer       | ID of the prescription
notification_policy_id | Integer       | ID of the notification policy
id                     | id1, id2, id3 | IDs of the notifications to fetch

## Get specific notifications from a Scheduled Dose

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves specific notifications belonging to the given prescription and scheduled dose.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/notifications/:id`

### Query Parameters
Parameter         | Format        | Description
---------         | -------       | -----------
prescription_id   | Integer       | ID of the prescription
scheduled_dose_id | Integer       | ID of the scheduled dose
id                | id1, id2, id3 | IDs of the notifications to fetch

## Create a notification on a Scheduled Dose

> Request structure:

```json
{
  "notifications": [
    {
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
    },
  ]
}
```

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint creates a new notification to the given scheduled dose.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/notifications`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription the dose belongs to
scheduled_dose_id | Integer | ID of the scheduled dose

## Update notification on a Prescription

> Request structure:

```json
{
  "notifications": [
    {
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
    },
  ]
}
```

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves updates a notification belonging to the given prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id            | ID of the notification to update


## Update notification on a  Notification Policy

> Request structure:

```json
{
  "notifications": [
    {
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
    },
  ]
}
```

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint updates a specific notification belonging to the given prescription and notification policy.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:notification_policy_id/notifications/:id`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_policy_id | Integer | ID of the notification policy
id                     | id      | IDs of the notification to update

## Update a notification on a Scheduled Dose

> Request structure:

```json
{
  "notifications": [
    {
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
    },
  ]
}
```

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint updates a specific notification belonging to the given prescription and scheduled dose.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/notifications/:id`

### Query Parameters
Parameter         | Format        | Description
---------         | -------       | -----------
prescription_id   | Integer       | ID of the prescription
scheduled_dose_id | Integer       | ID of the scheduled dose
id                | id            | ID of the notification to update

## Delete a notification from a Prescription

> Response structure:

```json
{
  "notifications": [
    {
      "id": Integer,
      "moment_to_send": String Timestamp (Formated in ISO 8601),
      "sent_at": String Timestamp (Formated in ISO 8601),
      "message": String
      "links": {
        "notification_policy": [ID]
      }
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint deletes specific notifications belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | IDs of the notifications to delete