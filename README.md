<img src="https://ownpush.com/wp-content/uploads/2016/02/ownpush_128-logoSpelledout.png">
### _Next generation, open-source push services for Android_ ###
Developers know that in order to keep their users engaged with their apps/services they need to use push messages. Until now there has been little choice outside of Google Cloud Messaging (GCM). With this lack of choice came a dependency on Google Services which is a known battery and resource drain on today’s modern devices. This dependency also has created a challenge for developers looking to provide the billion or more users who do not have access to Google Services, or choose to value privacy, with push notifications.

# Introducing OwnPush #
* **End-to-end encrypted:** With GCM, all messages go through Google, which acts as the gatekeeper between developer and user. We know that Android users value their privacy, and OwnPush messages are encrypted (seamlessly and by default) from the developer's server, all the way through to the end device. This means that we (and anyone else in the path) can't get into your push messages. Like it should be.
* **Simple to use:** Push messages can be delivered to any device running Android, whether tablet or phone. It works over Wifi or mobile data, and it’s very simple to use. To aid in implementing OwnPush in your applications, we will be providing libraries for major backend platforms to help with handling the encryption and signing process. 
* **Battery-light:** GMS is fairly heavy on the battery, as it has a huge number of features tied together, including location logging and Google accounts. OwnPush was designed to be as lightweight as possible. In addition, OwnPush has shown an ability to work with Android M’s Doze mode while still providing fast and efficient push notifications.
<img src="https://ownpush.com/wp-content/uploads/2016/02/ownpush_structural.png">

## What can this be used for? ##
OwnPush has the capability to be the driving force behind some really cool ideas, from a fully open-source PC-to-phone push system, to building real-time secure messaging platforms. OwnPush can do everything that other options can do, and it’s more secure to boot! OwnPush enables you to keep your users informed while not impacting battery life. We hope that the uses for OwnPush are limited only to your imagination.  
Open source tools are easier to work with, tweak and play with, and learn from. There’s no reason to use the proprietary Google Services library just to get push messages working! Coupled with XDA Labs, you can start to build an ecosystem without relying on Google at all, and without them being able to shut your developer account down!

## OwnPush Performance Examples ##
For an example of what OwnPush can offer regarding battery savings, we setup a test with a Nexus 9 over a 20hr period. The test application used OwnPush to keep alive a server connection (typical ping pong) once every 4-5 minutes and a push notification randomly sent every 2-10 minutes.  

**Nexus 9 CPU usage over 20hrs running OwnPush**  
<img src="https://ownpush.com/wp-content/uploads/2016/02/ownPush-n9-20hrs-usage.jpg">  

**OwnPush Application Resource usage on Nexus 9**  
<img src="https://ownpush.com/wp-content/uploads/2016/02/ownPush-n9-application-usage.jpg">  

**Google Services Resource usage on Nexus 9**  
<img src="https://ownpush.com/wp-content/uploads/2016/02/ownPush-n9-gms-usage.jpg">

# Get Involved
To find out more about how you can utilize OwnPush in your apps/services, check out the following resources:
* [OwnPush Developer Documentation](https://github.com/ownpush/docs/blob/master/DEVELOPERS.md)
* [OwnPush App Demos](https://demo.ownpush.com)
* [Contact Us](mailto:ownpush@fastbootmobile.com)
* 
