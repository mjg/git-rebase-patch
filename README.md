git rebase-patch
================

Given you have a patch that doesn't apply to the current HEAD, but you know it
applied to some commit in the past, `git rebase-patch` will help you find that
commit and do a rebase.

Usage: `git rebase-patch <patch-file.patch>`

(Note: If the patch has been created with `git format-patch`, it is more
efficient to use `git am`, because that considers meta information from the
patch.)

Example
-------

You can reroll a patch against the current HEAD like this:

    git rebase-patch old-patch.patch

That might give you:

    Trying to find a commit the patch applies to...
    Patch applied to 9d1a78c as 9e22d99
    [master 4d28217] remove-second-paragraph.patch
     1 file changed, 2 deletions(-)

Now your latest commit has the changes of your path. It's message is the patch
file name. Then proceed as usual.

Reroll the patch:

    git diff HEAD~1 > new-patch.patch

Change the commit message:

    git commit --amend

Automated testing
-----------------
[![Build Status](https://secure.travis-ci.org/niklasf/git-rebase-patch.png?branch=master)](http://travis-ci.org/niklasf/git-rebase-patch)
