# FAQ

## Why a messenger?

Trying to achieve mass adoption for a client, Carl & Jarrad looked at things like where people are, how they behave on their devices, and how much time they spent on PC vs. mobile. As of 2014, people spend more time on smartphones than desktops; and of that time, a **third** of it is in instant messengers.

Instant messengers have the highest retention rates. That is to say that when someone downloads and installs the app, they won't immediately uninstall it.

The average user lifetime skyrockets when friends join up as well, creating a network effect. When you think about the user base, and you can connect it with Etherum, things like payments and applications built on top of Etherum and integrated into a conversational interface becomes a clear path forward. 

Ultimately, we're creating a browser-messenger hybrid that will give us the opportunity to cast a wide net and focus on user acquisition while staying agnostic and as close as possible to the principles that Etherum embodies.

## Does Status support DApps that have their own web page?

Yes, we support DApps within their own web page and are striving for SWARM support also. The chances are that if a DApp works in Mist or MetaMask, it is likely to work in Status!

Our goal is to be a DApp browser for Android & iOS. In addition to that, we'll support a Chat API if you wish to integrate within a chat context.

If your web-based DApp renders on mobile, trying using the `!browse` command inside a chat and navigating to your DApp URL. During our alpha release, DApp developers can also add their DApps as default contacts by following [these instructions](../contributing/development/adding-dapps.md), but in later releases, these will be discoverable to users via the Discover feature.

 
## Can your app be launched with a link?

Not at the moment. The standard we will likely support is [EIP67](https://github.com/ethereum/EIPs/issues/67).

## Do I have to run go-ethereum myself or on a server?

Status includes `go-ethereum` and connects directly to the Ethereum network. All you need to do is run the Status app. This is possible to do with the new Light Client Protocol.

## When did you start coding and how you are funded?

Status is largely self-funded.  We've been working on it prior to Devcon1, and we were awarded a Devgrant to port EthereumJ to Android before that.

EtherumJ has different goals. Its developers intended it for server use and had no interest in supporting the Light Client Protocol. Other important factors were that we largely wanted a single codebase for multiple platforms; we had Java running on iOS and Android; and we wanted to unify the GUI, but the means to do so (JavaFX) wasn't suited to mobile devices.

Our current approach allows us to get bleeding edge tech and stability of geth while maintaining a single codebase.

## I am new to Ethereum & Blockchain and would like to contribute to the project. Where would you suggest I start?

To get up to speed with Ethereum, here are a few resources to get you started:

[Ethdocs.org](http://www.ethdocs.org/en/latest/),
[Ethereum.org](http://ethereum101.org/), 
[Ethereum Stack Exchange](http://ethereum.stackexchange.com/), and 
[Ethereum on Youtube](https://www.youtube.com/user/ethereumproject/playlists)

For Status - please take a look under the [Contributing Section](../index.md#how-to-contribute), and ask us about it [on Slack](https://status.im) (we're friendly people!)

## I have a DApp that runs on Mist. How can I test it in Status?

Each chat context has a command !browse - that allows users to access a web view (imagine this as a bit like a browser tab), much in the same way as Mist. Regarding integration & compatibility, nothing is required on your end if it already works in Mist.

Looking beyond the alpha, we'll have developer tooling and a way for DApp developers to have profiles for theirs DApps (making them discoverable through the 'Discover' feature), along with the Chat API for developers who want to integrate through a conversational UI rather than (or in addition to) web view.

##  What is the "jail" in your status-react code?

When the Chat API is ready to use, your javascript code is executed in Otto VM  [https://github.com/robertkrimen/otto](https://github.com/robertkrimen/otto), the same javascript engine that `go-ethereum` uses. In theory, when the code is executed in a "jail", it shouldn't interfere with the rest of Status. At the moment we have no implementation of the halting problem, but we will.

For web DApps, we rely on the web view to correctly jail javascript.

## When can we expect to see the beta?
The first release of our alpha was at the very beginning of Q1 2017. The beta will come at the end of Q1 or early Q2 2017 with developer tooling, bug fixes, and the ability for DApps to integrate within a chat context.

## Is it going to be for Android only? 

No, we support Android & iOS.

## Is it possible to install Status? How can I test it?

At the moment you have to [build it yourself](../contributing/development/building-status.md). We are fixing some bugs before the first alpha release to the early access subscribers that signed up on our website [https://status.im](https://status.im). Alternatively, there are some binaries floating around the Slack now.

Soon we'll have our alpha test on Google Play & Testflight. Currently, Status has been tested on:

- LG Nexus 5X
- Samsung Galaxy Nexus
- Samsung Galaxy A3
- Samsung Galaxy A5
- Samsung Galaxy S7 Edge
- Motorola G3
- iPhone 5
- iPhone 6S
- iPhone 7

## What languages do you support?

We’re currently supporting 30 languages — this includes: English, 官話, 官话, 廣東話, 上海话, Nederlands, Français, Deutsch, हिन्दी, Magyar, Italiano, 日本語, 한국어, Polski, Português brasileiro, Português europeu, Română, Slovenski, Español, Español (Latin-America), Swahili, Svenska, Suisse française, Schweizerdeutsch, Svizzera Italiana, ภาษาไทย, Türkçe, русский, українська, اُردُو & Tiếng Việt!

If you see a typo, mistranslation, or something missing, don't hesitate to let us know [via the Status Slack](http://slack.status.im), or fix it yourself using our [Translation Guide!](../contributing/translations.md)

## What about all these permissions in the app?

Permissions are always a hot topic for apps. We hate the way we’re doing them too. The good news is it’s only like this for alpha, and in production, we’ll make permission usage on-demand. At the moment, there are many moving parts and a bunch of react-native dependencies (and Instabug) which don’t have code to ask on-demand. Thanks for understanding!

**Contacts, SMS, and telephone permissions** are for an optional step of phone contact synchronization. We don’t use them unless you tap on the phone sync request message.  

**Location permissions** are used for our toy !location command. Our aim is to provide this to DApps for things like sharing location with friends, ordering food, or self-driving cars.  

**Microphone permissions,** while not needed in this version, are included because we intended to send audio messages over Whisper. In practice, it was a bad idea. We plan to offer audio messages in the beta, however, so it will stay included. It is also used in Instabug which we use to collect feedback.  

**Storage permissions** are required to store blockchain data. 

**Camera permissions** are required to set up a profile picture and for reading QR codes.

## Where are the nightlies?

Here you go!
[http://artifacts.status.im:8081/artifactory/nightlies-local/](http://artifacts.status.im:8081/artifactory/nightlies-local/)





