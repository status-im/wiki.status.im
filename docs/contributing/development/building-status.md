# Building Status

This document is the entry point for developers of Status. This guide is for anyone who is interested in building, developing, debugging or submitting a bug report, pull request or contributing to Status with code.

This guide is written with OS X in mind.

## Build and Test

### Requirements
- [Homebrew](http://brew.sh/) + `brew update` (optional, for OS X)
- [Node & NPM](https://nodejs.org/en/) `brew install node watchman`
- [Lein](http://leiningen.org) `brew install leiningen`
- [react-native](https://facebook.github.io/react-native/docs/getting-started.html) `npm install -g react-native-cli`
- [Latest JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) `brew cask install java`
- Android SDK with build tools version 23.0.1 [Mac] `brew install android-sdk` or [Windows/Linux](https://developer.android.com/sdk/installing/index.html)
- [Genymotion](https://www.genymotion.com) (optional, you may use an Android Virtual Device or real device)
- [Setup Android Development Environment / Simulator](https://facebook.github.io/react-native/docs/android-setup.html)
- GIT over SSH, please add public key to Github
- [Maven](https://maven.apache.org/install.html)
- [Cocoapods](https://cocoapods.org) `sudo gem install cocoapods`

### Dependencies & Setup
    $ git clone git@github.com:status-im/status-react.git -b master && cd status-react
    # or 
    $ git clone git@github.com:status-im/status-react.git -b develop && cd status-react

    $ lein deps && npm install && ./re-natal deps
    $ mvn -f modules/react-native-status/ios/RCTStatus dependency:unpack
    $ cd ios && pod install && cd ..

### Building Status for Release
    # fill in store file properties in android/gradle.properties
    $ lein prod-build
    $ react-native run-android --variant=release
    # for iOS, build in Xcode

### Building Status for Development

    $ ./re-natal use-android-device <device> # (genymotion, real or avd)
    # or
    $ ./re-natal use-ios-device <device> # (simulator or real)

    $ ./re-natal use-figwheel

    # new tab, run figwheel REPL
    $ BUILD_IDS="ios,android" lein repl

    # new tab, run react native packager
    $ react-native start

    # new tab, enable communication to react-native and figwheel
    # for android
    $ adb reverse tcp:8081 tcp:8081
    $ adb reverse tcp:3449 tcp:3449
    $ react-native run-android

    # for ios
    $ react-native run-ios

## Access Geth on Device

    adb forward tcp:8545 tcp:8545
    build/bin/geth attach http://localhost:8545

## Contributing

Please make sure your contributions adhere to our coding guidelines:

 * Code must be idiomatic Clojure, please refer to the [style guidelines](https://github.com/bbatsov/clojure-style-guide) (i.e. use [lein eastwood
](https://github.com/jonase/eastwood) & [lein kibit](https://github.com/jonase/kibit)).
 * Code must be documented.
 * Pull requests need to be based on and opened against the `master` branch.
 * Commit messages should be prefixed with the root namespace(s) under `status-im` that they modify.
   * e.g. "contacts, ios: add contact stylistic changes"

###  Issues
Only Github is used to track issues. (Please include the commit and branch when reporting an issue.)

[Overv.io](https://overv.io/~/status/) is used to overview issues in multiple repositories.

### Code formatting

Please run `lein eastwood` and `lein kibit` before contributing.

### Branch naming

Branch format must be under `CATEGORY/PLAIN-TEXT-#ISSUE_NUMBER` acceptable branches are;

`feature/discover` or `bug/broken-form-#113`

The following categories are;
- `feature/` for implementation of features
- `bug/` for fixing bugs
- `tests/` for unit/UI tests
- `experiment/` for non-features
- `wip/` for longer lived branches
- `junk/` for irrelevant/soon-to-be-deleted branches

### Pull Requests

Pull Requests should by default commit on the `master` branch. The `master` branch is used for history, tags for releases. Each Pull Request must be rebased against `master` and squashed into a single commit, prefixed with the root namespace(s) under `status-im` that they modify. e.g.
> "contacts, ios: add contact stylistic changes"


### Walkthrough

Start by first pulling down `master`

    $ git checkout master
    $ git fetch origin
    $ git merge master

Then isolate the bug/feature work you will do into a branch;

    $ git checkout -b bug/missing-contact-#116

Keep your branch fresh against master

    $ git fetch origin
    $ git rebase origin/master

If multiple people are working on the same feature branch don't forget to also

    $ git rebase origin bug/missing-contact-#116

When you are reading to make your pull request;

    $ git push bug/missing-contact-#116

After PR has been reviewed do a final cleanup and squash your commit

    $ git rebase -i origin/master

## Repository Overview

The Status application is divided into 6 core repositories;

- [status-react](https://github.com/status-im/status-react) - our main react native application writtein in Clojurescript, Java & Objective C

- [go-ethereum](https://github.com/status-im/go-ethereum) - our branch of `go-ethereum` which contains our custom modifications in `go-ethereum/status-develop`

- [status-go](https://github.com/status-im/status-go) - represents our binding to the `go-ethereum` lib and exposes methods to `status-react` to Java / Objective C.
- [status-lib](https://github.com/status-im/status-lib) - implements our application protocols for chatbots, has been absorbed into `status-react` until application protocol settles
- [react-native-status](https://github.com/status-im/react-native-status) - the intent behind this repo was to seperate Java/Objective C code into a react native module, it may be absorbed into `status-react` in future
- [status-server](https://github.com/status-im/status-server) - is our intermediary server primarily used for contact discovery.