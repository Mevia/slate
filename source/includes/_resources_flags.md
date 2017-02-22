# Flags
The following resources are used to fetch flags. Flags are created automatically in response to various events occurring in the system. In order to register as a listener to a certain flag, users should use <a href='#flag-policies'>flag policies</a>. To find what flags exists currently, please read the <a href='/#flag-types'>flag types</a> section of this documentation.

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
    },
    "paging": {
      "limit": Integer,
      "offset": Integer,
      "count": Integer
    }
  }
}
```

This endpoint retrieves all flags filtered by flag type, with both offset and limit

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
having_flag_type | type_1,type_2 | Flag types to fetch

## Get specific flag

> Response structure:

```json
{
  "flag": {
    "id": String,
    "flag_type": String,
    "severity": Integer,
    "description": String,
    "prescription_id": Integer
  },
  "meta": {
    "API": {
      "version": String
    }
  }
}
```

This endpoint retrieves a single specified flag.

### HTTP Request

`GET https://api.mevia.com/v1/flags/id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ids of the flags to fetch
