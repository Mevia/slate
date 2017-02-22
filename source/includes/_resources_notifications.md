# Notifications
These methods are used to obtain, update and create the reminders that are being sent by the API to its end users. Notifications are stored even after being sent, and can be fetched like any other resource.

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
      "scheduled_dose_id": Integer,
      "notification_policy_id": Integer
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
      "scheduled_dose_id": Integer,
      "notification_policy_id": Integer
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all notifications belonging to the given notification policy.

### HTTP Request

`GET https://api.mevia.com/v1/notification_policies/:notification_policy_id/notifications`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
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
      "scheduled_dose_id": Integer,
      "notification_policy_id": Integer
    },
  ],
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves all notifications belonging to the given scheduled dose.

### HTTP Request

`GET https://api.mevia.com/v1/scheduled_doses/:scheduled_dose_id/notifications`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
scheduled_dose_id | Integer | ID of the scheduled dose

## Get specific notifications

> Response structure:

```json
{
  "notification": {
    "id": Integer,
    "moment_to_send": String Timestamp (Formated in ISO 8601),
    "sent_at": String Timestamp (Formated in ISO 8601),
    "message": String
    "scheduled_dose_id": Integer,
    "notification_policy_id": Integer
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves a single specific notification.

### HTTP Request

`GET https://api.mevia.com/v1/notifications/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
ID        | Integer | ID of the notification to fetch

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
  "notification": {
    "id": Integer,
    "moment_to_send": String Timestamp (Formated in ISO 8601),
    "sent_at": String Timestamp (Formated in ISO 8601),
    "message": String
    "scheduled_dose_id": Integer,
    "notification_policy_id": Integer
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint creates a new notification to the given scheduled dose.

### HTTP Request

`POST https://api.mevia.com/v1/scheduled_doses/:scheduled_dose_id/notifications`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
scheduled_dose_id | Integer | ID of the scheduled dose

## Update a notification

> Request structure:

```json
{
  "notifications": {
    "moment_to_send": String Timestamp (Formated in ISO 8601),
    "sent_at": String Timestamp (Formated in ISO 8601),
    "message": String
  }
}
```

> Response structure:

```json
{
  "notification": {
    "id": Integer,
    "moment_to_send": String Timestamp (Formated in ISO 8601),
    "sent_at": String Timestamp (Formated in ISO 8601),
    "message": String
    "scheduled_dose_id": Integer,
    "notification_policy_id": Integer
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint updates a notification

### HTTP Request

`PUT https://api.mevia.com/v1/notifications/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ID of the notification to update

## Delete a notification

> Response structure:

```json
{
  "notification": {
    "id": Integer,
    "moment_to_send": String Timestamp (Formated in ISO 8601),
    "sent_at": String Timestamp (Formated in ISO 8601),
    "message": String
    "scheduled_dose_id": Integer,
    "notification_policy_id": Integer
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint deletes a single specific notification

### HTTP Request

`DELETE https://api.mevia.com/v1/notifications/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
ID        | Integer | ID of the notification to delete
