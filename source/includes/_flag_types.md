# Flag types
This is a list of all flags that currently exists in the system. Flags are simply events occuring in the system that users can chose to be notified about.

Type                  | Description                                      | When is it sent?
----                  | -----------                                      | ----------- 
LOW_BATTERY           | A module is low on battery.                      | When a module has a battery status < 20%
SEQUENCE_ANOMALY      | A pod was taken in the wrong order               | When a patient takes a pod that is not the next expected pod
OUTSIDE_DOSE_INTERVAL | A pod was taken outside of any existing dose     | When a patient takes a pod outside of any existing scheduled dose
ADHERENCE_ANOMALY     | Someting went wrong from a adherence perspective | Whenever a adherence-related flag (currently: OUTSIDE_DOSE_INTERVAL and SEQUENCE_ANOMALY) is created.
DISCONNECTED_DEVICE   | A device was disconnected right before user dose started | ~30 minutes before start of a dose if user has a disconnected device
DELAYED_COMMUNICATION | A device failed to communicate for 24.5 hours or more. | Whenever a device has failed to communicate for an entire day (24 hours)