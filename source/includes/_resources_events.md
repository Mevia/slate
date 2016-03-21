# Events
The following resources are used to obtain events from MIA modules. An event is a status update on a module, e.g. if a pill is taken, a packaged is removed etc.

## Get all events

> Response structure:

```json
{
  "events": [
    {
      "id": Integer,
      "timestamp": String Timestamp (Formated in ISO 8601),
      "event_type": String,
      "taken_pods": [Integer1, Integer2...],
      "newly_taken_pods": [Integer],
      "battery_percentage": Integer,
      "raw_module_number": String,
      "module_message_id": String,
      "module_timestamp": String Timestamp (Formated in ISO 8601),
      "module_sequence_number": Integer,
      "module_repeated_attempts": Integer,
      "module_network_quality": Integer,
      "module_network_type": String
    },
    .
    .
  ],
  "meta":{
     "API":{
        "version": String
     }
  }
}
```

This endpoint retrieves all events for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/events`

### Query Parameters
Parameter       | Format    | Description
---------       | -------   | -----------
prescription_id | Integer   | ID of the prescription

## Get specific events

> Response structure:

```json
{
  "events": [
    {
      "id": Integer,
      "timestamp": String Timestamp (Formated in ISO 8601),
      "event_type": String,
      "taken_pods": [Integer1, Integer2...],
      "newly_taken_pods": [Integer],
      "battery_percentage": Integer,
      "raw_module_number": String,
      "module_message_id": String,
      "module_timestamp": String Timestamp (Formated in ISO 8601),
      "module_sequence_number": Integer,
      "module_repeated_attempts": Integer,
      "module_network_quality": Integer,
      "module_network_type": String
    },
    .
    .
  ],
  "meta":{
     "API":{
        "version": String
     }
  }
}
```

This endpoint retrieves specific events for the specified prescription.

### HTTP Request

`GET https://api.mevia.com/v1/prescription/:prescription_id/events/:id`

### Query Parameters
Parameter       | Format     | Description
---------       | -------    | -----------
prescription_id | Integer    | ID of the prescription
id              | id1, id2...| IDs of the events to fetch