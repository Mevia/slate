# Notification Policies
These methods are used handle Notification Policies, used for generating a notifications related to dose schemas.

## Get all notification policies

> Response structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "id": Integer,
      "notification_type": String,
      "message": String,
      "minutes": Integer,
      "links": {
        "notifications": [id1, id2, id3...],
        "recipients": [id1, id2, id3...]
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

This endpoint retrieves all notification policies belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Get specific notification policies

> Response structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "id": Integer,
      "notification_type": String,
      "message": String,
      "minutes": Integer,
      "links": {
        "notifications": [id1, id2, id3...],
        "recipients": [id1, id2, id3...]
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

This endpoint retrieves specific notification policies belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | ID1, ID2, ID3 | IDs of the notification policies to fetch

## Create a Notification Policy

> Request structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "notification_type": String,
      "message": String,
      "minutes": Integer,
    }
  ]
}
```

> Response structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "id": Integer,
      "notification_type": String,
      "message": String,
      "minutes": Integer,
      "links": {
        "notifications": [id1, id2, id3...],
        "recipients": [id1, id2, id3...]
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

This endpoint creates a notification policy to the given prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Update a Notification Policy

> Request structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "notification_type": String,
      "message": String,
      "minutes": Integer,
    }
  ]
}
```

> Response structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "id": Integer,
      "notification_type": String,
      "message": String,
      "minutes": Integer,
      "links": {
        "notifications": [id1, id2, id3...],
        "recipients": [id1, id2, id3...]
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

This endpoint updates a notification policy belonging to the given prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | Integer       | ID of the notification policy to update

## Delete a Notification Policy

> Response structure: (To see all available notification types, please look at that section of this documentation.)

```json
{
  "notification_policies": [
    {
      "id": Integer,
      "notification_type": String,
      "message": String,
      "minutes": Integer,
      "links": {
        "notifications": [id1, id2, id3...],
        "recipients": [id1, id2, id3...]
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

This endpoint deletes a notification policy belonging to the given prescription.

### HTTP Request

`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | Integer       | ID of the notification policy to delete