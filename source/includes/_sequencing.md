# Sequencing

> Example JSON when posting (creating) prescription:

```json
{
  "prescriptions":{
    "start_date":"2015-01-01",
    "end_date":"2015-03-01",
    "pod_sequence":[1,2,3,4]
  },
  "linked":{
    .
    .
    .
  }
}
```

When creating prescriptions, the API user has the option to create scheduled doses according to a package pod sequence. This means that the patient must take their pods according to a specific sequence on the package (tray), which is represented by numbers.

For example, the package with numbers can look as following:

<img src="images/horizontal-sequence.jpg" width="200">
<img src="images/vertical-sequence.jpg" width="200">

For the left package, the sequence is
<strong>[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28]</strong>

For the right package, the sequence is
<strong>[1,5,9,13,17,21,25,2,6,10,14,18,22,26,3,7,11,15,19,23,27,4,8,12,16,20,24,28]</strong>

This represents the order of which the pods should be taken (from left to right in the above arrays). The API user is not restricted to "horizontal" or "vertical" package sequences as shown above, this is just an example. The API user can insert any sequence in the packages/trays that can be taken, e.g. [1,3,5,7...] if the patient should take every second pod from left to right.

## Practical assumptions when using sequencing

> Example JSON when retrieving schedule dose which is based on the prescription above:

* When taking wrong pods in a sequence, or missing dose completely, the patient moves on to the next set of pods to take for next dose at the next time slot. This means that pods can be untaken when finishing a tray. This does not affect module dose planning, which is very important e.g. for reused modules with set date intervals.
* If no sequence is specified for prescriptions (pod_sequence == null) and no expected pods are given for scheduled doses, then any pod can be taken at any dose time interval in order to complete them. This is the default behavior.

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
      "expected_pods":[1,2,3],
      "links":{
        "prescription":"210"
      }
    },
    {
      "id":"4745",
      "period_starts_at":"2015-03-01T16:00:00.000+00:00",
      "period_ends_at":"2015-03-01T19:00:00.000+00:00",
      "is_taken":false,
      "completed_at":null,
      "nr_remaining_pods":1,
      "expected_pods":[4],
      "links":{
        "prescription":"210"
      }
    },
    {
      "id":"4746",
      "period_starts_at":"2015-03-01T20:00:00.000+00:00",
      "period_ends_at":"2015-03-01T22:00:00.000+00:00",
      "is_taken":false,
      "completed_at":null,
      "nr_remaining_pods":2,
      "expected_pods":[1,2],
      "links":{
        "prescription":"210"
      }
    }
  ]
}
```