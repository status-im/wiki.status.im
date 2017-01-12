# CommitETH

Commiteth is a Github Bounty Bot that allows 

so the idea was that maintainers would add their repos the to bot, the bot would then crawl issues with "bounty" tag,

[9:47]  
when it found one thats open, it would deploy a multisig wallet to mainnet and generate an image, make a comment of the issue with the address and a qr code

[9:48]  
the problem with this is that commiteth has to monitor these multisig wallets for balance updates and then re-comment/update the comment with a new image

[9:48]  
since we wanted to display the balance in the image

[9:51]  
basically any contributor that wanted to receive a bounty would have to sign in with github to commiteth

[9:51]  
and submit an address

[9:51]  
then when a PR is made that auto closes the issue when merged, commiteth would sign the multisig wallet and display it to the maintainer, and the maintainer would have to sign it as well

[9:51]  
which would release the funds

[9:52]  
the implementation is a little naive but at least this way theres isn't too many moving parts and funds can't be easily stolen or hacked

tpatja [9:53 PM] 
I see.. so polling the wallets is basically required with current approach. do you think it’s an acceptable quirk in how it works, if we   make the comment updating work?

jarradhope [9:55 PM] 
well i doubt we're going to have 10,000's of issues to deal with

[9:55]  
i didn't like something with the way dmitry had implemented the current version

[9:55]  
but i can't remember what it was

[9:56]  
theres also a problem with http://commiteth.com/#/manage in that it doesn't list the repositories of the organisations

[9:56]  
so i can't add it to `status-react`

[9:57]  
you can see what the graphic looks like atm, https://github.com/kagel/test/issues/6
GitHub
First sync takes days too complete both on testnet and public chain · Issue #6 · kagel/test · GitHub
Contribute to test development by creating an account on GitHub.
 