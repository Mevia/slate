---
title: Resources REST API

language_tabs:
  - json: JSON

toc_footers:
  - <a href='http://www.mevia.se'>Mevia</a>
  - <a href='/'>Main page</a>

includes:
  - resources_prescriptions
  - resources_mia_modules
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

# Shared attributes among all resources


> Shared among all responses:

```json
{
  ...,
  "meta": {
    "API": {
      "version": String
    },
    "paging": { // When limit/offset filters are applied
      "count": Integer,
      "offset": Integer,
      "limit": Integer
    }
  }
}
```

All index fetching resources allows for some common arguments:

Parameter | Format  | Description
--------- | ------- | -----------
limit     | Integer | Maximum number of resources to fetch
offset    | Integer | Index of where to start fetching resources with specified filters applied
sort_by   | String  | Attribute to sort by
direction | String  | Direction to sort. Can be only 'asc' or 'desc'.

If limit or offset is used as a argument, a paging header will be included in the meta-data. This header will include:
limit: specified limit, offset: specified offset, count: number of resources available with applied filters