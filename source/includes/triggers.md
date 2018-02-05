# Notification Triggers
This is a list of all existing notification trigger. A trigger is set on a notification policy, and is used to know when to create notifications.

Type                  | Description                                      | When is the notification sent?
----                  | -----------                                      | -----------
BEFORE_DOSE_STARTS    | Used to create notifications before doses starts| x minutes before the doses start, where x is the offset variable on the notification policy
BEFORE_DOSE_ENDS      | Used to create notifications before doses ends  | x minutes before the doses start, where x is the offset variable on the notification policy
AFTER_DOSE_END        | Used to create notifications after doses ends   | x minutes before the doses ends, where x is the offset variable on the notification policy

Example: A notification policy with trigger: 'BEFORE_DOSE_ENDS' and offset: 15, and a scheduled_dose_schema with start_time: '10:00' and end_time: '11:00' will generate a notification that is scheduled to be sent at 10:45 every day that its prescription is active.