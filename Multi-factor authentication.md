
# Multi-Factor Authentication

## Two-Factor Authentication
### Briefly Take a Look at What Two-Factor Authentication Means.
It is based on the following flow:
1. User is asked to enter its credentials
	--> If it is correct
2. User is asked to enter a specific code (one time password)
	--> If it is correct 
3. User is logged in 

## Approaches to Multifactor Authentication
MFA can be used in a variety of ways depending on the desired balance between security and usability.

### Always On Approach
Even if the user is already logged in (after confirm its identity via two or more factors of authentication) each access to sensitive data or another login the user will be prompted to verify its identity again.

### Opt in Approach

### Step-up Authentication
Depending on what kind of operation the user is trying to perform. The user can be prompted for additional factors to identify itsel, thus stepping up from one factor to two or more.

### Time-sensitive Re-verification
In this case, the user logs on for the first time with two or more factors so that MFA is established from the beginning. If the user continues to use the same browser and a trusted device, however, it may be unnecessary for the user to go through this entire process again for an extended period of time. 

After sometime, the user will be asked to verify his identity again.

## References
[How TOTP Works]https://www.freecodecamp.org/news/how-time-based-one-time-passwords-work-and-why-you-should-use-them-in-your-app-fdd2b9ed43c3/
