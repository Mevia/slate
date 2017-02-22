# Releases

## Development - 1.9.0

## Staging - 1.8.0

## Production - 1.8.0

### Shallow scopes
All resources under v1/ are now as shallow as at all possible. Scoping is only required for POST and GET(index).

### Singular/plural naming
Resources fetched using SHOW, POST, PUT or DELETE will now use singular naming.

### Common filters
All index calls now share some common filters. Available (for all index routes) filters are:
* sort_by
* direction
* offset
* limit
