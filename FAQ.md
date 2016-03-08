<img src="https://ownpush.com/wp-content/uploads/2016/02/ownpush_128-logoSpelledout.png">
# OwnPush FAQ

### Q: Is OwnPush open source? ###
**A:** Most of the parts of that make up OwnPush will be made open source. We already have made the code for our demo applications and Provider servers available on our GitHub account (https://github.com/OwnPush).

---

### Q: Can I deploy my own OwnPush server to serve push notifications to my applications? ###
**A:** At this moment we are concentrating on getting our own servers up for developers to use, and have not ruled out supplying server code. The challenge with this is that needing an OwnPush connection per application (if using your own servers) will cause a greater battery drain in comparison to using a single OwnPush service.

---

### Q: What do you need to make use of OwnPush? ###
**A:** All of this information can be found in the Developer Documentation we provide. In a nutshell, our OwnPush service application and the corresponding client library are all that is needed to be added into your applications while the OwnPush Provider server can be deployed for your application which handles sending the actual push notifications.

---

### Q: Do I have to use the OwnPush apk and service, or can OwnPush be bundled into my application directly? ###
**A:** Like the server question above, we have not ruled this out. However again this would require more OwnPush connections (think of it as a one-to-one connection), and therefore a bigger battery drain than having one service installed for many applications to use (one-to-many).

---

### Q: What happens to messages that are sent while the target device is offline (crashed / no data connection ect.)? ###
**A:** We have implemented a queue system within our OwnPush server so that any message that is not delivered (or acknowledged from the enduser OwnPush service) will be delivered on reconnect or next successful push message. These messages can be set to expire after X number of days sitting in the queue. We recommend 72 hrs, but in many cases will leave that up to you and your application to determine. (By default within the demo the message will expire from the queue after 24h)

---

### Q: How is OwnPush more secure than other push systems like GCM? ###
**A:** OwnPush provides the crypto functionality to the developer that makes it easy to implement end-to-end encyption with the use of public / private key encryption. When the developer calls the OwnPush register command a random keypair is generated, the public portion of which is used both as part of the push "to address" and in encrypting the push message. This ensures that only the target application install can decrypt the message. As to other push systems, the majority of them still utilize GCM to send the messages, aka GCM-reliant systems.

---

### Q: But isn't GCM encrypted? ###
**A:** GCM makes use of HTTPS/TLS so that its transport is encrypted (the message is secure from 3rd parties), however if the message is in plain text Google can see and store this.

---

### Q: Can I implement multi-users in my application and maintain security between users? ###
**A:** Yes, you just need to handle the registration keys in a way that user A cannot decrypt user B's messages.

---

### Q: Can OwnPush be used to push plain text messages? ###
**A:** Technically yes, however we strongly advise against this. Note OwnPush is a fully end-to-end encrypted system by default, so plain text messages may not be available in the final version.

---

### Q: Is there any limitations on the amount of messages I can send to my users? ###
**A:** We are still working out the specifics on "fair usage", etc.

---

### Q: Is there an API to allow me to see if a message has been deliverd? ###
**A:** Not at the moment, however it's on a list of possible features to add.

---

### Q: Is there any example implementations I can look at? ###
**A:** Sure, there is example code for both the Provider servers (python) and Android apps that make use of OwnPush services on our GitHub (https://github.com/OwnPush).

---

### Q: Is OwnPush Android only or will it support multiple platforms? ###
**A:** At the moment we only support Android, however implementng new clients is something we will be looking into. Different platforms have different requirements for how you can utilize push notifications, i.e. Apple mandates that you can only use Apple Push Notifications (APN) for distributing notifications to their platform. If you're interested in being involved in this, please [let us know](mailto:ownpush@fastbootmobile.com).

---

### Q: Does OwnPush work with Google's Doze Mode like GCM? ###
**A:** Not even GCM works "with" Doze Mode as it's whitelisted from battery optimisations (check for yourself). We have made a main focus of this project to be compatible with Doze as much as possible, however like GCM, for best results OwnPush should be excluded from battery optimisations (the user will be prompted to add OwnPush on app registration automatically).

---

### Q: Is this more power efficient than other push systems like GCM? ###
**A:** When looking at GCM it's very hard to get a good reading on power drain, a GCM is bundled within Google Play Services. However, as [we've shown](https://ownpush.com/#Uses), OwnPush itself uses very little resources to do a lot.

---