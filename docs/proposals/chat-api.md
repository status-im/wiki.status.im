# Chat API 

## Interface Anatomy

This anatomy establishes the different sections of the chat interface and establishes a common verbiage. The main components being:

- Message
- Input
- Keyboard
- Suggestions

![](img/chat-anatomy.png)

## Accessing a bot

`/global` (hidden)
Universal command for the bot, allows the bot command to be referenced in any chat via `@botname`. If this exists it should appear in the command list as another section at the bottom. 

`/init` (hidden)  
Run on open chat session, only in 1-to-1 chats.  

`/<command>` bots can register a command handler of any ASCII title, which then Status repeats

`@botname/command` if there is multiple bots in a chat context, then the `@botname` can be used to make the distinction (or alternatively a suggestions/commands list should appear to help with the distinction)

`Bot Message` a bot can send a message that can only be read by another instance of itself in chat history. This message can send markup to draw and contain data. It is activated by a user tapping on it.

`A message parsed from chat history` on 1-to-1 chats, any message the user send can be read by the bot and can activate code via `status.on('chat-update', function () { ... } );` handler.

## Bot Messages

A Bot Message can contain it's own markup and a data payload, this message can be transmitted to the chat context. If it is interactable then the interaction (what we currently call response handler) handles the message when tapped. 

**If the user does not have the bot installed, then we display a custom keyboard that shows the bot name, its reviews/ reputation and a "Install / Add to Contacts" button, which the user can either cancel or install and continue with response flow.**


## Command Handlers

Once a command handler is invoked it is passed the current text / data payload of the message, and is required to return the paramaters (and their placeholder information). The return of the handler must include 
- `markup` or a `status component(data)` for the suggestions area 
- `markup` or a `status component(data)` for the the keyboard
- an error object
- the revised text / data payload.

## Privacy

- a bot can only be interacted with via commands or messages via in 1-to-1 chats
- a bot can only see messages from itself and the current user in group chats.


## Deployment & Testing

Console should have some `/debug` mode that allows the user to plugin their phone in and hot-load javascript/webpage to make testing web-based dapps or bots easily from desktop. Ideally it should have integration with [Truffle](http://truffleframework.com/) & [Embark](https://github.com/iurimatias/embark-framework) and pay respect to [EIP190](https://github.com/ethereum/EIPs/issues/190)

## Open Questions

Is there an issue of resources  and conservation around Otto VM jails?
Should it runs per dapp per chat context? or per DApp and then an object in each per chat context?

