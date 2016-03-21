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
      "links": {
        "mia_module_schedules": [id1, id2, id3...]
      }
    }
  ],
   "meta":{
      "API":{
         "version": String
      }
   }
}
```

This endpoint retrieves all Mia Modules belonging to the current user.

### HTTP Request

`GET https://api.mevia.com/v1/mia_modules`

### Query Parameters
No available parameters

## Get specific mia modules

> Response structure:

```json
{
  "mia_modules": [
    {
      "id": Integer,
      "is_connected_to_package": Boolean,
      "module_number": String,
      "battery_percentage": Integer,
      "links": {
        "mia_module_schedules": [id1, id2, id3...]
      }
    }
  ],
  "meta":{
     "API":{
        "version": String
     }
  }
}
```

This endpoint retrieves specific Mia Modules belonging to the current user.

### HTTP Request

`GET https://api.mevia.com/v1/mia_modules/:id`

### Query Parameters
Parameter | Format        | Description
--------- | -------       | -----------
id        | id1, id2...   | IDs of the mia modules to show.

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
      "links": {
        "mia_module_schedules": [id1, id2, id3...]
      }
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

## Get specific modules through a prescription.

> Response structure:

```json
{
  "mia_modules": [
    {
      "id": Integer,
      "is_connected_to_package": Boolean,
      "module_number": String,
      "battery_percentage": Integer,
      "links": {
        "mia_module_schedules": [id1, id2, id3...]
      }
    }
  ],
  "meta":{
     "API":{
        "version": String
     }
  }
}
```

This endpoint retrieves all specified Mia Modules belonging to the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescriptions/:prescription_id/mia_modules/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
prescription_id | Integer       | ID of the prescription
id              | id1,id2,id3...| IDs of the mia modules to show

## Delete 

This endpoint deletes the specified Mia Modules. This action unlocks the module numbers for use on other API users.

### HTTP Request

`DELETE https://api.mevia.com/v1/mia_modules/:id`

### Query Parameters
Parameter       | Format        | Description
---------       | -------       | -----------
id              | id1,id2,id3...| IDs of the mia modules to delete