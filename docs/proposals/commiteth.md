# Commiteth

Commiteth aims to incentivise development on open source projects hosted on Github.

[commiteth.com](http://commiteth.com)  
[github.com/status-im/commiteth](https://github.com/status-im/commiteth)

## How does it work?

Commiteth fosters open source development by incentivising pull request submissions by attaching a ETH or ERC20 cryptotoken bounty to open issues.

A project maintainer must first add their project to Commiteth, and include their address (this address & Commiteth's address will be the two signatories on the multisig wallet).

Once done, Commiteth will list the project and crawl it's Github Issues with the label `bounty`. When found Commiteth will deploy a Multisig wallet to the network with itself and project maintainer as signatories.

Commiteth will then generate an image containing the address, a QR code of the address and the balance of the wallet and comment on the issue. (as well as this information in plaintext). Commiteth will update this comment with a new image everytime the balance has changed and when the bounty is complete.

[![An example bounty image](img/commitethbounty2.png)]( "An example bounty image")  

Commiteth observes the repository for pull requests that contain a reference to the `bounty` issue by the use of the Github special "`fixes #6`" feature. Read more about [Closing Issues via Pull Requests here](https://github.com/blog/1506-closing-issues-via-pull-requests).

When this pull requests are accepted and merged, Commiteth will sign a transaction in the associated wallet and display it to the maintainer as a pending transaction to sign.

The maintainer must load commiteth.com in Mist or Metamask to complete the transaction.

## How do I use it?

First you must sign-in to Commiteth via a Github login. Then you must submit your receiving address. 

Once done you are ready to submit pull requests for issues with the `bounty` tag. 

If your pull request is accepted, Commiteth will sign the bounty balance to you, however you must wait until the maintainer confirms the transaction.
 