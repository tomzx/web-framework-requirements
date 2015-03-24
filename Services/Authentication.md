# Authentication

## Intent

The authentication service main intent is to confirm that a certain identifier is possessed by a particular user. Authentication can be done through various means, such as a *username* (identifier) and *password*  (confirmation of ownership) combination.

## Also Known As

*No known alias at the moment.*

## Collaborators

* [Data source](Data source.md)
* [Email](Email.md)
* [Hashing](Hashing.md)

## Collaboration

### Data source

In general, the authorization service will need to query a data source in order to authenticate a user. This generally means selecting the user data that matches the credentials given by the user, if it exists.

### Email

The email service will generally be involved as part of the user's registration and forgot password process.

In the case in which there is no email data available for the authenticated users, the email service will be of no use to authentication.

### Hashing

The hashing service main involvement with authentication has to do with user password hashing.

It is preferred for user passwords to be hashed over being encrypted. Encryption being reversible by nature, if an attacker gains access to the encryption key, all passwords are susceptible to being decrypted. Hashing on the other hand is not reversible. If you wish to know what password generated a specific hash, you will have to compute a large amount of data to do so.

## Implementation

* User (Source of user information)
	* Id
	* *Username*
	* Password
	* *State (Pending, Active, Suspended, Banned)*
* Reset (List of password reset requests)
	* User.Id
	* Token
	* Created At
* Attempt (List of unsuccessful authentication attempts)
	* User.Id
	* Timestamp

* A user must be able to authenticate himself through at least a single piece of information.
	* The constraints used to uniquely identify an account should be configurable.
		* Whether you want email + password, or username + password or simply a password, all option should be supported.
* A user should be able to activate his account if said account is linked to external authentication sources, such as an email address (to prove that the user is truly the owner of the provided email account).
* A administrator should be able to suspend/ban a account if the user's behavior goes against the system's policies.
* The system should throttle user authentication attempts in order to prevent brute forcing.
* The system should allow the user to reset his password when the user forgets his.

## Known Uses

* Login systems

## Related Services

### Authorization

Authorization often goes hand in hand with authentication as they both deal with a specific user. Whereas authentication deals with confirming that a specific client is a specific user within the system, authorization deals with what this user is allowed to do within its boundaries.

## Sources

* https://en.wikipedia.org/wiki/Authentication
* https://github.com/Zizaco/confide
* https://github.com/cartalyst/sentry