# Version 3.2.2, 2022-10-23

## Fixes

* Remember the serial of the token that was used to authenticate to add the refill values to the right token, fixes #123
* If prefill_username is enabled, set the focus to the password field, fixes #122
* Update the offline info after wrong password or other errors. The number displayed will now represent the comsumed offline 	OTPs if they had not been refilled directly (e.g. machine is offline)
* Fixed the count field in the offline file to correctly display the count of OTPs

# Version 3.2.1, 2022-09-23

## Fixes
* Fixed a bug where an offline user would not be found if the username was capitalized differently (missing case insensitivity)
* When entering the wrong OTP in RDP scenarios, the credential provider will now reset to the first step with username and password prefilled. This way, the user just has to press enter and can trigger challenges again.
*Fixed a bug where the installer wrote the wrong values for scenario specific configuration


# Version 3.2.0, 2022-05-03

## Features
 * Multiple offline token for multiple users are possible now
 * Added "offline_threshold" configuration entry. OfflineRefill is only attempted when the remaining offline OTPs drop below the threshold. This will prevent having to wait for a connection timeout every time a authentication is performed where the computer is really offline.
 * Added "offline_show_info" configuration entry. This will display available offline token for the user that is currently logging.
 * Added "enable_filter" configuration entry. This will enable the filter (which removes all other Credential Providers).
 * Updated the installer with more configuration possibilities. Moreover, the filter is now always installed and has to be activated via the configuration of this Credential Provider.

## Fixes
 * When using RDP, the incoming password is now properly decrypted so that "2step_send_password" works correctly in this scenario.
 * Fixed a bug that could cause an infinite loop in the CredUI scenario.
 * Improved the "show_domain_hint" feature to directly show the domain that will be used when entering a backslash.
 * Entering '.\' will now be properly resolved to the local computer name.
 * Entering '@' will now be handled correctly to indicate a domain.
 * Failing the 2nd factor check in RDP scenarios will now only reset the 2nd step. In RDP scenarios, the username and password are already checked before connecting, therefore it is not required to check those on the target again.

# Version 3.1.2, 2021-06-09

## Features
 * Added "enable_reset" configuration setting to show a clickable text at the bottom that resets the login.
 * Added "debug_log" configuration setting to create a detailed log file. This setting replaces "release_log", real errors are always written to the log file. This setting also removes the need to install the debug version to create a detailed log.
 * Added status callback to WinHttp to get more detailed information about certain failures.
 
 ## Fixes
 * Fixed crash when deselecting the Credential Provider tile.
 * Fixed missing lookup of "no_default" setting.
 * The installer now writes all possible configuration keys to the registry. The configurable parts in the installer are unchanged.

# Version 3.1.1, 2021-05-07

## Features
 * Added "prefill_username" configuration setting to prefill the username field with the last user that logged on

## Fixes
 * Fix loading custom bitmaps as custom tile picture.
 * Fix WinHttp default timeouts

# Version 3.1.0, 2020-09-29

## Features
 * The behavior of the CP and Filter can be modified for each scenario separately (see docs).

## Enhancements

## Fixes
 * Fix missing Submit button upon failure when 2step is enabled.


# Version 3.0.0, 2020-05-28

## Features
 * Support realms by configuring a realm mapping in the registry
 * Support of Push Token
 * Support offline authentication
 * Support exclusion of a single account

## Enhancements

## Fixes


# Version 2.5.2, 2019-08-02

## Fixes
 * Fix for clients experiencing a freeze when using only hide_otp configuration.
 * URL encoding of parameters which are sent to the server.

# Version 2.5.1, 2018-11-26

### Fixes

 * Fix buffer overflow in certain RDP scenarios, that crashes the terminal server client.
 * Make default tile configurable via NO_DEFAULT='1' registry key.


# Version 2.5.0, 2018-10-15

### Features
 *	Support SMS/Email tokens, which require a transaction id to be appended to the request. This only works when the CP is configured to ask for the OTP in a second step.
	The message of the challenge is displayed to the user.
	
### Enhancements
 *	Logging of sensitive data can be activiated by a registry key
 
### Fixes
 *	Fix missing lookup of the domain when using over-the-shoulder-prompting (UAC).
	Note: The UAC scenario with the credential provider does currently not work on Windows 8/ Server 2012.
 
# Version 2.4.0, 2018-09-13

### Features
 *	Password change on a locked workstation is not possible. If this occurs, block our tile and guide the user to sign out and in again to
	complete the password change in the LOGON scenario. (Similar to what Windows does)
	
### Enhancements

### Fixes


# Version 2.3.3, 2018-08-21

### Features
 * Optionally send an empty password or the domain password to the privacyIDEA server.
   (As intended in version 2.0)
   This is only possible if the request for the OTP is made in a second step.

### Enhancements
 * Added icon to display in installed software list
 * Improved debug message format
 * More debug messages
 * Changed version number format to end with buildnumber
 
### Fixes
 * Displaying the correct version number in the MSI as well as in the installed software list
 * Removed unnecessary communication with the privacyIDEA server

# Version 2.3.2, 2018-08-19

### Features
* Support changing the password on logon if the password expired or is requested to change by the admin

### Enhancements

### Fixes


# Version 2.3.1, 2018-07-19

### Features
  * Optional registry key for custom ports

### Enhancements
 * Adjusted Installer

### Fixes
  * Fixed a bug with parsing the path from the URL  

# Version 2.2, 2018-05-29

### Features
* Bugfix for URLs with scheme and paths specified
* Username and domain hideable on locked machines (custom login text will still be displayed)
* Custom OTP field text

### Enhancements
 * Adjusted Installer

### Fixes


# Version 2.1, 2018-05-07

### Features

### Enhancements
  
* When connecting to a machine with privacyIDEA CP, allow
  to use the credentials which were already passed in NLA.
  We only ask for OTP.

### Fixes


# Version 2.0, 2018-05-03

### Features
  * Replaced libcurl and OpenSSL with Winhttp
  * SSL errors can be ignored optionally
  * Second dialog to enter OTP separately
  * Optionally send the domain password to the privacyIDEA server
  
### Enhancements
  * Adjusted Installer
  * Add new logos
  * Cleanup license and README

### Fixes
  * Add correct user-agent
