deck.js-packed
==============

A single-file version of deck.js with some extensions.

This can be convenient if you want any of:
- a single-file release of [deck.js](https://github.com/twitwi/deck.js) to copy in a project,
- a faster-loading submodule to use in your presentations hosted on github pages.

See also https://github.com/twitwi/deck.js-starterkit that uses this version but provides also a tutorial presentation.

## Step 1 (option 1): as a single file

Get the latest version (or another version) from github.
Download and save the file next to your HTML file:
- most recent: profile-7, adds savedom → <https://raw.githubusercontent.com/twitwi/deck.js-packed/master/deck-packed.js>
- previous: profile-6, smartdown → <https://raw.githubusercontent.com/twitwi/deck.js-packed/3703ca53bff2cec6f4ff0d329c1738f6f61c3be0/deck-packed.js>
- previous: profile-5, smarkdown → <https://raw.githubusercontent.com/twitwi/deck.js-packed/ec861260d7e16cfbb9a3dc11e6551ebc437c8610/deck-packed.js>


## Step 1 (option 2): as a submodule (e.g., for gh-pages)

In your project, just run:

    git submodule add https://github.com/twitwi/deck.js-packed.git

To eventually see it on [github pages](https://pages.github.com/), you'll need to commit and push these to your gh-pages branch.

## Step 2 (option 1): include in an existing presentation

First, you need to include the custom version instead of the deck.js loader:

    -	<script src="deck.js/extensions/includedeck/load.js"></script>
    +	<script src="deck.js-packed/deck-packed.js"></script>

Then, you should remove the profile as it is present in the packed version:

    includedeck([
    -    "profile-7",
       "theme.css"

## Step 2 (option 2): start from zero

See the starter kit: https://github.com/twitwi/deck.js-starterkit


# Notes on how the packed version is built

    git clone https://github.com/twitwi/deck.js tmpdeck
    git -C tmpdeck/ pull
    node ./tmpdeck/extensions/bundle-maker/make-packed.js profile-7 deck-packed.js
    sed -i -e 's@/.*/tmpdeck//*@..../@g' deck-packed.js*
