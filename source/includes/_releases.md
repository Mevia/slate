# Releases

## Development - 1.7.0

### Notification muting for non-sequence scheduled doses
If a pill is taken between the a missed dose interval and its notification, that notification will now be muted.

### Ability to filter prescriptions by active status
Prescriptions can now be filtered by active. An active prescription is one that is within its module_activity interval

## Staging - 1.6.0

## Production - 1.6.0

### Datetimes to prescriptions
Prescriptions now have two new fields - starts_at and ends_at, both beeing datetimes. The old variables start_date and end_date are still available. Setting start_date=2015-05-05 will behave exactly like setting starts_at=2015-05-05 00:00:00, and setting end_date=2015-05-05 will behave exactly like setting ends_at=2015-05-05 23:59:59. Internally, this is exactly what happens as well.

### Soft deletes of prescriptions
Prescriptions deleted will still be stored in the Mevia Database. Resources deleted by the delete-call will be saved as well. As of now, to restore any data, contact Mevia.

### Offsets
Any call to Mapi fetching more than one resource can now be offset by setting the offset parameter in the call.

### Limits
Any call to Mapi fetching more than one resource can now be limited by setting the limit parameter in the call.

### Filters added
Resources with internal dates can now be filtered using date_from and date_to (can be dates or datetimes)

### Orders
Resources fetched through Mapi can be now ordered by any available attribute.

### RESTful doses
Doses can now be created without using a dose schema. Doses can be batch-created by sending a array of doses rather than a single resource. WARNING: Using both a dose schema and individual doses is not recommended when using expected pods.

### Mia Modules are now independant from Prescriptions
Mia Modules no longer need a link to a prescription. Having a module that does not rely on a single prescription allows for fetching all events sent by a given module, as well as updating parameters of a module without having to redo the update every time the module changes user. This update contains a few new available resources under mia_modules.

### Ability to 'sign in' to user using name and password
A new resource is available under api_user: login. The route simply returns the specified (by name) api_user together with all linked api_keys. This allows for fetching api_keys programmatically. By default, a user has no password, and can not use this feature. In order to set a password on a given user, contact us at Mevia.
