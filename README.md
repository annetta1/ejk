> Write common sides and differences between merge and rebase commands.

## Similarities

* Git rebase and merge both integrate changes from one branch into another.
* In both merge and rebase conflicts can occur that need manual resolution.
* There is no difference in the final product of the integration.

## Differences

* Rebase takes all the changes that were committed on one branch and replays them on a different branch.
* The log of a rebased branch looks like a linear history.
* Rebase creates a whole new series of commits, as a consequence of this, it rewrites history.
* Merge adds a new merge commit.
* Merge performs a three-way merge between the two latest branch snapshots and the most recent common ancestor of the two, creating a new snapshot (and commit).
* Merge preserves the history of a branch as it happened.

> Write pros and cons for merge and rebase. Describe situations for preferably usage of these commands.

## Pros and Cons of rebase

### Pros

* Streamlines a potentially complex history. History stays linear and readable.
* The neat flow of commit messages makes it easier for developers to track a bug when a new feature was introduced.

### Cons

* Rebase produces more conflicts, because individual commits in the topic branch can each involve merge conflicts which must be individually resolved.
* Reverting a rebase is considerably more difficult compared to reverting a merge.
* Rewriting of history is bad for teamwork.

## Pros and Cons of merge

### Pros 

* Maintains the original context of the source branch.
* The commits on the source branch are separated from other branch commits.
* Preserves complete commit history and chronological order.
* Merge conflicts only have to be resolved once (at the point of the merge).

### Cons

* History can become intensely polluted by lots of merge commits because multiple people are working on the same branch in parallel.
* Visual charts of repository can become a chaos and don’t provide clear information.
* Debugging using git bisect can become much harder due to the merge commits.

## Preferably usage of these commands

Developer can use rebase to make sure that commits will apply cleanly on a remote branch. In this case, developer is doing his work in a branch and then rebases his work onto origin/main when he is ready to submit patches to the main project. That way, there is no need to do any integration work — just a fast-forward merge.

This way developer avoids a potential problem related to rebase when the branch he is rebasing has already been published remotely, and someone else has based their work on it. Then, developer’s rebased branch can cause serious confusion for all team because developers will have inconsistent repositories.

If for development team true representation of sequence is more important, they would merge without rebasing.
