# Testing

Shake your phone and submit bug report.
Please try to be as descripive as possible.


## For Developers

To run appium tests:

1. install appium `npm install -g appium`
2. start appium server in new tab `appium &`
3. start application on emulator or real device
4. run tests `lein test`

To run unit tests execute:

`lein doo node test once`     
     or  
`lein doo node test`

Second command will watch files inside `src` and `test` folders and rerun on changes.