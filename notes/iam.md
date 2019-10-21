# IAM

Identity and Access Management, i.e. users.

* Users: usually a physical person.
* Groups: Functions (admins, devops) or teams (engineering, design). Groups contain users.
* Roles: Internal usage within AWS resources **for machines**.

Root account should never be uesd (and shared).

Permissions are governed by policies (JSON).

IAM has predefined managed policies so the policy doesn't need to be written by hand.

* One IAM user per physical person.
* One IAM role per application.
* IAM credentials should never be shared.
* Never ever write IAM credentials in code. Ever.
* Never commit your IAM credentials.
* Never use the root account except for the initial setup.

It's recommended to follow some best practices for access security.

1. After creating your AWS account with root, activate MFA on the root account. Use Google Authenticator.
2. Create an individual IAM user for yourself. Do all work from this account.
3. Create groups and add users to groups. Manage permissions from the groups as it's easier to administer.
4. Apply an IAM password policy (i.e. must have uppercase and lowercase, no reusing the same passwords).

## IAM Federation

Big enterprises usually integrate their own repository of users with IAM. This way, one can log in to AWS using their company credentials. It uses the SAML standard (Active Directory).