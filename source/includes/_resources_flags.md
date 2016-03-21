# Flags
The following resources are used to fetch flags. Flags are created automatically in response to various events occurring in the system. In order to register as a listener to a certain flag, users should use flag policies, described separatly in this document. To find what flags exists currently, please read the flag_types section of this documentation.

## Get all flags

> Response structure:

```json
{
  "flags": [
    {
      "id": String,
      "flag_type": String,
      "severity": Integer,
      "description": String
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint retrieves all flags for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/flags`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

<aside class="success">
To find out what flag types are available, please see flag_types section of this documentation
</aside>

## Get specific flags

> Response structure:

```json
{
  "flags": [
    {
      "id": String,
      "flag_type": String,
      "severity": Integer,
      "description": String
    }
  ],
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint retrieves specified flags for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/flags/id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1, id2, id3 | ids of the flags to fetch

<aside class="success">
To find out what flag types are available, please see flag_types section of this documentation
</aside>