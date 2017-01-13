# Translations

Special thanks to [@cryptowanderer](https://twitter.com/cryptowanderer) for contributing this fantastic guide!

Thank you for taking the time to help out with our fledgling free (libre) open source project. Any initiative like this depends primarily on the community that forms around it, so by contributing any of your knowledge or skills, even if it’s just one line, you are playing an active role in forming the sort of decentralized, robust peer network which might have a hope of securing a more equitable future for all of us.

Obviously, the first and most important thing to know about contributing in any way to the wonderful status.im is where to go to find all the stuff. That one is easy to answer: [click here](https://github.com/status-im/status-react/tree/develop/src/status_im/translations).

Now, git is very cool, and there are ways to use the command line to do all this stuff, but if you’re doing that then I am going to assume that you don’t need a guide, or can find a better one than this on your own. This will only cover submitting a pull request (PR) through the browser and is aimed specifically at those wanting to help us with translations who might not be actual coders themselves.

The page with all the translations listed on it should look something like this:

<center><img src="../img/image_0.png" style="width:100%" /></center>

If you can see a file for your language already, then click on that and we can submit the PR from there. You can skip the next section and go straight to the last one if you are just updating an existing file. If you are starting a new file for a language not currently listed, please click the `Create new file` button highlighted in the top right.

## Start a New Translation

If you are creating a new file, this is what the page should look like:

<center><img src="../img/image_1.png" style="width:100%" /></center>

There are some important things to note here. First off, I have decided to help out with the translation to Wooki, so have called my file wo.cljs. Please give the two letters used to represent your language and make sure to include the .cljs file extension (as a lot of status is written in clojure and clojurescript). If your language doesn’t have a two letter identifier, or you are doing a dialect, then use the fr_ch.cljs example as your template. Second, make sure that you update the first line. In this example, I have copy-pasted the Afrikaans file and changed .af to .wo to match what I called my file.

You can then get translating - as you can see by my exact translation of members-title to the Wooki equivalent.

Once you’ve done all the translations, all you really need to do is propose the file, review the changes you have made, submit the PR and the team should be able to handle it from there. Please see below for a fully illustrated version of those last two steps if you need it.

<center><img src="../img/image_2.png" style="width:100%" /></center>

## Update an Existing Translation

If your language already appears in this repo, but you would like to see some stuff change because it’s wrong or impolite or gets its tense all mixed up, then click on the file in question and submit a PR from there. Seeing as I’m South African, I’m going to take on the Afrikaans translation and submit a PR which the team will then decide to merge or not, depending on how *lekker* they think my *taal* is.

You want to select the file and then click on the pencil edit icon near the top right:

<center><img src="../img/image_3.png" style="width:100%" /></center>

This should open a file on your fork of the project, which will allow you to edit it as you please and submit the changes to the status team, who can review it, decide if they like your changes and then merge it back from your newly-created fork into the main repo. I know it sounds a bit complex, but this is awesome for versioning software, controlling changes, edits, and conflicts and makes much more sense once you do it a bit yourself. Your edit page should look something like this:

<center><img src="../img/image_4.png" style="width:100%" /></center>

As I have indicated, I am going to edit "en jy" to “en u” because it is more formal and polite (if you speak Afrikaans, you know that this is contextually incorrect, but bear with me while I illustrate the concept here).

Once you are happy with all the changes you have made, scroll down and hit the green button to propose them. This should take you to a screen where it will highlight in red what the file used to say and highlight in green what you have changed it to. Please review your changes here in full and then hit the other green button in the top left to submit the PR:

<center><img src="../img/image_5.png" style="width:100%" /></center>

And that’s it. Now sit back, have a cup of tea, and let the rest of the black magic that is status.im do its thing.

