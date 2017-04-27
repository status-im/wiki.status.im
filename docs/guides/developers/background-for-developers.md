## Background for DApp Developers

More and more developers without much blockchain experience are now starting to develop Decentralized Apps, DApps, on Ethereum. And that’s exactly what we want! With more developers with a broad range of experiences and backgrounds, we’ll have a richer ecosystem of DApps for users and a better Web 3.0.

However, many developers then come with [questions which arise logically](https://www.quora.com/How-is-an-ethereum-dapp-hosted) from their other development experience — but questions which long-time blockchain users might not think of. In this article, we just want to give some background information to clear up some of these questions. If any of your questions aren’t answered, please come raise them on the Status [Slack](http://slack.status.im), and we might be able to address them in future articles.

### [What’s a decentralized app?](http://ethereum.stackexchange.com/questions/383/what-is-a-dapp)

One way to think of a blockchain is as a decentralized database. When you run a node in the blockchain, you’re hosting a local copy of this database. When this aspect of the blockchain became clear, developers naturally began to think of uses for the database other than validating transactions (as on Bitcoin).

In Ethereum, much of the business logic of your application, as well as transaction history, gets stored on the blockchain. For instance, if you made a fantasy football DApp, you’d [create a smart contract](https://medium.com/@ConsenSys/a-101-noob-intro-to-programming-smart-contracts-on-ethereum-695d15c1dab4), an address on the blockchain that can send and receive funds programmatically. You’d program your DApp to send and receive funds only in certain ways and under certain conditions. You’d allow your users to send funds to this smart contract to place their bets,  and the smart contract would lock the funds in place until the football scores were available from a trusted source, and then pay out to the winner.

Already, in a very important sense, your app is decentralized! No central server stores your users’ data, and no central server makes the decisions about routing and handling money. All this happens on the blockchain, as Ethereum runs the code in your smart contract.

### Okay, how would my users access this app?

So now the backend of your app is decentralized. But what about your frontend — HTML, JavaScript, CSS? And how can your users access this backend?

Here’s what used to happen. You’d get a server, on DigitalOcean for instance. You’d download some implementation of the Ethereum network — a client like geth (Go-Ethereum) — so that your server can connect to and make calls to the Ethereum blockchain. You’d build your frontend any way you normally build your front end: React, Meteor, heck you can go all Web 1.0 with just HTML and minimal JS if you want. You serve that frontend on your server by making it available at a port and configuring your DNS to point to that address, the way you normally do.

Then, using the [Web3.js library](https://github.com/ethereum/web3.js/), your app would make calls to the geth network running on your server. Just as any web app sends info to, or gets info from, a database, your application will call your smart contract. In this way, your users access your app like any other web page, and your server accesses the decentralized part of your app.

### Wait, so who’s storing my app?

Well. If you just write a simple smart contract, Mist Wallet will also allow you to publish it to the Ethereum network (by compiling it to Ethereum Virtual Machine code, and then making it live on the network). In the future, Status will also allow you to publish to the Ethereum network from your mobile phone.

But neither Mist nor Status is storing the business logic of your app. That lives on the blockchain, and is served and stored peer-to-peer. Spookily, it’s everywhere and nowhere!

### And I have to set up an Ethereum node to access the backend?

To save you the trouble of setting up an Ethereum node, the fine folks at Ethereum and ConsenSys have come up with two solutions, and Status now provides a third mobile-based solution. The [Mist browser](https://blog.ethereum.org/2016/07/12/build-server-less-applications-mist/), the MetaMask plugin for Chrome, and the [Status mobile app](http://status.im) all handle making the calls to the Ethereum network. You still use Web.js to program your app, but you don’t have to run a local geth node. As a result, if your users are using Mist, MetaMask, or Status, you can provide your app like a normal web page, and your users access it like a normal web page.

### Doesn’t that mean the front end isn’t decentralized? Is there a decentralized way to host my front end code?

As you astutely point out, the front end is not decentralized at this point in your app development. Some DApps, like [Aragon, are hosting](https://medium.com/@ericxtang/an-ethereum-dapp-case-study-f4dd7c1cbe7a) the front end both in a centralized and a decentralized way, so you actually can do both at the same time.

To make your front end decentralized as well, you’ll need to [use Swarm](https://medium.com/@codeAMT/how-to-launch-swarm-for-dapp-testing-8003e55380e2) or [IPFS](http://ipfs.io). These are distributed file servers. Swarm is actually one of the [core Ethereum technologies](http://ethereum.stackexchange.com/questions/375/what-is-swarm-and-what-is-it-used-for), while IPFS is an [independent file system](https://en.wikipedia.org/wiki/InterPlanetary_File_System). To use a distributed file server, your website needs to be packaged as a single file.

Fortunately, as you probably know, the latest and greatest in web application technology is Single Page Application (SPA) architecture. Examples include [Meteor](https://github.com/ethereum/wiki/wiki/Dapp-using-Meteor), which plays very well with Reactive approaches to programming a complex webapp. As a result, you can build your web page, then package it up into a single file, and then publish it to Swarm or IPFS. This process still isn’t as easy or seamless as it should be and will be soon.

Your users will access your DApp with “www” if you host it on a centralized server (such as DigitalOcean or Amazon S3 or whatever), and with “bzz://” for Swarm, or “file://” for IPFS.

If you publish your front end in a decentralized way, your DApp really is full-stack decentralized, with both front and back ends being served from peer-to-peer networks. There are [many reasons](https://blog.ethereum.org/2014/08/18/building-decentralized-web/) to prefer developing with such an architecture, including safety, in some cases speed, and resilience to network attacks or downtime.

### Hope this helps!

Because there aren’t many explicit discussions of web-app vs. DApp hosting and architecture, we just wanted to provide some background information which will aid in understanding future, more practical, tutorials.
