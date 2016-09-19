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
      "description": String,
      "prescription_id": Integer
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

`GET https://api.mevia.com/v1/flags?having_flag_type=example_flag_type,other_example_type&offset=0&limit=20`

### Query Parameters
Parameter        | Format         | Description
---------        | -------        | -----------
offset           | Integer        | Number of flags to offset with. Used for pagination
limit            | Integer        | Maximum number of flags to fetch.
having_flag_type | type_1,type_2  | Flag types to fetch


## Get all flags for prescription

> Response structure:

```json
{
  "flags": [
    {
      "id": String,
      "flag_type": String,
      "severity": Integer,
      "description": String,
      "prescription_id": Integer
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
Parameter        | Format        | Description
---------        | -------       | -----------
prescription_id  | Integer       | ID of the prescription
offset           | Integer       | Number of flags to offset with. Used for pagination
limit            | Integer       | Maximum number of flags to fetch.
having_flag_type | type_1,type_2 | Flag types to fetch


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
      "description": String,
      "prescription_id": Integer
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
Parameter        | Format        | Description
---------        | -------       | -----------
prescription_id  | Integer       | ID of the prescription
id               | id1, id2, id3 | ids of the flags to fetch
offset           | Integer       | Number of flags to offset with. Used for pagination
limit            | Integer       | Maximum number of flags to fetch.
having_flag_type | type_1,type_2 | Flag types to fetch

<aside class="success">
To find out what flag types are available, please see flag_types section of this documentation
</aside>