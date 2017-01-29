# Testing

Shake your phone and submit bug report.
Please try to be as descripive as possible.


## For Developers

### UI (Appium) tests

To run the tests:

1. Install appium: run `npm install -g appium`
2. Start application on emulator or real device ([more details here](https://wiki.status.im/contributing/development/building-status/#build-and-test))
3. Start appium server in new tab: run `appium --session-override`
4. Run `lein test`

Hints / Gotchas:

- Confirmed working using Appium version 1.6.1.
- To find an element easily in the tests, use the `:accessibility-label` property in the respective Reagent component.
- When querying an element by its inner text, be sure to use the whole text that the element is supposed to contain (it won't match just a part of the text).

### Unit tests

To run the unit tests execute:

`lein doo node test once`     
     or  
`lein doo node test`

Second command will watch files inside `src` and `test` folders and rerun on changes.
