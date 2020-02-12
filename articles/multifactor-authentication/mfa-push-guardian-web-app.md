---
title: How to Implement MFA with Push Notifications for a Web App
description: Overview of how to implement MFA with push notifications for a web app
topics:
  - mfa
  - factors
contentType:
  - how-to
  - concept
useCase:
  - customize-mfa
---

# Implement MFA with Push Notifications for a Web App

[Multi-factor Authentication (MFA)](/multifactor-authentication) will add an extra layer of security to your web app. <dfn data-key="multifactor-authentication">MFA</dfn> requires users to present more than one piece of identifying information to log in to your app. One of the most straightforward ways to handle MFA is to use push notifications with Auth0's Guardian app, installed on the user's smartphone.

## Prerequisites
* An active Auth0 account. If you do not have an active account, you can create one on the [Signup](https://auth0.com/signup) page.
* A [tenant](/getting-started/create-tenant) for the application to reside in.
* A [regular web app](/dashboard/guides/applications/register-app-regular-web) created in the tenant. 

## Choose the MFA factor

Auth0 offers you the ability to choose from different [factors](/multifactor-authentication/factors) your users will be required to choose from when authenticating with MFA. In this case, you will use push notifications which will be sent to the Auth0 Guardian app installed on your user's smartphone. You can also choose the MFA policy when choosing the factor.

* Navigate to the [Multi-factor Authentication](${manage_url}/#/mfa) page in your Auth0 Dashboard. 
* Under **Factors**, locate and click the toggle next to **Push via Auth0 Guardian**.
* Scroll to the **Policies** section, and click the toggle next to **Always require Multi-factor Authentication** if you want to require that users utilize the factor chosen. 

:: note
Rules affecting Multi-factor Authentication will take precedence over the policy configuration chosen here. 
::

## Create the MFA Rules

You can configure [rules](/rules) in your [Auth0 Dashboard](${manage_url}/#/rules). Rules are powerful and can be used for a wide variety of ways to exercise granular control over your authentication pipeline. Here, you will use rules to specify that MFA is to be used, and further to use push notifications with Auth0 Guardian as the MFA factor. 

* On the [Rules](${manage_url}/#/rules) page in your Dashboard, click **+ Create Rule**. 
* Scroll to the **Multifactor** section, and click **Multifactor with Auth0 Guardian**.
* You can give this rule a name to identify it by, and you can modify or debug the script snippet provided. For more details on modifying this script snippet, see [Customize Multi-Factor Authentication](/multifactor-authentication/custom#change-the-frequency-of-authentication-requests).
 :: note
 Please note that *trying* or *debugging* the rule will save the rule as well, which will overwrite the rule if it already exists. 
 ::
* When done making your choices, click **Save Changes**

## Install Guardian 

[Auth0 Guardian](https://auth0.com/multifactor-authentication) is a smartphone app that your users can install to their Android or iOS devices. Users can install the app from the [Google Play Store](https://play.google.com/store/apps/details?id=com.auth0.guardian) for Android, or the [Apple App Store](https://itunes.apple.com/us/app/auth0-guardian/id1093447833?ls=1&mt=8) for iOS. 

## Test the Login

Once the user has installed Guardian and MFA has been enabled for your web app, you can attempt to login to the app. The initial configuration of Guardian requires that the user scan a <dfn data-key="qr-code">QR code</dfn> to register the device. 

* Log in to your web app. After a successful password entry, you will be presented with a QR code. 
* Open the Guardian app on your Android or Apple Device, and scan the QR code. 
* When prompted, enter the code now showing on the device. 

Once the device has been registered, the user can simply swipe left on the push notifications they received on their device to accept or deny the request. 

## Keep Reading

* [Troubleshoot Multi-Factor Authentication for End Users](/multifactor-authentication/troubleshooting)
* [Multi-factor Authentication in Auth0](/multifactor-authentication)
* [Multi-factor Authentication API](/multifactor-authentication/api)
* [Developer Documentation for Multi-factor Authentication](/multifactor-authentication/developer)