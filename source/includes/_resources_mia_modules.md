# Mia Modules
The following resources explains basic interaction with MIA Modules.

## Get All mia modules

> Response structure:

```json
{
    "data": [
        {
            "id": Integer,
            "type": "mia_modules",
            "attributes": {
                "is_connected_to_package": Boolean,
                "name": String (example: "GAA001"),
                "firmware_file_name": String,
                "prescription_id": Integer,
                "module_number": String,
                "battery_percentage": Integer
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

This endpoint retrieves all Mia Modules belonging to the current user.

### HTTP Request

`GET https://api.mevia.com/v1/mia_modules`

### Query Parameters
No available parameters apart from the ones <a href='##shared-attributes-among-all-resources'>shared</a> by all index resources

## Get specific mia module

> Response structure:

```json
{
    "data": {
        "id": Integer,
        "type": "mia_modules",
        "attributes": {
            "is_connected_to_package": Boolean,
            "name": String (example: "GAA001"),
            "firmware_file_name": String,
            "prescription_id": Integer,
            "module_number": String,
            "battery_percentage": Integer
        }
    }
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
    "data": [
        {
            "id": Integer,
            "type": "mia_modules",
            "attributes": {
                "is_connected_to_package": Boolean,
                "name": String (example: "GAA001"),
                "firmware_file_name": String,
                "prescription_id": Integer,
                "module_number": String,
                "battery_percentage": Integer
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