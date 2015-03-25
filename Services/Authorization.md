# Authorization

## Intent

The authorization service main intent is to specify access rights to resources.

## Also Known As

* Access control lists (ACL)

## Collaborators

* [Authentication](Authentication.md)
* [Data source](Data source.md)

## Collaboration

### Authentication

Authorization generally starts with authentication, that is, a user must prove he's a specific account within the system. Then, roles and permissions are assigned to this account.

### Data source

As a system is bound to grow, the addition of new users means giving roles and permissions to those accounts. This information will most likely end up living in a database which will be queried when the system needs to verify that an account has the required authorization to perform a certain task.

## Implementation

The implementation of authorization can come in many flavors. The level of feature one may provide can vary greatly and will directly influence the complexity of the authorization system.

* The system must be able to query the authorization of an account.
	* The system must be able to query an account groups/roles.
	* The system must be able to query an account permissions.
* The system must be able to get the list of existing groups/roles.
* The system must be able to get the list of existing permissions.
* An administrator should be able to assign one or multiple group(s)/role(s) to an account.
* An administrator should be able to add new groups/roles.
* An administrator should be able to edit groups/roles attached permissions.
* An administrator should be able to delete groups/roles.

## Known Uses

* Resource based access control
* Group/Role based authorization
* Permission based authorization
* Group/Role/Permission based authorization

## Related Services

### Routing/Filtering

It is common to have authorization at the route level. This means that a user will be allowed or denied access to a certain URL based on no more information than the URL/route and the authenticated user and his authorization.

## Sources

* https://en.wikipedia.org/wiki/Authorization_(computer_access_control)

## Todo

* Describe groups/roles - permissions interactions
* Hierarchical groups/roles/permissions systems