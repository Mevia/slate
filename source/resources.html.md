---
title: Resources REST API

language_tabs:
  - json: JSON

toc_footers:
  - <a href='www.mevia.se'>Mevia</a>
  - <a href='/'>Main page</a>

includes:
  - resources_prescriptions
  - resources_mia_modules
  - resources_events
  - resources_packages
  - resources_scheduled_doses
  - resources_scheduled_dose_schemas
  - resources_notification_policies
  - resources_notifications
  - resources_recipients
  - resources_taken_pods
  - resources_flags
  - resources_flag_policies

search: true
---
# Resources


> Api Endpoint

The API aims to take care of all data related to the MIA module itself, which is sending and receiving information from modules. Developers that use the API can, for instance, obtain all events from a module for a given patient, or register a prescription for a patient which then automatically will set reminders and other logic that interacts with the patient's mobile phone.

```
https://api.mevia.com/v1/
```

The purpose of this setup is that API users will be able to concentrate on their business logic, henceforth not on how the modules work, which is abstracted away through the API. A benefit of this is also that, if the physical module changes, then there will be no impact on API users due to this abstraction.


## Authentication and security

> Example of how header should look:

All API calls are done via HTTPS requests, which means that all data obtained and retrieved from the API is delivered through an encrypted connection. Moreover, an API key must be sent with each request in order to authorize with the API. The key is used to idenfify which user that is connecting to the API and is initially handed out manually by Mevia.

In order to authorize with the API, the API key must be sent with each request as a request parameter in the request header.

```json
Authorization: Token token="API KEY"
```

> This means that the parameter name is 'Authorization' and the parameter value is 'Token token="API KEY"'.

## Versioning

### Major Versions(<span class="red-text">x</span>.y.z)

The major versions will be seperated through API url namespaces, e.g.
https://api.mevia.se/v1/:resource and https://api.mevia.se/v2/:resource

Each major version will be supported as long as API users make use of it.

### Minor Versions(x.<span class="red-text">y</span>.z)

Includes new requirements, improvements and changes that does not affect API users and their interface with the resources they use. The API might add functionality, but does not change or remove existing API resources.

If an API resource is going to change or be removed, it will be marked as "depricated" long enough for API users to adapt, not breaking any functionality during the transition period for API users.

### Bug Fixes(x.y.<span class="red-text">z</span>)

Includes bug fixes that doesn't change or functionality to the API, only fix behaviour so it works as expected to.
