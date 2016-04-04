<img src="https://ownpush.com/wp-content/uploads/2016/02/ownpush_128-logoSpelledout.png">
# OwnPush Developer Documentation #
## Overview ##
OwnPush is a Fastboot product, designed to offer an innovative and open source solution to the challenge of providing push notifications to Android devices. OwnPush provides end-to-end encrypted push messages, is simple to integrate, and battery-light and does not rely on Google Cloud Messaging (GCM), or require that devices have Google Services available, in order to function. It is completely independent.  
<img src="https://ownpush.com/wp-content/uploads/2016/03/ownpush_structural.png">

## Setting Up a New App Using OwnPush ##
### Generate key pairs (API & APP) ###
OwnPush is all about security and therefore we make use of two key pairs which are both used by the NaCl crypto library and will ensure a safe & secure push message. The two keys to generate are the API key and the APP key which are used in the following way:
#### API Key ####
This key is used to verify that the push message has originated from the correct developer. We keep a copy of only the public key and use that to verify the signature of the message sent.
#### APP Key ####
This key pair is mainly used in the encryption method we recomend for message data. On registration you will record the 'install public ID' and will use this and your APP private key to create an encrypted message that only the intended device can decrypt.

This APP key's public component is also used by the OwnPush services for message addressing. 

##### To Generate #####
```$ python generate_keys```

Then input the public keys into the OwnPush web interface and your app's build files. 
**(NEVER EXPOSE THE PRIVATE SECTIONS OF THE KEYS, THESE ARE ONLY TO BE USED BY YOUR WEB SERVICES)**

### Create application with OwnPush ###
To create an Android application that makes use of the OwnPush notification services you need to do the following:
1. Import the OwnPush client module into your application (this exposes the OwnPush service and the needed crypto functions for message decryption)
2. Add the permissions and BroadcastReceivers for OwnPush (1)
3. Add the needed code for key pair generation and install registration (1)
4. Pass the install public id back to your web service
  
### Create a web service with OwnPush ###
To create a web service that makes use of OwnPush you must do the following:  
1. Expose a register endpoint for the Android app to register its install public id
2. Generate a valid OwnPush token using NaCl crypto library (2)
3. Send a HTTPS POST request to the OwnPush services (2)

*(1) Please see the demo application(s) for example implementation of this*  
*(2) Please see the demo server(s) for example implementation of this*  

### API Token Format ###
#### Web Service -> Device Format ####
The format of the push messages sent to the device from the push services is as follows, if the header contains a "to" field it is a push message (this to field indecates the APP and the INSTALL (APP_ID.PER_INSTALL_ID)) the body of the token contains the NaCl encryptyed data at the npnce used to encrypt the data.

#### Header ####
```
{"alg": "FM-1", 
  "to": "28e31f7be76745958c85ecb69fa94659c998062c5f72e2c5bc408f8334c7fe4a.c2e34f9a1fe70f2afa16b3c0e6a2c9c37a69620ff0b603f82c2c3eb5b8f2e44e", 
  "srv_v": "v0.0", 
  "typ": "JWT"}
```

#### Body ####
The data within the body is encrypted with the APP private key and the INSTALL public key
```
{"data": "93b120001b338ebc26e22466e6b826d079420834e8fc1e57390b4b94cf02db80140b660264fc69aac4a9a1c7a8c5c0fae710b5d625e6ed59", 
  "nonce": "51632b7b52080fdecde47e7da65a56be4594c9a882686316"}
```
This data is then encoded into b64 format and signed via the NaCl library as sign(b64(header).b64(body) and the final data sent to the api is in the format

```b64(header).b64(body).b64(signature)```
