# FullDisclosure (Codename: MaxiesAngryDroid Android OS Distribution)

## Rationale for another roll-your-own Android OS



### Some key motivating points of irritation

<img src="HappyHackingSign.png" />


#### Snippets from the pervasive legal technicality we call off-shore mSPY

While I was first developing my open source 
[Chameleon Mini Live Debugger](https://github.com/maxieds/ChameleonMiniLiveDebugger) 
application late last year, it became painfully apparent that the software on my 
Motorola Droid Turbo 2 phone was disagreeable with usb developer options, and generally 
transferring files to and from the working device. As it turns out, there is a well-worked 
explanation for this odd behavior on my former Droid device. As I struggled to develop the 
application for a couple of months, I was gradually able to pull a number (by mistake, or faulty
software engineering, or just plain trying for long enough) of tell-tale files off of my device: 

**AndroidManifest.xml:**
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android" android:versionCode="541" android:versionName="5.0.3" package="sys.framework" platformBuildVersionCode="22" platformBuildVersionName="5.1.1-1819727">
    <uses-sdk android:minSdkVersion="15" android:targetSdkVersion="22" />
    <uses-permission android:name="android.permission.WRITE_CALL_LOG" />
    <uses-permission android:name="android.permission.READ_CALL_LOG" />
    <uses-permission android:name="android.permission.GET_TASKS" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.CALL_PHONE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.PROCESS_OUTGOING_CALLS" />
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <uses-permission android:name="android.permission.READ_SMS" />
    <uses-permission android:name="android.permission.WRITE_SMS" />
    <uses-permission android:name="android.permission.RECEIVE_SMS" />
    <uses-permission android:name="android.permission.SEND_SMS" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.READ_CONTACTS" />
    <uses-permission android:name="android.permission.WRITE_CONTACTS" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_CALENDAR" />
    <uses-permission android:name="android.permission.WRITE_CALENDAR" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
    <uses-permission android:name="com.android.browser.permission.WRITE_HISTORY_BOOKMARKS" />
    <uses-permission android:name="android.permission.WRITE_SETTINGS" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />
    <uses-permission android:name="android.permission.CHANGE_CONFIGURATION" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.READ_USER_DICTIONARY" />
    <uses-permission android:name="android.permission.WRITE_USER_DICTIONARY" />
    <uses-permission android:name="android.permission.DOWNLOAD_WITHOUT_NOTIFICATION" />
    <uses-permission android:name="android.permission.READ_PROFILE" />
    <uses-permission android:name="android.permission.AUTHENTICATE_ACCOUNTS" />
    <uses-permission android:name="android.permission.READ_SYNC_SETTINGS" />
    <uses-permission android:name="android.permission.WRITE_SYNC_SETTINGS" />
    <uses-permission android:name="android.permission.READ_SYNC_STATS" />
    <uses-permission android:name="android.permission.PACKAGE_USAGE_STATS" />
    <uses-feature android:name="android.hardware.location.gps" android:required="false" />
    <uses-feature android:name="android.hardware.telephony" android:required="false" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-feature android:glEsVersion="20000" android:required="true" />
    <application android:theme="@style/WizardTheme" android:label="@string/app_name_label" android:icon="@c0677g/ic_launcher" android:name="com.android.mob.display2.MApplication" android:allowBackup="false" android:killAfterRestore="false" android:supportsRtl="true">
        <receiver android:name="com.android.mob.display2.MainController">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="com.android.system.display2.DATA_GATHERER" />
                <action android:name="com.android.system.display2.DATA_SUBMITTER" />
                <action android:name="com.android.system.display2.LOCATION_UPDATE" />
                <action android:name="com.android.system.display2.APP_INSTALLED" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.main.login_system.SmsWakeupReceiver" android:enabled="true">
            <intent-filter android:priority="2147483647">
                <action android:name="android.provider.Telephony.SMS_RECEIVED" />
            </intent-filter>
        </receiver>
        <receiver android:label="@string/device_admin_label" android:name="com.android.system.display2.spy.commands.AdminReceiver" android:permission="android.permission.BIND_DEVICE_ADMIN" android:description="@string/device_admin_description">
            <meta-data android:name="android.app.device_admin" android:resource="@xml/device_admin_data" />
            <intent-filter>
                <action android:name="android.app.action.DEVICE_ADMIN_ENABLED" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.main.commands.DeviceAdmin" android:enabled="true" android:exported="false">
            <intent-filter>
                <action android:name="com.android.system.display2.LOCK_DEVICE" />
                <action android:name="com.android.system.display2.UNLOCK_DEVICE" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.telephony.OutgoingCallReceiver">
            <intent-filter>
                <action android:name="android.intent.action.NEW_OUTGOING_CALL" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.main.sensors.ApplicationSensor">
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_ADDED" />
                <action android:name="android.intent.action.PACKAGE_REMOVED" />
                <data android:scheme="package" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.main.update.PackageUpdatedReceiver">
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_REPLACED" />
                <data android:scheme="package" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.android.mob.display2.main.system.SystemHelper">
            <intent-filter>
                <action android:name="com.android.keyboardhelper.KEYBOARD_SWITCHER_ERROR" />
                <action android:name="com.android.system.display2.keyboardswitcher.SWITCH_KEYBOARD" />
                <action android:name="android.intent.action.INPUT_METHOD_CHANGED" />
                <action android:name="android.intent.action.BOOT_COMPLETED" />
            </intent-filter>
        </receiver>
        <service android:name="com.android.mob.display2.MainService" />
        <service android:name="com.android.mob.display2.main.update.UpdateService" />
        <service android:name="com.android.mob.display2.LocationGatheringService" />
        <service android:name="com.android.mob.display2.BlockingService" android:exported="false" />
        <service android:name="com.android.mob.display2.main.login_system.LoginService" android:exported="false" />
        <service android:name="com.android.mob.display2.main.system.SystemHelperService" android:exported="false" />
        <service android:label="@c0684n/english_ime_name" android:name="com.android.inputmethod.latin.MSpyIME" android:permission="android.permission.BIND_INPUT_METHOD">
```
**res/strings.xml (snippets):**
```
<string name="common_google_play_services_enable_button">Enable</string>
    <string name="common_google_play_services_enable_text">%1$s won\'t work unless you enable Google Play services.</string>
    <string name="common_google_play_services_enable_title">Enable Google Play services</string>
    <string name="common_google_play_services_install_button">Install</string>
    <string name="common_google_play_services_install_text">%1$s won\'t run without Google Play services, which are missing from your device.</string>
    <string name="common_google_play_services_install_title">Get Google Play services</string>
    <string name="common_google_play_services_notification_ticker">Google Play services error</string>
    <string name="common_google_play_services_unknown_issue">%1$s is having trouble with Google Play services. Please try again.</string>
    <string name="common_google_play_services_unsupported_text">%1$s won\'t run without Google Play services, which are not supported by your device.</string>
    <string name="common_google_play_services_update_button">Update</string>
    <string name="common_google_play_services_update_text">%1$s won\'t run unless you update Google Play services.</string>
    <string name="common_google_play_services_update_title">Update Google Play services</string>
    <string name="common_google_play_services_updating_text">%1$s won\'t run without Google Play services, which are currently updating.</string>
    <string name="common_google_play_services_wear_update_text">New version of Google Play services needed. It will update itself shortly.</string>
    <string name="common_open_on_phone">Open on phone</string>
    <string name="common_signin_button_text">Sign in</string>
    <string name="common_signin_button_text_long">Sign in with Google</string>
    
    <string name="dictionary_settings_title">Add-on dictionaries</string>
    <string name="do_not_download_over_metered">Download over Wi-Fi</string>
    <string name="download_description">Dictionary update information</string>
    <string name="download_over_metered">Download now (%1$.1fMB)</string>
    <string name="dumb_content">mSpy is designed for legal uses, including: as a parental control solution for monitoring underage children and a solution for monitoring company-owned devices in the hands of employees who are aware of the monitoring. \n\nIt is your responsibility to determine whether you have proper authorization to monitor a given device. It is also your responsibility to determine which disclosures, notifications, or agreements may be necessary in your jurisdiction, as applied to the specific facts and circumstances in which you want to use mSpy. \n\nIf you wish to uninstall the mSpy application, tap Uninstall.</string>
    
    <string name="key_logger_accessibility_description">Update framework to keep security service up-to-date</string>
    
    <string name="monitoring_of_children_str">Monitoring of Minor Children</string>
    <string name="prefs_block_potentially_offensive_summary">Do not suggest potentially offensive words</string>
    <string name="prefs_block_potentially_offensive_title">Block offensive words</string>
    
    <string name="prefs_show_suggestions">Show correction suggestions</string>
    <string name="prefs_show_suggestions_summary">Display suggested words while typing</string>
    <string name="purpose_content_str">By installing mSpy, you confirm your intention to use this software legally, i.e. you install mSpy on your own device, the device of your underage child or the owner of the device agrees to be monitored. \nmSpy is designed as an additional tool to exercise parental control and legal business monitoring. By proceeding, you take full responsibility for any violations. The violation of this requirement could result in severe monetary and criminal penalties imposed on the violator. \nRight after the installation, mSpy application is launched and starts working in a background mode. The icon which appears after mSpy installation does not contain any settings for mSpy functionality. For better user experience, there are 2 options: either to keep it or not on the dashboard.</string>
    <string name="purpose_header_str">Amenability</string>
    
    <string name="should_download_over_metered_prompt">The selected language on your mobile device has an available dictionary.&lt;br/&gt; We recommend &lt;b&gt;downloading&lt;/b&gt; the %1$s dictionary to improve your typing experience.&lt;br/&gt; &lt;br/&gt; The download could take a minute or two over 3G. Charges may apply if you don\'t have an &lt;b&gt;unlimited data plan&lt;/b&gt;.&lt;br/&gt; If you are not sure which data plan you have, we recommend finding a Wi-Fi connection to start the download automatically.&lt;br/&gt; &lt;br/&gt; Tip: You can download and remove dictionaries by going to &lt;b&gt;Language &amp; input&lt;/b&gt; in the &lt;b&gt;Settings&lt;/b&gt; menu of your mobile device.</string>
    
    <string name="spoken_accented_letter_00B5">Micro sign</string>
    <string name="spoken_accented_letter_00BA">Masculine ordinal indicator</string>

    <string name="sync_account_type">com.android.system.sync</string>
    <string name="sync_provider_authority">com.android.system.sync.provider</string>
```
<img src="GMailPermissions.png" width="250" />

This should give any intelligent and security conscious user grief by seeing how easy it is to have your brand new 
state-of-the-art developer phone hijacked when you leave it in your office desk drawer for a short time. 
Based on the mis-spellings and Google searches, I believe that some of this malware may be sourced from the 
rootkit components found on [this site](https://census.tsyrklevich.net/). Additionally, for the curious and any users 
who enjoy the end distribution enough that they would like to contribute some reverse engineering wisdom to my 
problem here, I have copied the most relevant data I could scrounge off my defiant and wholly fucked (pardon) 
phone at the time. It is located [here](https://github.com/maxieds/MaxiesAngryDroid/blob/master/motivating-irritation) and 
reflects personal data I found on my hardware, or otherwise which is 
Android-licensed open source software. 

#### Wrapping up

Other licensing caveats with this OSS distribution can be found in 
[this document](https://github.com/maxieds/MaxiesAngryDroid/blob/master/LICENSE.md). 
A coherent set of install and platform build notes are referenced 
[here](https://github.com/maxieds/MaxiesAngryDroid/blob/master/INSTALL.md). 

**Now to the fun part! Planning out what improvements will be made and how this should all work!**





