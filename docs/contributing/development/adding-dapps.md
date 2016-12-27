# Adding DApps

In order to add a new DApp to Status.im, you need to submit a pull request with the following:

1. Place a nice icon of your DApp to `images/contacts` directory. The file should be called the same way as your DApp, for example `my-dapp.png`;
2. Add information about this icon to `src/status_im/resources.cljs`, for example, like that:

    ```clojure
    (def contacts
      {:auction-house (js/require "./images/contacts/auction-house.png")
       :my-dapp (js/require "./images/contacts/my-dapp.png")})
    ```

3. Add your DApp to the list of existing DApps (`resources/default_contacts.json`):

    ```js
    [
        ...,

        {"id": "my-dapp",
         "name": "My DApp",
         "photo-path": "contacts://my-dapp",
         "dapp?": true,
         "dapp-url": "http://link-to-your-dapp.com"}
    ]
    ```
