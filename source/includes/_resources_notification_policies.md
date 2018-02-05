# Notification Policies
These methods are used handle Notification Policies, used for generating a notifications related to dose schemas.

## Get all notification policies

> Response structure: (To see all available notification types, please look at <a href='/#notification-types'>that</a> section of this documentation.)

```json
{
    "data": [
      {
          "id": Integer,
          "type": "notification_policies",
          "attributes": {
              "trigger": String,
              "message": String,
              "offset": Integer,
              "audio_src": String,
              "prescription_id": Integer,
              "notification_type": String
          }
      }
    ]
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

This endpoint retrieves all notification policies belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Get a specific notification policy

> Response structure: (To see all available notification types, please look at <a href='/#notification-types'>that</a> section of this documentation.)

```json
{
    "data": [
      {
          "id": Integer,
          "type": "notification_policies",
          "attributes": {
              "trigger": String,
              "message": String,
              "offset": Integer,
              "audio_src": String,
              "prescription_id": Integer,
              "notification_type": String
          }
      }
    ]
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

This endpoint retrieves specific notification policies belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/notification_policies/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ID of the notification policy to fetch

## Create a Notification Policy

> Request structure: (To see all available notification types, please look at <a href='/#notification-types'>that</a> section of this documentation.)

```json
{
  "notification_policy": {
    "notification_type": String,
    "message": String,
    "minutes": Integer,
    "audio_src": String,
    "voice_notification": Boolean
  }
}
```

> Response structure: (To see all available notification types, please look at <a href='/#notification-types'>that</a> section of this documentation.)

```json
{
    "data": {
        "id": Integer,
        "type": "notification_policies",
        "attributes": {
            "trigger": String,
            "message": String,
            "offset": Integer,
            "audio_src": String,
            "prescription_id": Integer,
            "notification_type": String
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

This endpoint creates a notification policy under the specified prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies`

### Query Parameters
Parameter       | Format  | Description
---------       | ------- | -----------
prescription_id | Integer | ID of the prescription

## Update a Notification Policy

> Request structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policy": {
    "notification_type": String,
    "message": String,
    "minutes": Integer,
    "audio_src": String,
    "voice_notification": Boolean
  }
}
```

> Response structure: (To see all available triggers, please look at <a href='/#triggers'>that</a> section of this documentation.)

```json
{
    "data": {
        "id": Integer,
        "type": "notification_policies",
        "attributes": {
            "trigger": String,
            "message": String,
            "offset": Integer,
            "audio_src": String,
            "prescription_id": Integer,
            "notification_type": String
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

Update a single notification policy

### HTTP Request

`PUT https://api.mevia.com/v1/notification_policies/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
id              | Integer       | ID of the notification policy to update

## Delete a Notification Policy

> Response structure: (To see all available notification types, please look at <a href='/#notification-types'>that</a> section of this documentation.)

```json
{
    "data": {
        "id": Integer,
        "type": "notification_policies",
        "attributes": {
            "trigger": String,
            "message": String,
            "offset": Integer,
            "audio_src": String,
            "prescription_id": Integer,
            "notification_type": String
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

This endpoint deletes a notification policy belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/notification_policies/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ID of the notification policy to delete