# Special-Links
### Special links: phone calls, sms, e-mails, iPhone and Android apps

Everyone knows to include a link into a page, but what I want to discuss today is how you can include some special links.

## Phone calls
This is something cool and with the explosion of smart phones with which you can easily browse this is definitely to consider having on the mobile version of your website. Such a link will initiate a call on your mobile to a specified number. But here the things are a little bit more complicated, requiring different links for different phones. You can easily find how to create such a link consulting the WURFL database and looking at the `wml_make_phone_call_string` property in the `wml_ui` category.

Basically this is done as follows:
for iPhone and Nokia phones
```
callto:[phone_number]
```
for Android phones
```
wtai://wp/mc;[phone_number]
```
and most of the newest devices. If you want to have only one type of URI, use this one.
```
tel:[phone_number]
```

> In the phone number you can use +(plus) sign for international numbers. What’s also interesting to know is that this can even work on a desktop if you have an application like Skype installed. So maybe it’s a good idea to have this on the classic/desktop website too.

### Later update 
Another interesting phone link will be how to call a teleconferencing phone number. There you call a phone number and then you enter your conference code, usually followed by hash(#). To do this from a link you will need a pause after the phone number and this is done with , (comma), usually entered by a long press on star(*). I tested this on Android and iOS and it works fine, but you usually need two pauses (,) between the phone number and conference code. Same way you can dial an extension line.

Examples
```
callto:12345678
- call 12345678 on iPhone and Nokia

wtai://wp/mc;12345678
- call 12345678 on Android

wtai://wp/mc;+123456789
- call an international number on Android

tel:12345678
- call 12345678 on most of the newer devices

tel:12345678,,100200#
- join 100200 conference code on the conference line 12345678 on most of the newer devices

tel:+12345678,,100200#
- join 100200 conference code on the international conference line +12345678 on most of the newer devices
```
## SMS
From a web page you can open the SMS sending application on the user phone with a link like below:
```
sms:<phone_number>[,<phone_number>]*[?body=<message_body>]
```
The link contains a comma separated list of phone numbers and an optional message body. The phone numbers are specified as in the call links. Detailed information you can find in the [URI Scheme for GSM Short Message Service](https://www.ietf.org/archive/id/draft-wilde-sms-uri-19.html)

Examples
```
sms:12345678
- SMS to 12345678

sms:12345678?body=Hello my friend
- SMS “Hello my friend” to 12345678

sms:123456789,+123456789?body=Hello
- SMS to multiple phone numbers, including an international one
```
> There is also an URI version for MMS starting with mms:. On some (mobile) browsers (devices) it is also reported to work smsto: and mmsto:, although I would recommend the first version.

## iPhone/iPod/iTunes
When developing a website iPhone is definitely to be considered. You can include links to items in the iTunes store, such as movies, music or application. Apple provided for your convenience a web interface to create such links: [ITMS Link Maker](https://tools.applemediaservices.com/). Just specify the country, the search keyowrds and what type of iTunes items. You will get a list of items and when you click one you will get the link. You can even get the link for an author. These links will both work on the desktop and iPhone.

Example: [Fluid application (free)](https://apps.apple.com/us/app/fluid/id312575632?ign-mpt=uo%3D6)

## Android market
Android is gaining market share as we speak. Nexus One was just released and in my opinion will beat iPhone. As you include links to iTunes, you can include links to applications in [Android Market](https://play.google.com/store/games).
```
market://search?q=<query>
```
or
```
market://details?id=<your.package.name>
```
The query can include keywords or can identify a specific application using `q=pname:your.package.name` and then the link will be `market://search?q=pname:<your.package.name>`.

## Ovi Store
Nokia created a new fresh application repository for their latest phone – [Ovi Store](http://store.ovi.com/). If you want to include a link to an application, search for it and then copy the link that it will look like `http://store.ovi.com/content/XXXXX?clickSource=publisher+channel`. Just remove the last part and include `http://store.ovi.com/content/21309` into your page, where `XXXXX` is the application Id. You can also include a link to a publisher’s page containing a summary of their application. The link is found on any of the publisher’s application (see by Publisher Name) and it will look like `http://store.ovi.com/publisher/Publisher+Name`

## Windows Marketplace
We cannot exclude Microsoft from the list with their [Windows Phone Marketplace](). Same steps to find out the application link: search it, copy the link location and strip the last part. The link will look like `http://marketplace.windowsphone.com/details.aspx?appId=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`, where `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` is the application ID, clearly resembling a GUID. Here publishers don’t have a personal page.

## BlackBerry App World
For all those BlackBerry fans, there is [BlackBerry App World](). Again same process: search for the application and copy the link location of the application icon. The format is `http://appworld.blackberry.com/webstore/content/XXXXX`, where `XXXXX` is the application ID. The app authors have a page here with a summary of their apps. See the by Author link under each application. The link will be like `http://appworld.blackberry.com/webstore/vendor/XXXX`, where `XXXX` is the author ID.

## Geolocation
Nowadays you cannot even imagine a world without maps and GPS. More and more contact pages include a map too. Nowadays smart phones usually include a map application and opening a map with your location in it would be quite nice for the user
```
geopoint:latitude,longitude
```
As simple as this and you know where to go.

## Messengers
From a web site you can also interact with the messenger applications installed on your machine.

### Yahoo Messenger
```
ymsgr:ACTION?USERNAME&m=YOUR+MESSAGE
```
> The possible actions are addfriend, sendIM and call. The message can, of course, be specified only for sendIM action. The `USERNAME` should be `your.account@yahoo.com` or `your.account@hotmail.com`.

Example: `ymsgr:sendIM?beradrian&m=Hello` – Say Hello in Yahoo Messenger.

### Windows Messenger
```
msnim:ACTION?contact=USERNAME
```
The possible actions are chat, add (to add a contact), voice (for voice call) and video (for video call). The `USERNAME` should be `your.account@yahoo.com` or `your.account@hotmail.com`.

Example: `msnim:chat?contact=beradrian@yahoo.com` – Chat with me in Windows Messenger.

### Google Talk
```
gtalk:ACTION?jid=USERNAME&from_jid=YOURNAME
```
The possible actions are chat and call (for voice call). The `USERNAME` and `YOURNAME` should be your.account@gmail.com. The parameter from_jid is optional and it should be specified only if you use multiple accounts.

Example: `gtalk:chat?jid=beradrian@yahoo.com` – Chat with me in Google Talk.

### Skype
```
skype:USERNAME?ACTION
```
The possible actions are chat, add (to add a contact), userinfo (to view a profile) and voicemail (to leave a voicemail). The `USERNAME` is your Skype ID.

Example: `skype:chat?jid=beradrian` – Chat with me in Skype.

### Lync
```
sip:USERNAME@DOMAIN
```
The main thing here is the sip protocol. It is possible that this protocol can be used by other applications too, not being something specific to Lync.

Example: `sip:john.doe@domain.com`
### WhatsApp
```
whatsapp://send[/<phone_number>]?text=<message>
```
Example: Say [‘Hi John’](whatapp://send/0123456789?text=Hi%20John!) to number 0123456789 or pick a contact and Say [‘Hello World!’](whatsapp://send/?text=Hello%20World!).
> There are also other messengers but these are the most widely used. If you need another one, just post a comment.

## Mail
It’s pretty easy to include a link for sending an email into your webpage. Basically it’s replacing the http scheme with mailto. So the link will look something like:
```
mailto:<email>[,<email>]*[?<arguments>]
```
Such a link will practically open the system application for sending emails (like Outlook or Thunderbird) and the message will be prepopulated with some values. As you can notice you can use multiple email addresses (To) separated by comma.

The possible arguments to be included are:

`subject` the message Subject field
`cc` the message CC field as a comma separated list of addresses
`bcc` the message BCC field as a comma separated list of addresses
`body` the message body. If you include a new line in your message you should include %0A.

Examples
```
mailto:nobody@wordpress.com
- the simplest mailto link

mailto:nobody@wordpress.com,no.one@wordpress.com
- multiple email addresses

“mailto:nobody@wordpress.com?subject=Testing mailto
- specify a subject

“mailto:nobody@wordpress.com?subject=Testing mailto&cc=no.one@wrodpress.com
- specify a subject and CC
```
> Just as a side note in the end, it’s better not to rely on this kind of mechanism for handling email on your website. A contact form that sends an email could be a better idea.


Most of these URIs work not only on browsers, but on QR codes readers as well.

Credit to [Adrian's Blog'](https://beradrian.wordpress.com/2010/01/15/special-links/)
