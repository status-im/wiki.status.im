# Clojurescript

https://github.com/status-im/status-react

## Project Structure (out of date)
1. The structure of the project was changed from
   ```
syng_im
    - handlers.cljs
    - subs.cljs
    - models
    - components
        - chats
        - contatcs
        - react.cljs
```
   to
    ```
syng_im
   - chat 
       - handlers.cljs
       - subs.cljs
       - views
       - styles
       - screen.cljs
   - contacts
      ...
   ....
   - components
   - handlers.cljs
   - subs.cljs
```
So previously `syng-im.handlers` ns contained all handlers, now it is the point where all handlers are required, and the place for very common handlers (like `:set`).
`syng-im.subs` ns contained all subscriptions, but now it has to contain only common handlers, like `:get`. Everything specific to particular feature/screen (like `chat`/`contacts`/`navigation` etc), including specific handlers, subs, views etc. should be placed inside feature's dir. This helps to simplify reasoning about the particular feature by avoiding of mixing of code with unrelated functionality inside one namespace. We still have `components` which will contain common components and views like `text`/`view`/`carousel` etc, that can be used inside other `views`

2. Views must not contain any logic related to control on applications data (changing of state, specific validation/checks of data etc...). The only way to work with app-db inside views is to subscribe to particular data from app-db and dispatch events to handlers.

3. Styles. Views should be free of styles definitions but only reference to them. Everything related to presentation should be moved to `feature.styles`/`components.component-name.styles` ns. If there is any logic related to the presentation which should be computed based on data it is fine to write a function which will take that data as parameters and return styles.

4. Handlers. The idea is to keep handlers pure as far as it possible and don't mix code that contains side-effects with code that is pure. The code that contains `side-effects` shouldn't contain any application's logic. It means that if we have handler like
   ```
(register-handler  :load-messages
    (-> load-messages!
         ((enrich add-messages)))))
   ```
everything related to applications logic (like processing of messages after loading, adding messages to app-db, etc) should be placed inside `add-messages` function, when `load-messages!` only contains a call to external api/db/whatever outside app-db. In this case, all handlers which contain applications logic are pure and that means that they are testable (I hope we will get to tests once).

5. Subs. Nothing specific. Just keep them in right namespaces.

**Common things:**

1. Namespaces should not contain all other namespaces in `require` form. Just keep there namespaces/refers that are really used.

2. Models shouldn't contain any logic wich not related to fetching data from db. 

3. There is no need to gather "paths" inside `syng-im.db` ns. This only leads to coupled code with a lot of senseless references. For instance to code like this
   ```
   (register-handler :change-message
     (fn [db [_ message]]
       (change-message db message)))

(defn change-message [db message]
     (assoc-in db (message-path (get-current-chat-id id)) message))

(defn message-path [chat-id]
     [:chats chat-id :message])

(defn get-curent-chat-id [db]
     (get-in db current-chat-id-path))

(def current-chat-id-path :current-chat-id)
```
where these functions are placed in three different namespaces, when it can be just
   ```
(register-handler :change-message
     (fn [{:keys [current-chat-id] :as db} [_ message]]
       (assoc-in db [:chats current-chat-id :message] message)))
```

4. Specific properties that are used everywhere for same components better to move to components definition than to repeat each time when a component is used. Like `:underlineColorAndroid :transparent` for `text-input`

And so on... Other things are more related to Clojure, not to application's or `re-frame`'s architecture.