# Recipients
These methods are used to set and remove recipients. Recipients are simply receivers of notifications or flags.

## Get all recipients under a prescription

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String
    }
  ],
  "meta": {...}
}
```

This endpoint retrieves all recipients for the specified prescription.

### HTTP Requests

`GET https://api.mevia.com/v1/prescription/:prescription_id/recipients`

## Get all recipients from a notification policy

> Response structure:

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String
    }
  ],
  "meta": {...}
}
```

This endpoint retrieves all recipients for the specified notification policy.

`GET https://api.mevia.com/v1/notification_policies/:notification_policy_id/recipients`

## Get all recipients from a notification

```json
{
  "recipients": [
    {
      "id": String,
      "email": String,
      "phone": String
    }
  ],
  "meta": {...}
}
```

This endpoint retrieves all recipients for the specified notification.

`GET https://api.mevia.com/v1/notifications/:notification_id/recipients`

## Get specific recipients

> Response structure:

```json
{
  "recipient": {
    "id": String,
    "email": String,
    "phone": String
  },
  "meta": {...}
}
```

This endpoint retrieves a single specified recipient.

### HTTP Requests

`GET https://api.mevia.com/v1/recipients/:id`

## Create a recipient to a notification policy
Creates a recipient and adds it to the specified notification policy. All notifications sent by this policy will be recieved by the recipient.

> Request structure:

```json
{
  "recipients": [
    {
      "email": String,
      "phone": String
    }
  ]
}
```

> Response structure:

```json
{
  "recipient": {
    "id": String,
    "email": String,
    "phone": String
  },
  "meta": {...}
}
```

### HTTP Requests

`POST https://api.mevia.com/v1/notifications/:notification_id/recipients`

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
      "phone": String
    }
  ]
}
```

> Response structure:

```json
{
  "recipient": {
    "id": String,
    "email": String,
    "phone": String
  },
  "meta": {...}
}
```

### HTTP Requests
`POST https://api.mevia.com/v1/notifications/:notification_id/recipients`

## Update a recipient
Updates a single specified recipient

> Request structure:

```json
{
  "recipients": {
    "email": String,
    "phone": String,
  }
}
```

> Response structure:

```json
{
  "recipient": {
    "id": String,
    "email": String,
    "phone": String,
  },
  "meta": {...}
}
```

### HTTP Requests
`PUT https://api.mevia.com/v1/recipients/:id`

## Delete a recipient
Deletes a single specified recipient

> Response structure:

```json
{
  "recipients": {
    "id": String,
    "email": String,
    "phone": String
  },
  "meta": {...}
}
```
