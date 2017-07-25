# Running tests

### Unit tests

We have two separate test bundles:

* Run `lein test-cljs` to execute unit tests for models and utility methods.
* Run `lein test-protocol` to execute unit tests for protocol-related method (see `status-im.protocol` namespace).

Both commands execute tests only once. If you're developing tests and want to re-run them each time you change something in code (inside `src` and `test` folders), you can run the following commands:

* `lein with-profile test doo node test`
* `lein with-profile protocol doo node test`

### UI tests

Prerequisites:

1. Install Appium by running `npm install -g appium`
2. Build and start the application on emulator or real device ([more details here](https://wiki.status.im/contributing/development/building-status/#build-and-test)). **Important:** use the _android-test_ build (run `BUILD_IDS="android-test" lein repl`). Testing in iOS is not supported yet
3. Start appium server in new tab: run `appium --session-override`
4. Run `lein test`

Hints / Gotchas:

- Confirmed working using Appium version 1.6.1.
- To find an element easily in the tests, use the `:accessibility-label` property in the respective Reagent component.
- When querying an element by its inner text, be sure to use the whole text that the element is supposed to contain (it won't match just a part of the text).
