# Event types
This is the supported event types that MIA modules sends to the API from the attached packages. All events contains information regarding the current battery state of its module.

> Example of an intake event.

```json
{
"id": "1",
"timestamp": "2015-05-11T09:39:40.000Z",
"event_type": "INTAKE",
"taken_pods": "[1, 2]",
"newly_taken_pods": "[1, 2]",
"battery_percentage": 100,
"raw_module_number": "123456789",
"module_message_id": "f5baTB1",
"module_timestamp": "2015-05-11T10:55:37.000Z",
"module_sequence_number": 1,
"module_repeated_attempts": 1,
"module_network_quality": 1,
"module_network_type": "home"
}
```

Type                    | Description                                                                                    | When is it sent?
----                    | -----------                                                                                    | ----------- 
STARTUP                 | Module has been switched on.                                                                   | Only when system starts.
STARTUP_NO_PACKAGE      | Module was started without a package                                                           | On startup if no package.
PACKAGE_INSERT_FULL     | Tells that a full package is inserted to module.                                               | When new package is inserted.
PACKAGE_INSERT_NON_FULL | Tells that a non-full package is inserted to module.                                           | When new package is inserted.
PACKAGE_INSERT_EMPTY    | Tells that an empty package is inserted to module.                                             | When new, empty package is inserted.
PACKAGE_REMOVE          | Tells that the package was removed.                                                            | When package is removed from module.
INTAKE                  | Dose(s) taken from package. Gives one or several integers depending on which doses are taken.  | Change in dose status.
HEARTBEAT               | Module is giving a sign that it is alive and functional.                                       | Happens on a set interval (set in module) each day. 