Manage subtrees manually
========================

A lean approach to managing git subtrees [manually][mastering-subtrees].
Because git-subtree clutters the history graph and [git-stree][stree]
still does too much for me.

I wanted the simplest possible solution that does not require anything
special and that does not modify a repository beyond what's required
for the most basic approach.

So you _may_ use this script to manage a subtree. But your repository
won't depend on it.

Samples
-------

Adding a subtree:

	$ git sub add https://github.com/you/component.git

This clones the repository "component" into the directory "component".
The directory is now in the staging area and ready to be committed.
git-sub won't make any commits.

Later, when you want to update the "component" subtree do:

	$ git sub update component

The updated files are now in the staging area and can be committed.

Usage
-----

	usage: git sub add    <repository> <prefix>
	   or: git sub update <remote>

Use the optional prefix argument to put the repository into a subfolder.
By default, repositories are put into the parent repository's root folder.

Cloning
-------

Remotes don't get cloned. So after a repository is cloned, you need to
add the remotes for the subtrees again:

	$ git remote add component https://github.com/you/component.git

After that, you can use git sub update as before:

	$ git sub update component

[mastering-subtrees]: https://medium.com/@porteneuve/mastering-git-subtrees-943d29a798ec
[stree]: https://tdd.github.io/git-stree/