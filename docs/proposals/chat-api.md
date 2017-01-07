# Chat API 

## Interface Anatomy

This anatomy establishes the different sections of the chat interface and establishes a common verbiage. The main components being:

- Message
- Input
- Keyboard
- Suggestions

![](img/chat-anatomy.png)

## Commands

!init (hidden)  
    - if it exists run on open chat session, only in 1-to-1 chats.  
!help  
!settings

### Explicitly calling commands

DApps are namespaced with @dappname!command, which can be useful if same commands used by multiple bots are available, alternatively these can be used for commands when bot is not actually in the chat, ie @wallet!send

## Custom Keyboards

Parameters use custom keyboards (instead of types, we adapt our types to be keyboards themselves?)  

Make our emoji/sticker market with this, otherwise accessible through commands
ie !init command with param that opens up a config

## Messages

- subscription to message feed
- api for sending messages, and setting things like "typing"
- not available in group

## Privacy

- by default does not receive all messages in group chat
- only commands and in 1-to-1