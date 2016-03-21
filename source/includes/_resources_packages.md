# Packages
These methods are used to show what packages has been generated.

## Get all packages from a Prescription

> Response structure:

```json
{
  "packages": [
    {
      "id": Integer,
      "created_at": String Timestamp (Formated in ISO 8601),
      "is_current": boolean,
      "number": Integer,
      "nr_of_taken_pods": Integer,
      "links": {
        "taken_pods": [Integer],
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

This endpoint retrieves all packages belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:id/packages`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Get specific packages from a Prescription

> Response structure:

```json
{
  "packages": [
    {
      "id": Integer,
      "created_at": String Timestamp (Formated in ISO 8601),
      "is_current": boolean,
      "number": Integer,
      "nr_of_taken_pods": Integer,
      "links": {
        "taken_pods": [Integer],
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

This endpoint retrieves specific packages belonging to the given prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:id/packages/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1,id2,id3...| IDs of the packages to show