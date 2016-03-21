# Flag Policies
The following resources are used to flag policies. A flag policy is used to monitor a specific type of flag.

## Get all flag policies

> Response structure:

```json
{
  "flag_policies": [
    {
      "id": Integer,
      "flag_type": String,
      "message": String,
      "links": {
        "recipients": [
          id1, id2, id3...
        ]
      }
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint retrieves all flag policies for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/flag_policies`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

<aside class="success">
To see what flag types are available, please see flag types section of this documentation
</aside>

## Get specific flag policies

> Response structure:

```json
{
  "flag_policies": [
    {
      "id": Integer,
      "flag_type": String,
      "message": String,
      "links": {
        "recipients": [
          id1, id2, id3...
        ]
      }
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint retrieves specified flag policies for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/flag_policies/id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | ids of the flag policies to fetch

<aside class="success">
To see what flag types are available, please see flag types section of this documentation
</aside>

## Delete specific flag policies

This endpoint deletes the specified flag policies

### HTTP Request

`DELETE https://api.mevia.com/v1/prescription/:prescription_id/flag_policies/id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | ids of the flag policies to delete

<aside class="success">
To see what flag types are available, please see flag types section of this documentation
</aside>

## Create a flag policy

> Request structure:

```json
{
  "flag_policies": {
    "flag_type": String,
    "message": String,
    "links": {
      "recipients": [
        {"phone": String,
         "email": String},
        .
        .
        .
      ]
    }
  }
}
```

> Response structure:

```json
{
  "flag_policies": [
    {
      "id": Integer,
      "flag_type": String,
      "message": String,
      "links": {
        "recipients": [
          id1, id2, id3...
        ]
      }
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint creates a flag policy for the specified prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescription/:prescription_id/flag_policies`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

<aside class="success">
To see what flag types are available, please see flag types section of this documentation
</aside>

## Update a flag policy

> Request structure:

```json
{
  "flag_policies": {
    "flag_type": String
    "message": String
  }
}
```

> Response structure:

```json
{
  "flag_policies": [
    {
      "id": Integer,
      "flag_type": String,
      "message": String,
      "links": {
        "recipients": [
          id1, id2, id3...
        ]
      }
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint updates a flag policy for the specified prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/prescription/:prescription_id/flag_policies/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1           | ID of the flag policy to update

<aside class="success">
To see what flag types are available, please see flag types section of this documentation
</aside>