# VoiceIt-Android-Wrapper-BETA


For more information on VoiceIt and its features, see [the website](http://voiceit.tech) and [getting started docs](https://siv.voiceprintportal.com/getstarted.jsp)

* [Getting Started](#getting-started)
* [Installation](#installation)
* [API Calls](#api-calls)
  * [Create User](#create-user)
  * [Set User](#set-user)
  * [Get User](#get-user)
  * [Delete User](#delete-user)
  * [Create Enrollment](#create-enrollment)
  * [Create Enrollment By Wav URL](#create-enrollment-by-wav-url)
  * [Get Enrollments](#get-enrollments)
  * [Delete Enrollment](#delete-enrollment)
  * [Authentication](#authentication)
  * [Authentication By Wav URL](#authentication-by-wav-url)

## Getting Started

This is a BETA Version of a VoiceIt Wrapper meant solely for use inside of Android Projects, as our Java wrapper utilizes dependencies not available for Android.

To use this Wrapper in your Android Project, if you haven't already, please Sign Up for a free **Developer Id** at [http://voiceit.tech](https://siv.voiceprintportal.com/getDeveloperID.jsp). Then follow the installation instructions below.

## Installation

Add the VoiceIt class to your Android Project

### Permissions

In order to use VoiceIt inside of your Android apps make sure you have the following permissions enabled inside of your [AndroidManifest.xml](https://developer.android.com/guide/topics/manifest/manifest-intro.html) file, that let the app access internet, recording, and give it the ability to write to external storage.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
```

## API Calls

Here are code snippets that show you how you can call the Various VoiceIt API Calls inside of your Cordova Project JavaScript Files.

### Create User

To create a new user call the createUser function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), first name, last name

```java
try {

String response = myVoiceIt.createUser("developer@voiceit-tech.com", "d0CHipUXOk", "John", "Doe");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```
### Set User

To update an existing user call the setUser function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), first name, last name

```java
try {

String response = myVoiceIt.setUser("developer@voiceit-tech.com", "d0CHipUXOk", "John", "Doe");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```
### Get User

To retrieve an existing user call the getUser function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you)

```java
try {

String response = myVoiceIt.getUser("developer@voiceit-tech.com", "d0CHipUXOk");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```
### Delete User

To delete an existing user call the deleteUser function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you)

```java
try {

String response = myVoiceIt.deleteUser("developer@voiceit-tech.com", "d0CHipUXOk");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```
### Create Enrollment

To create a new enrollment template for the specified user profile use the createEnrollment function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), the path to the wave audio file and optionally a content language.

```java
try {

String response = myVoiceIt.createEnrollment("developer@voiceit-tech.com", "d0CHipUXOk", "/home/users/username/voicePrint.wav");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

/* And with the optional content language parameter */

try {

String response = myVoiceIt.createEnrollment("developer@voiceit-tech.com", "d0CHipUXOk", "/home/users/username/voicePrint.wav", "es-ES");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```

### Create Enrollment By Wav URL

To create a new enrollment template for the specified user profile use the createEnrollment function like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), the URL to the wave audio file and optionally a content language.

```java
try {

String response = myVoiceIt.createEnrollmentByWavURL("developer@voiceit-tech.com", "d0CHipUXOk", "http://voiceit-tech.com/voicePrint.wav");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

/* And with the optional content language parameter */

try {

String response = myVoiceIt.createEnrollmentByWavURL("developer@voiceit-tech.com", "d0CHipUXOk", "http://voiceit-tech.com/voicePrint.wav", "es-ES");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

```

### Get Enrollments

To get a list of the existing enrollments simply call the getEnrollments method for the specific user like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you)

```java
try {

String response = myVoiceIt.getEnrollments("developer@voiceit-tech.com", "d0CHipUXOk");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```
### Delete Enrollment

To delete an enrollment simply call the deleteEnrollment method for the specific user like this with the following parameters: developerID, email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), enrollmentId

```java
try {

String response = myVoiceIt.deleteEnrollment("developer@voiceit-tech.com", "d0CHipUXOk", "1816");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```

### Authentication

This REST API call is used to authenticate the specified user profile within the Voiceprint Developer Portal (VPDP) service.

It authenticates the specified user profile in the VPDP service database and returns success or failure.

Please Note: The Voiceprint Phrase's (VPP's) are Text-Dependent. The Minimum length of a VPP is 1.5 second. Please note: You cannot use the same sound file for an enrollment and then an authentication. This is because of our anti- spoofing technology.

To manage the VPPs associated with your DeveloperID, please login to the developer portal and navigate to Voiceprint Phrases section.

To authenticate the user profile use the authentication method like this with the following parameters: email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), the path to wave audio file, confidence level (between 85-100), and optionally a content language.

```java
try {

String response = myVoiceIt.authentication("developer@voiceit-tech.com", "d0CHipUXOk", "/home/users/username/voicePrint.wav", "85");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

/* And with the optional content language parameter */

try {

String response = myVoiceIt.authentication("developer@voiceit-tech.com", "d0CHipUXOk", "/home/users/username/voicePrint.wav", "85", "es-ES");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }
```

### Authentication By Wav URL

This REST API call is used to authenticate the specified user profile within the Voiceprint Developer Portal (VPDP) service.

It authenticates the specified user profile in the VPDP service database and returns success or failure.

Please Note: The Voiceprint Phrase's (VPP's) are Text-Dependent. The Minimum length of a VPP is 1.5 second. Please note: You cannot use the same sound file for an enrollment and then an authentication. This is because of our anti- spoofing technology.

To manage the VPPs associated with your DeveloperID, please login to the developer portal and navigate to Voiceprint Phrases section.

To authenticate the user profile use the authentication method like this with the following parameters: email, password(not encrypted, just in text form the plugin encrypts the password using SHA256 for you), the URL to wave audio file, confidence level (between 85-100), and optionally a content language.

```java
try {

String response = myVoiceIt.authenticationByWavURL("developer@voiceit-tech.com", "d0CHipUXOk", "http://voiceit-tech.com/voicePrint.wav", "85");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

/* And with the optional content language parameter */

try {

String response = myVoiceIt.authenticationByWavURL("developer@voiceit-tech.com", "d0CHipUXOk", "http://voiceit-tech.com/voicePrint.wav", "85", "es-ES");

} catch (IOException ex) {
			System.out.println("Error: " + ex.getMessage());
		}
    }

```
