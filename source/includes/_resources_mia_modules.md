# Mia Modules
The following resources explains basic interaction with MIA Modules.

## Get All mia modules

> Response structure:

```json
{
  "mia_modules": [
    {
      "id": Integer,
      "is_connected_to_package": Boolean,
      "module_number": String,
      "battery_percentage": Integer,
      "name": String,
      "prescription_id": Integer,
      "firmware_file_name": String
    }
  ],
   "meta": {...}
}
```

This endpoint retrieves all Mia Modules belonging to the current user.

### HTTP Request

`GET https://api.mevia.com/v1/mia_modules`

### Query Parameters
No available parameters apart from the ones <a href='##shared-attributes-among-all-resources'>shared</a> by all index resources

## Get specific mia module

> Response structure:

```json
{
  "mia_modules": {
    "id": Integer,
    "is_connected_to_package": Boolean,
    "module_number": String,
    "battery_percentage": Integer,
    "name": String,
    "prescription_id": Integer,
    "firmware_file_name": String
  },
  "meta": {...}
}
```

This endpoint retrieves a single specific mia module.

### HTTP Request

`GET https://api.mevia.com/v1/mia_modules/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ID of the mia module to show.

## Get all modules from a prescription

> Response structure:

```json
{
  "mia_modules": [
    {
      "id": Integer,
      "is_connected_to_package": Boolean,
      "module_number": String,
      "battery_percentage": Integer,
      "name": String,
      "prescription_id": Integer,
      "firmware_file_name": String
    }
  ]
}
```

This endpoint retrieves all Mia Modules belonging to the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/mia_modules/`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription

## Delete mia module

This endpoint deletes the specified Mia Module. This action unlocks the module numbers for use on other API users.

### HTTP Request

`DELETE https://api.mevia.com/v1/mia_modules/:id`

### Query Parameters
Parameter | Format  | Description
--------- | ------- | -----------
id        | Integer | ID of the mia module to delete