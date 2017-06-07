# Documenting

Without clear documentation, new members to the community have no clear instruction on how they can help to make Status better. We truly value contributions that help to improve our documentation; whether that be tutorials for users, additions to the FAQs, or more granular instructions for developers - it all adds up and our community appreciates it :)

Our Wiki is powered by MKDocs, and is on: [https://github.com/status-im/wiki.status.im](https://github.com/status-im/wiki.status.im), and if you spot any errors, find parts of the documentation confusing, or have some suggestions on how we could have clearer communication we'd love your help, and feel free to let us know via the [Status Slack](http://slack.status.im).

## Documenting Guide  

It's fairly difficult to write a general documentation guide as how you document stuff will depend on what it is you are trying to explain. The most basic stuff to know is that MKDocs uses markdown as it's primary language, although you can also write your guides using inline HTML as well. Please go [here](http://www.mkdocs.org/user-guide/writing-your-docs/) for more detailed info on this, as well as a look at how the file structure of our docs works.

## Getting Set Up

You need to have both python and pip set up on your machine to install MKDocs. You can find all the information for how to do that and what versions are required [here](http://www.mkdocs.org/). I had python already installed on my machine, but needed to get pip:

```
sudo easy_install pip
sudo pip install mkdocs
```

It seemed like using `sudo` was important otherwise the mkdocs install failed with some nasty stack trace, but that may have been specific to my environment (Mac). Once you have got that all working and  

`mkdocs --version` 

returns an answer (currently `mkdocs, version 0.16.1`), then you can clone into the status repo and get going.

`git clone https://github.com/status-im/wiki.status.im.git` 

(or `git clone git@github.com:status-im/wiki.status.im.git` if you have your SSH keys set up) followed by 

```
cd wiki.status.im
mkdocs serve
```

You should then be able to navigate to http://localhost:8000 or http://127.0.0.1:8000 and see the changes you are making to the wiki as you make them. Magic!

## General Notes on What We Look For

Generally speaking, we like a lot of screenshots and less language as this helps us to guide people all over the world who may not all speak the same languages. Take a look at our [User Guide](http://wiki.status.im/getting-started/user-guide/) for a rough outline of what we mean by balancing your text with screenshots and other helpful images. 

As you can see from our [github repo](https://github.com/status-im/wiki.status.im) all of the different documents are kept in the `docs` directory. Click through to there to find the section and then the specific document you are wanting to add to or edit, or make a new file for documentation that you feel is missing. 

<center><img src="../img/status-wiki.png" /></center>

In the top level repo, you can also see an `mkdocs.yml` file, which is what controls how and where each document appears. If you are adding a new document, you will need to speak to Jarrad, Carl or another team member to figure out where it belongs, but either way you will need to edit this file in order for it to appear. It is definitely best to communicate with the core team before diving this deep though.

As you can see, I have uploaded a bunch of images into this post (which is largely about encouraging you to use lots of images in your own documentation and explainers). The images are all kept in the `img` directory in each folder within the `docs` directory. You cannot upload straight to these `img` folders as that requires push access to the whole repo, but you can make your own fork of `wiki.status.im` and upload the images there to be merged by the team once you have completed your awesome work. To do all this, navigate to the folder you are working in and click the `Fork` option in the very top right. This will start a new fork of the wiki in your own repo, where you can upload the photos and then later push back to status to be merged.

<center><img src="../img/img-location.png" /></center>

Once you have forked it and selected where it should go in your profile, you can then add images easily by either dragging and dropping or uploading directly from your machine.

<center><img src="../img/forking-repo.png" /></center>

You can select the first radio button option to commit the uploaded images you need directly onto your own master branch. From there, once you are sure that all the changes you have made are the ones you want to make and look good on the wiki via that neat trick with

`mkdocs serve`

then you can submit a PR to the actual status wiki:

<center><img src="../img/pull-request.png" /></center>

Click the highlighted button near the top right and follow the instructions from there to submit your changes to the status team. You should see a screen something like this where you can review all the changes you have made before actually submitting. For the PR, I have uploaded the photos needed for this post, made two grammatical changes to the User Guide and, obviously enough, uploaded this entire `documenting.md` file, all of which I can review easily. 

<center><img src="../img/comparing-pr.png" /></center>

Thank you so much for adding to our wonderful, free (libre) open source, community-driven effort to bring Ethereum to the people!

## Documentation Guidelines

These will evolve as the project does, but really depends on what specific type of documentation you are looking to help out with. For technical documentation, examples and lots of code is what we are primarily looking for; by way of example see the first set up section of this article. For instance, in order to add an image here, you can either use inline html (my preferred option because it is easier to position and style) or the normal markdown way of doing things. The images above are inserted like so:

`<center><img src="../img/status-wiki.png" /></center>` 

and style tags etc can be added really easily:

`<center><img src="../img/status-wiki.png" style="width:300px" /></center>`

or you can just do it in normal markdown:

`[![We lost the documentation on quantum mechanics.  You'll have to decode the regexes yourself.](img/xkcd-224.jpg)](https://xkcd.com/224/ "We lost the documentation on quantum mechanics.  You'll have to decode the regexes yourself.")`

If you are writing documentation that is end-user-facing, rather than aimed at the technical folks in our community, then the less code and text and the more pretty images with directions scrawled across them the better.
