# Flag Policies
The following resources are used to flag policies. A flag policy is used to monitor a specific type of <a href='/#flag-types'>event</a> in the system, and generates a <a href='#flags'>flag</a> for every occurrence.

## Get all flag policies

> Response structure:

```json
{
    "data": [
        {
            "id": Integer,
            "type": "flag_policies",
            "attributes": {
                "flag_type": String,
                "message": String
                "prescription_id": Integer
            }
        }
    ],
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

This endpoint retrieves all flag policies for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/flag_policies`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

## Get specific flag policies

> Response structure:

```json
{
    "data": {
        "id": Integer,
        "type": "flag_policies",
        "attributes": {
            "flag_type": String,
            "message": String
            "prescription_id": Integer
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
}```

This endpoint retrieves a single specified flag policy.

### HTTP Request

`GET https://api.mevia.com/v1/flag_policies/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | id      | id of the flag policy to fetch

## Delete specific flag policies

This endpoint deletes the specified flag policy

### HTTP Request

`DELETE https://api.mevia.com/v1/flag_policies/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | id      | id of the flag policy to delete

## Create a flag policy

> Request structure:

```json
{
  "flag_policies": {
    "flag_type": String,
    "message": String
  }
}
```

> Response structure:

```json
{
    "data": {
        "id": Integer,
        "type": "flag_policies",
        "attributes": {
            "flag_type": String,
            "message": String
            "prescription_id": Integer
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

This endpoint creates a flag policy for the specified prescription.

### HTTP Request

`POST https://api.mevia.com/v1/prescription/:prescription_id/flag_policies`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

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
    "data": {
        "id": Integer,
        "type": "flag_policies",
        "attributes": {
            "flag_type": String,
            "message": String
            "prescription_id": Integer
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

This endpoint updates a flag policy for the specified prescription.

### HTTP Request

`PUT https://api.mevia.com/v1/flag_policies/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | id      | ID of the flag policy to update