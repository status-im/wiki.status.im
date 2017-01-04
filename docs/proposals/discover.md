# Discover

This document describes the Discover feature of Status. Ethereum is its community, and with Discover we want to connect other Ethereum users with other Ethereum users - to trade and exchange ideas. Ultimately this will reduce transaction costs and increase the utility of ETH.

Discover is done through a users Status (hence the application name). This status is a 140 char sub-headline to a users profile which can be seen on [my profile](https://zpl.io/22nSfB), [user profile](https://zpl.io/CFBa8) and [discover](https://zpl.io/Z1p9XlV) screens.

A status is private and not shared with anyone except their immediate contacts, unless a **#hashtag** is introduced. These #hashtags are locally searchable on the discover screen.

The Discover application protocol is built ontop of Whisper, possibly utilising our messaging protocol and is implemented in [status-im/status-lib](https://github.com/status-im/status-lib/tree/master/src/cljs/status_im/protocol)

Periodically the client should request from it's contacts, a package of statuses that is an aggregate compilation of discoverable statuses (created using the specifications below), this package should contain no more than 100-500 statuses and the period in which the client requests the package is after when the user is back online and/or after waiting X hours has elapsed. Whisper penalizes larger payloads so we may have to chunk this. `140chars × 4bytes (utf-8) × 100 contacts = 54kb`

The 100 contacts the user decides to return is weighted by;
- the newest available information (latest status from that user),
- the most seen contact statuses by other contacts. (that user who has seen the same contact status from all his contacts)
- and actual interactions with contacts, favor contacts that the user has actually messaged themselves.
- if contact is online

The Discover screen then takes this aggregate search space 
`100-500 statuses × users in contact list` and organise them by #hashtags, the hashtags that have more than X contacts are put into the carousel under that #hastag category.

Below it the statuses are listed by most recent.

On tapping one of these messages a chat session is attempted with that user.

Each user should cache no more than 1000 statuses

