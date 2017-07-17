# FAQ

## Basics

### What is Status?

Status is an open source messaging platform and mobile interface to interact with decentralized applications that run on the Ethereum Network.

### Which Problem does Status want to solve?

In legacy social networks all parties (owner, advertiser, and user) operate with vastly different goals mind and their model fails to provide means by which their incentives can coexist and be aligned.

### How does Status want to solve this?

By flattening the existing roles in social networks users posses a real stake in the network they participate in. Incentives of all parties are aligned and naturally promote behaviours that benefit all participants.

### Why a Messenger?

When Carl & Jarrad looked at how to achieve mass adoption for a client. We looked at things such as where the people are, how they behave on their devices, time spent on pc vs mobile - as of 2014 more time is spent on mobile than desktop, and of that time - a THIRD of it is spent within Instant Messengers.

Instant Messengers have the highest retention rates, that is when you purchase an install, they become sticky and typically users won't immediately uninstall.

The average user lifetime sky rockets once their friends are involved. When you start thinking about this as a user base and how to connect that with Ethereum, things like payments and applications built on top of Ethereum integrated into a conversational interface starts becoming like a clear path forward.

Ultimately we're building a hybrid browser and messenger for us to have the best chance to cast the widest net and focus on user acquisition, staying agnostic and as close as possible to the principles Ethereum embodies.

### When did you start coding and how you are funded?

Status is largely self-funded.  We've been working on it since prior Devcon1, and we were awarded a Devgrant to port EthereumJ to Android prior to that.

EthereumJ has different goals, its developers intended for server use and had no interest in supporting the light client protocol, another large factor is we wanted largely a single codebase for multiple platforms, we had Java running on iOS and Android, we want unify the GUI but the means to do that (JavaFX) is really not suited to mobile devices.

Our current approach allows us to get bleeding edge tech and stability of geth whilst maintaining a single codebase.

### Are there any videos?

Here are a two introductory videos. More can be found on the [Status Youtube](https://www.youtube.com/statusim) channel.

[![IMAGE ALT TEXT](http://img.youtube.com/vi/Je7yErjEVt4/0.jpg)](http://www.youtube.com/watch?v=Je7yErjEVt4)

[![IMAGE ALT TEXT](http://img.youtube.com/vi/-BVpm8cPLUU/0.jpg)](http://www.youtube.com/watch?v=-BVpm8cPLUU)


## Contribution

### How can I contribute to Status?

[http://contribute.status.im](http://contribute.status.im)


## Development

### Is it possible to install Status & how can I test it?

At the moment you have to [build it yourself](../contributing/development/building-status.md), we are just fixing some bugs before first alpha release to the early access subscribers which signed up on our website [https://status.im](https://status.im) - alternatively there are some binaries floating around the Slack now.

Soon we'll have our alpha test on Google Play & Testflight. Currently Status has been tested on:

- LG Nexus 5X
- Samsung Galaxy Nexus
- Samsung Galaxy A3
- Samsung Galaxy A5
- Samsung Galaxy S7 Edge
- Motorola G3
- iPhone 5
- iPhone 6S
- iPhone 7

###  What is the "jail" in your status-react code?

When the Chat API is ready to use, your javascript code is executed in Otto VM  [https://github.com/robertkrimen/otto](https://github.com/robertkrimen/otto)  this is the same javascript engine `go-ethereum` uses. That way your code is executed in a "jail" and shouldn't interfere with the rest of Status. At least, that's the theory, at the moment we have no implementation of the halting problem, but we will.

For web DApps, we rely on the webview to correctly jail javascript.

### Do I have to run go-ethereum myself or on server?

Status includes `go-ethereum` and connects directly to the Ethereum network. All you need to do is run the Status app! This is possible to do with the new Light Client Protocol.


## DApps

### What is the DApp Directory?

Much like the Apple App Store or the Google Play Store, the Status DApp directory will provide a way to navigate by category and rating, enabling users to find and install exactly what they are looking for.

### Does Status support DApps that have their own web page ?

Yes, we absolutely support DApps on their own webpage and are striving for SWARM support also. Chances are, if a DApp works in Mist or MetaMask it is likely to work in Status!

Our goal is to be a DApp browser for Android & iOS, in addition to this we'll support a Chat API if you wish to integrate within a chat context.

If your web-based DApp renders on mobile, trying using the `!browse` command inside a chat and navigating to your DApp URL! During our alpha release, DApp developers can also add their DApps as default contacts by following [these instructions](../contributing/development/adding-dapps.md), but in later releases these will be discoverable to uses through the Discover feature.

### I have a DApp that runs on Mist how can I test it in Status?

So each chat context has a command !browse - allowing users to access a webview (you can imagine this as a bit like a browser tab), so much in the same way as mist. In terms of integration/compatibility nothing is required on your end to do that if it already works in Mist.

That said, looking beyond the alpha, we'll have developer tooling, and a way for DApp developers to have profiles for theirs DApps (this then makes them discoverable through the 'Discover' feature), along with the Chat API for Developers who want to integrate through a conversational UI rather than (or in addition to) webview.


## Mobile Application

### Is it going to be for Android only?

No, we support both Android & iOS.

### It is said that the Status App is in the Alpha phase. How can I test it?

Take a look here: [http://contribute.status.im/](http://contribute.status.im/)

### Is there an Android Alpha?

Yes there is. Take a look here: [https://test.status.im](https://test.status.im)

### Is there an Apple Alpha?

Yes there is but unfortunately there are no more slots left for the Alpha due to a limited amount of codes. However, you can [build it yourself](../contributing/development/building-status.md) and run in the simulator or on your iPhone (Apple Developer Account required). Another way is to use [Genymotion](https://www.genymotion.com/), an Android emulator that runs on OSX.

### When can we expect to see the Beta?
The first release of our alpha was at the very beginning of Q1 2017, beta will come end of Q1 or early Q2 2017 with developer tooling, bug fixes & the ability for DApps to integrate within a chat context.

### What about all these permissions in the app?

Permissions are always a hot topic for apps, we hate the way we’re doing them too. The good news is it’s only like this for alpha and in production we’ll make permission usage on-demand. At the moment there’s many moving parts and a bunch of react-native dependencies (and Instabug) which don’t have code to ask on-demand. Thanks for understanding!

**Contacts, SMS, Telephone** — these are for an optional step of phone contact synchronisation. We don’t use them unless you tap on the phone sync request message.  

**Location** — Currently used for our toy !location command. Our aim is to provide this to DApps For things like sharing location with friends, ordering food, or self-driving cars.  

**Microphone** — In this version, we don’t need it, it’s there because we intended to send audio messages over Whisper, in practice this was a bad idea. We still intend to offer Audio messages in Beta so it’s going to stay. It is also used in Instabug which we use to collect feedback.  

**Storage** — We need a place to put the blockchain data.  

**Camera** — We use this for setting your profile picture and for reading QR codes.  

### Can your app be launched with a link?

Not at the moment, the standard we will likely support is [EIP67](https://github.com/ethereum/EIPs/issues/67).

### What languages do you support?

We’re currently supporting 30 languages — this includes; English, 官話, 官话, 廣東話, 上海话, Nederlands, Français, Deutsch, हिन्दी, Magyar, Italiano, 日本語, 한국어, Polski, Português brasileiro, Português europeu, Română, Slovenski, Español, Español (Latin-America), Swahili, Svenska, Suisse française, Schweizerdeutsch, Svizzera Italiana, ภาษาไทย, Türkçe, русский, українська, اُردُو & Tiếng Việt!

If you see a typo, mistranslation or something missing, don't hesitate to let us know [via the Status Slack](http://slack.status.im), or fix it yourself using our [Translation Guide!](../contributing/translations.md)


## SGT Token

### What are SGT used for?

Status Genesis Tokens are a way to say thank you to community contributors. SGT can be redeemed for SNT after the Contribution Period has been finalised.

### How can I buy SGT Token?

You can not buy SGT token, they are given for community contributions

### How can I earn SGT Token?

Until June 17th we’ll be allocating SGT to those who can prove they have helped grow or are a part of the Status community. Join the [Status Slack](http://slack.status.im/) to learn more.

## SNT Token

### What are SNT Token used for?

The Status Network Token is Status' ERP-20 compatible utility token. It is required for certain features of the client: select and receive push notifications, register and hold usernames via the Ethereum Name Service. In general SNT enable users to steer the direction of development and influence how the network evolves over time.

### How can I buy SNT

There will be a Contributing Periode starting on June 17th 2017 at 2pm GMT (UTC+0), which will end on 1st July 2017 at 2pm GMT (UTC+0) or before when some goals are achieved. [http://contribute.status.im](http://contribute.status.im/)

After that SNT will be traded on exchanges.

### What will be the initial exchange rate for SNT token?

10,000 SNT per 1 ETH

### Is it possible to buy less then 10,000 SNT Token?

You will be able to buy a minimum of 0.01 ETH which will be 100 SNT.

### What do I need to buy SNT?

You need an Ethereum wallet and ETH to buy SNT and receive it. **Do not use Exchanges to send ETH!** You can check out [MyEtherWallet](https://www.myetherwallet.com) or [Mist](https://www.ethereum.org) by the Ethereum network

### Can US residents buy SNT Token?

US residents can not participate due to US law restrictions outside of our influence.

## Links

[Facebook](https://www.facebook.com/ethstatus)

[Github](https://github.com/status-im)

[Reddit](https://www.reddit.com/r/statusim/)

[Status Blog](https://blog.status.im/)

[Status FAQ](https://wiki.status.im/getting-started/faq/#faq)

[Status Slack](http://slack.status.im/)

[Status](https://status.im/)

[Twitter](https://twitter.com/ethstatus)

[Youtube](https://www.youtube.com/statusim)

## Where are the nightlies?

Here you go!
[http://artifacts.status.im:8081/artifactory/nightlies-local/](http://artifacts.status.im:8081/artifactory/nightlies-local/)
