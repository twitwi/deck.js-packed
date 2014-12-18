deck.js-packed
==============

A single file version of deck.js with some extensions.

This can be convenient if you want any of:
- a single file release to copy in a project,
- a fast-loading submodule to use in your presentations hosted on github pages.

## A) option 1: how to use as a simple file

Get the latest version (or another version) from github.
For example at <https://raw.githubusercontent.com/twitwi/deck.js-packed/master/deck-packed.js> and save it next to your HTML file.

## A) option 2: how to use as a submodule (e.g., for gh-pages)

In your project, just run:

    git submodule add https://github.com/twitwi/deck.js-packed.git

To eventually see it on [https://pages.github.com/](github pages), you'll need to commit and push these to your gh-pages branch.

## B) How to include this version of deck.js in your HTMl presentation

First, you need to include the custom version instead of the deck.js loader:

    -	<script src="deck.js/extensions/includedeck/load.js"></script>
    +	<script src="deck.js-packed/deck-packed.js"></script>

Then, you should remove the profile as it is present in the packed version:

    includedeck([
    -    "profile-5",
       "theme.css"


# Notes on how the packed version is built

    git clone https://github.com/twitwi/deck.js tmpdeck
    node ./tmpdeck/extensions/bundle-maker/make-packed.js profile-5 deck-packed.js
    sed -i -e 's@/home/.*/tmpdeck//*@..../@g' deck-packed.js
