# Sequencing

> Example JSON when posting (creating) prescription:

```json
{
  "prescriptions":{
    "start_date":"2015-01-01",
    "end_date":"2015-03-01",
    "pod_sequence": "[1,2,3,4]"
  }
}
```

When creating prescriptions, the API user has the option to create scheduled doses according to a package pod sequence. This means that the patient must take their pods according to a specific sequence on the package (tray), which is represented by numbers. The API, as well as the modules, can handle any kind of sequencing pattern.

## Practical assumptions when using sequencing

> Example JSON when retrieving schedule dose which is based on the prescription above:

* When taking wrong pods in a sequence, or missing dose completely, the patient moves on to the next set of pods to take for next dose at the next time slot. This means that pods can be untaken when finishing a tray. This does not affect module dose planning, which is very important e.g. for reused modules with set date intervals.
* If no sequence is specified for prescriptions and no expected pods are given for scheduled doses, then any pod can be taken at any dose time interval in order to complete them. This is the default behavior.

```json
{
    "data": [
        {
            "id": "478",
            "type": "scheduled_doses",
            "attributes": {
                "period_starts_at": "2016-09-19T11:00:00.000Z",
                "period_ends_at": "2016-09-19T12:00:00.000Z",
                "taken": false,
                "completed_at": null,
                "nr_remaining_pods": 1,
                "expected_pods": "[13]",
                "muted": false,
                "nr_remaining_pods_until_mute": 1,
                "prescription_id": 9,
                "scheduled_dose_schema_id": 17
            }
        },
        {
            "id": "1315",
            "type": "scheduled_doses",
            "attributes": {
                "period_starts_at": "2016-09-14T09:00:00.000Z",
                "period_ends_at": "2016-09-14T10:00:00.000Z",
                "taken": false,
                "completed_at": null,
                "nr_remaining_pods": 1,
                "expected_pods": "[0]",
                "muted": true,
                "nr_remaining_pods_until_mute": -1,
                "prescription_id": 9,
                "scheduled_dose_schema_id": 19
            }
        },
        {
            "id": "1345",
            "type": "scheduled_doses",
            "attributes": {
                "period_starts_at": "2016-09-14T11:00:00.000Z",
                "period_ends_at": "2016-09-14T12:00:00.000Z",
                "taken": true,
                "completed_at": "2016-09-14T11:51:40.000Z",
                "nr_remaining_pods": 0,
                "expected_pods": "[1]",
                "muted": true,
                "nr_remaining_pods_until_mute": 0,
                "prescription_id": 9,
                "scheduled_dose_schema_id": 20
            }
        },
        {
            "id": "1316",
            "type": "scheduled_doses",
            "attributes": {
                "period_starts_at": "2016-09-15T09:00:00.000Z",
                "period_ends_at": "2016-09-15T10:00:00.000Z",
                "taken": false,
                "completed_at": null,
                "nr_remaining_pods": 1,
                "expected_pods": "[2]",
                "muted": true,
                "nr_remaining_pods_until_mute": -1,
                "prescription_id": 9,
                "scheduled_dose_schema_id": 19
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
