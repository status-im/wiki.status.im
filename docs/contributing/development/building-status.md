# Building Status

This document is the entry point for developers of Status. This guide is for anyone who is interested in building, developing, debugging or submitting a bug report, pull request or contributing to Status with code.

This guide is written with OS X in mind.

## Build and Run

### Requirements

- [Homebrew](http://brew.sh/) + `brew update` (optional, for OS X) + `brew tap caskroom/cask`. For Windows use [Chocolatey](https://chocolatey.org/).
- [Node & NPM](https://nodejs.org/en/) `brew install node watchman`
- [Lein](http://leiningen.org) `brew install leiningen`
- [react-native](https://facebook.github.io/react-native/docs/getting-started.html) `npm install -g react-native-cli`
- [Latest JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) `brew cask install java`
- Android SDK with build tools version 23.0.1 [Mac] `brew cask install android-sdk` or [Windows/Linux](https://developer.android.com/sdk/installing/index.html)
- [Genymotion](https://www.genymotion.com) (optional, you may use an Android Virtual Device or real device)
- [Setup Android Development Environment / Simulator](https://facebook.github.io/react-native/docs/android-setup.html)
- GIT over SSH, please add public key to Github
- [Maven](https://maven.apache.org/install.html) `brew install maven`
- For Windows, [Ruby](https://www.ruby-lang.org/en/) `choco install ruby`
- [Cocoapods](https://cocoapods.org) `sudo gem install cocoapods`.

#### Windows-specific Setup Notes
Setting up a development instance in Windows requires some tweaks. Consider the following before attempting the following sections:

- Make sure you run everything in a elevated command prompt (Right-click a link to Cmd.exe or Cygwin and click 'Run as Administrator')
- Do not use the ./re-natal symlink. Write your own `re-natal.sh` script that uses full relative paths, give it execution permissions with `chmod +x`, and use it instead. Script:
```
#!/usr/bin/env node

require('coffee-script/register');
require('./node_modules/re-natal/index.js');
```
- In the root `package.json` edit `"./postinstall.sh"` to `"postinstall.sh"`
- Any `npm install` commands (except for `npm install -g` global commands) should be done as follows, to avoid windows symlink problems: `npm install --no-bin-links`
- Do not use Cygwin for `npm install` commands, use cmd.exe.
- React-native is not bug-free. If you run into an error like `error: bundling: UnableToResolveError: Unable to resolve module...`, the guaranteed solution is to manually edit the `require()` statements to the full relative path. E.g. `(crypt = require('crypto'))` becomes `(crypt = require('../../../../node_modules/crypto/package.json'))`.

### Dependencies & Setup
    $ git clone git@github.com:status-im/status-react.git -b master && cd status-react
    # or
    $ git clone git@github.com:status-im/status-react.git -b develop && cd status-react

    $ lein deps && npm install && ./re-natal deps && ./re-natal use-figwheel && lein re-frisk use-re-natal && ./re-natal enable-source-maps
    $ mvn -f modules/react-native-status/ios/RCTStatus dependency:unpack
    $ cd ios && pod install && cd ..

### Building Status for Release
    # fill in store file properties in android/gradle.properties
    $ lein prod-build
    $ react-native run-android --variant=release
    # for iOS, build in Xcode

### Building Status for Development
    $ lein prod-build

    $ ./re-natal use-android-device <device> # (genymotion, real or avd)
    # or
    $ ./re-natal use-ios-device <device> # (simulator or real)

    $ ./re-natal use-figwheel

    # new tab, run figwheel REPL
    $ BUILD_IDS="ios,android" lein repl

    # new tab, run react native packager
    $ react-native start

    # FOR ANDROID
    # new tab, enable communication to react-native, figwheel and re-frisk debugging
    $ adb reverse tcp:8081 tcp:8081
    $ adb reverse tcp:3449 tcp:3449
    $ adb reverse tcp:4567 tcp:4567
    $ react-native run-android

    # FOR IOS
    $ react-native run-ios

## Access Geth on Device

    adb forward tcp:8545 tcp:8545
    build/bin/geth attach http://localhost:8545

## Contributing

Please make sure your contributions adhere to our coding guidelines:

 * Code must be idiomatic Clojure, please refer to the [style guidelines](https://github.com/bbatsov/clojure-style-guide) (i.e. use [lein eastwood
](https://github.com/jonase/eastwood) & [lein kibit](https://github.com/jonase/kibit)).
 * Code must be documented.
 * Pull requests need to be based on and opened against the `develop` branch.
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

Pull Requests should by default use the `develop` branch as a base. The `master` branch is kept stable and `develop` is periodically merged there. Tags are used for releases. Each Pull Request must be rebased against `develop` and squashed into a single commit.

### Commit messages

Commit message should help understand why (and what) has been fixed. Add a summary as first line if the message is too long.
When fixing bugs the first line should be prefixed with `[FIX #123]`.

As a good practice message starts with capitalized verb in the imperative mood.

### Walkthrough

Fork the repository on Github's web UI.

Clone your fork. Add the upstream as a remote.

    $ git clone git@github.com:<you>/status-react.git
    $ git remote add upstream git@github.com:status-im/status-react.git

Now you have two remotes: `origin` pointing to your fork and `upstream` pointing to the shared repo.

    $ git fetch --all

Then isolate the bug/feature work you will do into a topic branch

    $ git checkout -b bug/missing-contact-#116 upstream/develop

Keep your branch fresh against upstream

    $ git fetch upstream
    $ git rebase upstream/develop

If multiple people are working on the same feature branch don't forget to also

    $ git rebase upstream bug/missing-contact-#116

When you are ready to make your pull request

    $ git push origin

After PR has been reviewed do a final cleanup and squash your commit

    $ git rebase -i upstream/develop
    $ git push -f origin

## Repository Overview

The Status application is divided into 6 core repositories;

- [status-react](https://github.com/status-im/status-react) - our main react native application writtein in Clojurescript, Java & Objective C

- [go-ethereum](https://github.com/status-im/go-ethereum) - our branch of `go-ethereum` which contains our custom modifications in `go-ethereum/status-develop`

- [status-go](https://github.com/status-im/status-go) - represents our binding to the `go-ethereum` lib and exposes methods to `status-react` to Java / Objective C.
