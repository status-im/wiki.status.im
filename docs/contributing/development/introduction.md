# Introduction

In this post, you will learn what the two main languages used in Status are, how to learn them, how to build Status, & finally how to find tasks to work on.

Status is largely written in two languages: Clojurescript & Golang and builds on React Native for UI. I'll talk about the rational behind these design decisions and link to offsite resources on learning each of these technologies.

## React Native

Status (formerly known as Syng) has always aspired to have a single, unified codebase for multi-platform development. This is not so easy to achieve, as many of the non-web-based solutions out there allow you to have a semi-single codebase, but you find yourself creating a lot of seperate logic for handling user interfaces on each platform - Status is 80% frontend code and this presents a problem. We tried Xamarin & Java (EthereumJ was the first implementation we got running on Android & iOS - via RoboVM), and we quickly discovered this problem.

Mobile apps built on web-based technologies, such as those done in Cordova, are great for short-term projects or mvp, but you will quickly run into performance issues on resource-limited devices and may need to rewrite you app. In our tests displaying webview DApps in a chat history with iFrames and all the other bells and whistles we wanted turned out to be a futile effort.

That limited our options to choosing between NativeScript & React Native. We chose React Native because it is more mature and is being used in production for popular apps like **Facebook**, **Instagram**, **Airbnb**, **Baidu** & **Discord**. This gave us the impression that this framework was here to stay with many Fortune 500 companies invested in its continuance.

At this point all we had to do is merge Material & iOS design into our unique look'and'feel so that we could minimise the amount of Android & iOS specific code. Our amazing designer [Andrei Mironov](https://dribbble.com/andmironov) elegantly solved the rest of that puzzle.

### React Native Learning Resources

If you would like to start learning React Native, check out these resources:

- [Use React Native](http://www.reactnative.com/books/)
- [React Native Docs](https://facebook.github.io/react-native/docs/getting-started.html)

Although you might want to continue reading and learn more about [re-natal](#re-natal), [re-frame](#re-frame) & [reagent](#reagent).

## Clojurescript

*“Lisp is worth learning for the profound enlightenment experience you will have when you finally get it; that experience will make you a better programmer for the rest of your days, even if you never actually use Lisp itself a lot.”* — [Eric Raymond](https://en.wikipedia.org/wiki/Eric_S._Raymond).

To read more quotes on Lisp read [Lisp, made with secret alien technology](http://lispers.org/).

[![We lost the documentation on quantum mechanics.  You'll have to decode the regexes yourself.](img/xkcd-224.jpg)](https://xkcd.com/224/ "We lost the documentation on quantum mechanics.  You'll have to decode the regexes yourself.")  

There's alot of resources online about why learning Lisps are so great. For us, it's largely about culture; we like the way Lispers think. We want functional programming, macros, homoiconic code and the flexibility that comes with a simple, unstructured language in which to think. The benefits of this become more apparent in later stage development, where functional language allows us to perform rewrites more easily, isolate many bugs to specific functions, as well as enforcing correct coding. Also, I prefer reading it.

Moreover, with [hiccup](https://github.com/weavejester/hiccup), working with React Native markup becomes a dream.

### Clojurescript Learning Resources

If you would like to start learning Clojurescript, check out these resources:

- [Clojurescript FAQ (for JavaScript developers)](https://github.com/clojure/clojurescript/wiki/FAQ-(for-JavaScript-developers))
- [Clojurescript Community Resources](http://clojurescript.org/community/resources)
- [Clojurescript Unraveled Book (Free)](http://funcool.github.io/clojurescript-unraveled/)
- [/r/clojure](https://www.reddit.com/r/Clojure/) & [/r/clojurescript](https://www.reddit.com/r/Clojurescript/)

## Go

Of all the Ethereum implementations `go-ethereum` has received the most love and implements the newest and best features. Without `go-ethereum` we couldn't use the light client protocol and Status would not be possible. We will also get access to Swarm the fastest. We consume `go-ethereum` as a library in [status-go](https://github.com/status-im/status-go).

'Nough said.

## Re-natal

re-natal is an invaluable tool to that automates the setup of your [re-frame](#re-frame) React Native for Android & iOS, it includes [figwheel](https://github.com/decker405/figwheel-react-native) for easy development.

- re-natal [README.md](https://github.com/drapanjanas/re-natal)

## Re-frame

re-frame is simple but expressive library for writing Single Page Applications in ClojureScript, using [Reagent](#reagent). It is a functional framework for reactive 'MVC-style' applications. To learn more:

- re-frame [README.md](https://github.com/Day8/re-frame)
- re-frame [docs](https://github.com/Day8/re-frame/tree/master/docs#introduction)
- [A Noob's walkthrough of a re-frame Application](http://www.multunus.com/blog/2016/02/noobs-walkthrough-re-frame-app/)
- [The Angular Phonecat tutorial in re-frame](https://dhruvp.github.io/2015/03/07/re-frame/)

## Reagent

[Reagent](http://reagent-project.github.io/) provides a minimalistic interface between ClojureScript and React. It allows you to define efficient React components using nothing but plain ClojureScript functions and data, that describe your UI using a Hiccup-like syntax.
The goal of Reagent is to make it possible to define arbitrarily complex UIs using just a couple of basic concepts, and to be fast enough by default that you rarely have to care about performance.

- [Reagent website](http://reagent-project.github.io/)
- Reagent [README.md](https://github.com/reagent-project/reagent)
- [Building Single Page Apps with Reagent](https://yogthos.net/posts/2014-07-15-Building-Single-Page-Apps-with-Reagent.html)
- [You should be using Figwheel & Reagent. Here's why](http://timothypratley.blogspot.com/2015/07/you-should-be-using-figwheelreagent.html)
- [Reagent Rocks](http://www.mattgreer.org/articles/reagent-rocks/)

## Building Status

[Read our guide on how to Build Status](building-status.md)

## Finding issues to work on

So by now you should have a general sense of the tech that goes into Status, managed to get Status built & running and want to find something to sink your teeth into. 

The best place to look for tasks to work on is our [Github Issues](https://github.com/status-im/status-react/issues). We've labelled the tasks by our estimated difficulty.

**Click the labels below to see what is available.**


## Beginner Issues
<a href="https://github.com/status-im/status-react/issues?q=is%3Aopen+is%3Aissue+label%3Abeginner" target="_blank"><img src="../img/beginner.png" style="height:28px;margin:0"/ ></a>

These are tickets we believe anyone willing to learn Clojurescript can handle. They involve minor UI and localisation changes. Even though they may seem minor that have a huge impact on the usability of Status.

## Intermediate Issues
<a href="https://github.com/status-im/status-react/issues?q=is%3Aopen+is%3Aissue+label%3Aintermediate" target="_blank"><img src="../img/intermediate.png" style="height:28px;margin:0"/ ></a>

Beginner too easy and your Clojure-fu up to par? Time to level up!
These issues require a slightly deeper understanding of what Status is trying to accomplish; an understanding of Ethereum; and more communication and intimacy in the Slack as they are interdependent tasks. They involve things like setting up UI tests, fixing nastier bugs and making decisions that will have a real impact on how Status behaves and functions.

## Advanced Issues
<a href="https://github.com/status-im/status-react/issues?q=is%3Aopen+is%3Aissue+label%3Aadvanced" target="_blank"><img src="../img/advanced.png" style="height:28px;margin:0"/ ></a>

These issues are really there for people deeply into Ethereum, Core Contributors and people who believe in Status and have the skills to make magic happen.
