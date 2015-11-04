# Recipients
These methods are used to set and remove receivers belonging to a prescription. Recipients are simply recievers of notifications.

## Get all recipients from a prescription 

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves all recipients for the specified prescription.

### HTTP Requests

`GET https://api.mevia.com/v1/prescription/:prescription_id/recipients`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

## Get all recipients from a notification policy

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves all recipients for the specified notification policy.

`GET https://api.mevia.com/v1/prescription/:prescription_id/notification_policies/:notification_policy_id/recipients`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_policy_id | Integer | ID of the notification policy

## Get all recipients from a notification

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves all recipients for the specified notification.

`GET https://api.mevia.com/v1/prescription/:prescription_id/notifications/:notification_id/recipients`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_id        | Integer | ID of the notification

## Get all recipients from a scheduled doses

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves all recipients for the specified scheduled dose.

`GET https://api.mevia.com/v1/prescription/:prescription_id/scheduled_doses/:scheduled_dose_id/recipients`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
scheduled_dose_id      | Integer | ID of the scheduled dose

## Get specific recipients from a prescription

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves specified recipients for the given prescription.

### HTTP Requests

`GET https://api.mevia.com/v1/prescription/:prescription_id/recipients/:id`

### Query Parameters
Parameter       | Format           | Description
---------       | -------          | -----------
prescription_id | Integer          | ID of the prescription
id              | id1, id2, id3... | IDs of the recipients to fetch

## Get specific recipients from a notification policy

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves specified recipients for the given notification policy.

`GET https://api.mevia.com/v1/prescription/:prescription_id/notification_policies/:notification_policy_id/recipients/:id`

### Query Parameters
Parameter              | Format           | Description
---------              | -------          | -----------
prescription_id        | Integer          | ID of the prescription
notification_policy_id | Integer          | ID of the notification policy
id                     | id1, id2, id3... | IDs of the recipients to fetch

## Get specific recipients from a notification

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves specified recipients for the given notification.

`GET https://api.mevia.com/v1/prescription/:prescription_id/notifications/:notification_id/recipients/:id`

### Query Parameters
Parameter              | Format           | Description
---------              | -------          | -----------
prescription_id        | Integer          | ID of the prescription
notification_id        | Integer          | ID of the notification
id                     | id1, id2, id3... | IDs of the recipients to fetch

## Get specific recipients from a scheduled dose

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

This endpoint retrieves specified recipients for the given scheduled dose.

`GET https://api.mevia.com/v1/prescription/:prescription_id/scheduled_doses/:scheduled_dose_id/recipients/:id`

### Query Parameters
Parameter              | Format           | Description
---------              | -------          | -----------
prescription_id        | Integer          | ID of the prescription
scheduled_dose_id      | Integer          | ID of the scheduled dose
id                     | id1, id2, id3... | IDs of the recipients to fetch

## Create a recipient to a notification policy
Creates a recipient and adds it to the specified notification policy. All notifications sent by this policy will be recieved by the recipient.

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests

`POST https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:notification_id/recipients`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_policy_id | Integer | ID of the notification policy

## Create a recipient to a notification
Creates a recipient and adds it to the specified notification. When the notification is sent the recipient will recieve it.

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`POST https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:notification_id/recipients`

### Query Parameters
Parameter              | Format  | Description
---------              | ------- | -----------
prescription_id        | Integer | ID of the prescription
notification_id        | Integer | ID of the notification

## Update a recipient through a prescription
Updates a recipient found through a prescription

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/recipients/:id`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription
id                | Integer | ID of the recipient

## Update a recipient through a scheduled dose
Updates a recipient found through a scheduled dose

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/recipients/:id`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription
id                | Integer | ID of the recipient
scheduled_dose_id | Integer | ID of the scheduled dose

## Update a recipient through a notification policy
Updates a recipient found through a notification policy

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:notification_policy_id/recipients/:id`

### Query Parameters
Parameter               | Format  | Description
---------               | ------- | -----------
prescription_id         | Integer | ID of the prescription
id                      | Integer | ID of the recipient
notification_policy_id  | Integer | ID of the notification policy

## Update a recipient through a notification
Updates a recipient found through a notification

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String,
    }
  ]
}
```

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`PUT https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:notification_id/recipients/:id`

### Query Parameters
Parameter       | Format  | Description
---------       | ------- | -----------
prescription_id | Integer | ID of the prescription
id              | Integer | ID of the recipient
notification_id | Integer | ID of the notification

## Delete a recipient from a prescription
Deletes a recipient found through a prescription

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/recipients/:id`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription
id                | Integer | ID of the recipient

## Delete a recipient from a scheduled dose
Deletes a recipient found through a scheduled dose

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/scheduled_doses/:scheduled_dose_id/recipients/:id`

### Query Parameters
Parameter         | Format  | Description
---------         | ------- | -----------
prescription_id   | Integer | ID of the prescription
id                | Integer | ID of the recipient
scheduled_dose_id | Integer | ID of the scheduled dose

## Delete a recipient from a notification policy
Deletes a recipient found through a notification policy

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/notification_policies/:notification_policy_id/recipients/:id`

### Query Parameters
Parameter               | Format  | Description
---------               | ------- | -----------
prescription_id         | Integer | ID of the prescription
id                      | Integer | ID of the recipient
notification_policy_id  | Integer | ID of the notification policy

## Delete a recipient from a notification
Deletes a recipient found through a notification

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String,
      "links": {
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

### HTTP Requests
`DELETE https://api.mevia.com/v1/prescriptions/:prescription_id/notifications/:notification_id/recipients/:id`

### Query Parameters
Parameter       | Format  | Description
---------       | ------- | -----------
prescription_id | Integer | ID of the prescription
id              | Integer | ID of the recipient
notification_id | Integer | ID of the notification

