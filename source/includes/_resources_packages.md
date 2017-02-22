# Packages
These methods are used to show what packages have been generated.

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
      "mia_module_id": Integer,
      "prescription_id": Integer
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

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/packages`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Get all packages from a Mia module

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
      "mia_module_id": Integer,
      "prescription_id": Integer
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

`GET https://api.mevia.com/v1/mia_modules/:mia_module_id/packages`

### Query Parameters
Parameter     | Format  | Description
---------     | ------- | -----------
mia_module_id | Integer | ID of the mia module


## Get a specific package

> Response structure:

```json
{
  "package": {
    "id": Integer,
    "created_at": String Timestamp (Formated in ISO 8601),
    "is_current": boolean,
    "number": Integer,
    "nr_of_taken_pods": Integer,
    "mia_module_id": Integer,
    "prescription_id": Integer
  },
  "meta": {
    "API": {
      "version": "1.4.0"
    }
  }
}
```

This endpoint retrieves a single specific package.

### HTTP Request

`GET https://api.mevia.com/v1/packages/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
ID        | Integer | ID of the package to show