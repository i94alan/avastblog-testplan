# Avast Test Plan

### Background
Avast Secureline VPN proxy is a VPN service app that provides security and privacy by protecting your sensitive information using encryption shield 'tunnel' while you are on public / open WiFi.
While the vpn connection is up, your communication is encrypted and personal data is impossible to be stolen. VPN service app on various mobile platform or desktop such as iOS, Android and Windows.

### Objective
This document is aimed to provide the audience a high level test plan of the app on Android platform. 
The goal of this test plan is to validate the mobile application and ensure all stated requirements in the software specification are met.

### Test Strategy
- Test on a samsung device that is with android OS 5.0
- test case priority high medium low: P0 P1 P2
- test case severity critical high medium low: S0 S1 S2 S3
- smoke test: run all P0 for every release , dot not proceed further if any of them fail
- full test: 1st version of sw release of all stages: Alpha / Beta / Release Candidate
- partial test: incremental sw release + modification in release note
- regression test: perform only if time is allowed and sw modification indicates the affected feature


### Testing approach
Test will be designed based on following categories:
- Functional
- UI
- UX
- Reliability
- Security


### Feature
Features to be tested are:
- connection rules
 -- auto connect rules
 -- split tunneling
 -- trusted network
- notification bar 
- subscription / cancel
- reliability


### Pass / Fail criteria
- test is considered pass if all steps are met and marked green
- test is considered fail if at least one of the steps failed and marked red
- test is considered n/a if it needs further discussion


### Deliverables
- this plan (this)
- test case 
- test report summary 


### Test Case
###### template
1. ID
2. Name
3. Priority
4. Severity
5. Summary
6. Prerequisite
7. Steps
8. Expected Results


###### Test Case 1
- ID 1
- connect_rule_auto_connect
- P0
- S0
- auto connect "wifi or cellular data" while on cellular should auto connect successfully
- prerequisite: mobile device is attached to a local cellular network
- Steps
  1. go to settings / auto connect , select "wifi or cellular data"
  2. go back to home screen
- Expected Results
  1. successful
  2. indicate it's connected 


###### Test Case 2
- ID 2
- connect_rule_split_tunneling
- P1
- S2
- selecting a an app in split tunneling should be successful
- prerequisite: chrome app is installed on device, network is cellular
- Steps
  1. go to Settings / auto connect , select "WiFi or cellular data"
  2. go back to home screen
  3. go to Settings / Split Tunnel, turn it on , unselect all and select chrome
  4. go back to home screen
- Expected Results
  1. successful
  2. should auto connect right away
  3. successful
  4. should see the vpn is reconnected due to change in split tunnel


###### Test Case 3
- ID 3
- connect_rule_trusted_network
- P1
- S1
- putting an unsecure hotspot into trusted network should reflect in the notification message at home screen
- prerequisite: device is connected to a unsecure personal wifi hotspot 
- Steps
  1. go to Settings / auto connect , select "unsecure WiFi" / successful
  2. go home screen / vpn is auto connected
  3. go to Settings / Trusted Network, select + on the current network / successfully became trusted
  4. go back to home screen / it shows disconnected and message says "Paused, as you're on a trusted network"
- Expected Results
  1. successful
  2. vpn is auto connected
  3. successfully became trusted
  4. it shows disconnected and message says "Paused, as you're on a trusted network"


###### Test Case 4
- ID 4
- notification_bar_disconnect
- P0
- S2
- click disconnect in vpn notification should successfully reflect in app
- prerequisite: auto connect is off / app notification is turned on in Android Device
- Steps
  1. at home screen, hit connect / connected and observe notification is displayed in notification bar
  2. go to notification, click disconnect / back at home screen, it should stay at disconnected 
- Expected Results
  1. connected and observe notification is displayed in notification bar
  2. back at home screen, it should stay at disconnected 


###### Test Case 5
- ID 5
- subscription_check_unsubscribe
- P0
- S3
- download app and subscribe and unsubscribe
- prerequisite: has payment method in Gpay , first time user
- Steps
  1. launch app, at home screen , hit connect
  2. select a payment method and subscribe for 7 day free trial
  3. go to Settings / Subscription
  4. go to app store, select the app, manage subscription, scroll to bottom and click unsubscribe
  5. go back to app , Settings / Subscription
- Expected Results
  1. message is popped up to inform user to subscribe 
  2. successful and see the vpn is connected
  3. indicate device is subscribed
  4. indication of successful
  5. indicate the device is unsubscribe and only valid until trial period ends


###### Test Case 6
- ID 6
- reliability_check_24_hour
- P2
- S0
- run the app for 24 hours and ensure the app doesn't not crash and vpn is still connected
- prerequisite : service location is optimal / auto connect is off / connection is wifi
- Steps
  1. at home screen, hit Connect
  2. let it run in bg and stay for 24 hour and put it in foreground
- Expected Results
  1. connected
  2. still connected


###### Test Case 7
- ID 7
- ui_version_check
- P2
- S0
- app version in about settings is displayed correctly
- prerequisite: update to latest version on google play store
- Steps
  1. launch app
  2. go to settings about and check version
- Expected Results
  1. launched
  2. version is not empty is matched version on app store


###### Test Case 8
- ID 8
- security_unsecure_wifi_notification
- P2
- S1
- connecting to an unsecure wifi spot at public subway station will send notification of unsecure connection
- prerequisite: wifi is disconnected
- Steps
  1. go to settings / auto connect select "When I connect to unsecured WiFi"
  2. go to home screen
  3. go to MRT station and connnect to public wifi
  4. go back to vpn app home screen
- Expected Results
  1. successful
  2. vpn is not connected
  3. wifi is connected succesfully
  4. vpn is connected and notification is displayed to indicate unsecure network