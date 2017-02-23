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
  "scheduled_doses":[
    {
      "id":"4744",
      "period_starts_at":"2015-03-01T05:00:00.000+00:00",
      "period_ends_at":"2015-03-01T12:00:00.000+00:00",
      "is_taken":false,
      "completed_at":null,
      "nr_remaining_pods":3,
      "expected_pods":[1,2,3]
    },
    {
      "id":"4745",
      "period_starts_at":"2015-03-01T16:00:00.000+00:00",
      "period_ends_at":"2015-03-01T19:00:00.000+00:00",
      "is_taken":false,
      "completed_at":null,
      "nr_remaining_pods":1,
      "expected_pods":[4]
    },
    {
      "id":"4746",
      "period_starts_at":"2015-03-01T20:00:00.000+00:00",
      "period_ends_at":"2015-03-01T22:00:00.000+00:00",
      "is_taken":false,
      "completed_at":null,
      "nr_remaining_pods":2,
      "expected_pods":[1,2]
    }
  ]
}
```
