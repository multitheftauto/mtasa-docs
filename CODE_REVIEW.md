### Contents:
- [The most important thing](#the-most-important-thing)
  - [Context](#context)
- [Everyone](#everyone)
- [As a code submitter](#as-a-code-submitter)
- [As a reviewer](#as-a-reviewer)
- [Responding to feedback](#responding-to-feedback)

_These aren't necessarily "rules", it is just a guide on how to review code effectively._

It's been often said that programming is part art, part science - that because
lots of times there's no single, simple solution to a problem; or if there is,
we might not know about it. There's also an infamous joke that if there are *n*
developers in the room, then there are *n+1* opinions on how things should be done.
That being said, here are some guidelines that should prevent friction when submitting
or reviewing code.

## The most important thing

**The code has to work.** Unless you open a PR as a work in progress, the code
should be built and tested.

If you have changed build setup, it's useful to test the whole build from
scratch (clean build). If you updated external libraries, test the pertaining
features (e.g. if you updated the JSON library, test that all the Lua JSON functions
work as expected). If you changed the BitStream version, test that your client/server
still works with older/newer servers/clients.

Having people review your code is one thing, but you should not expect them to
also *throughly test* the code for you. 

### Context

One important thing that lots of guidelines forget to mention is the *context*
of the pull request: sometimes it's a big refactor, sometimes it a new feature,
sometimes it's a bug fix. Some of those might be more urgent than the others,
and sometimes the code might not be perfect or extendable. **That's ok.** 

## Everyone

* There is no perfect code: good enough is usually good enough. That being said,
  try to keep the number of WTFs per minute to a minimum.  ![WTFs per minute](https://i.imgur.com/pFQNzHq.png)
* Accept that many programming decisions are opinions.
  Discuss tradeoffs, which you prefer, and reach a resolution quickly.
* Ask good questions; don't make demands ("What do you think about naming this :user_id?").
* Good questions avoid judgment and avoid assumptions about the author's perspective.
* Ask for clarification ("I didn't understand. Can you clarify?").
* Avoid selective ownership of code. ("mine", "not mine", "yours")
* Avoid using terms that could be seen as referring to personal traits ("dumb", "stupid").
  Assume everyone is intelligent and well-meaning.
* Be explicit. Remember people don't always understand your intentions online.
* Be humble. ("I'm not sure - let's look it up.")
* Don't use hyperbole ("always", "never", "endlessly", "nothing"). Don't use sarcasm.
* Keep it real. If emoji, animated gifs, or humor aren't you, don't force them.
  If they are, use them with aplomb.
* Consider talking synchronously (e.g. chat) if there are too many
  "I didn't understand" or "Alternative solution:" comments.
   Post a follow-up comment summarizing the discussion.

When it boils down to it, remember that you're both on the same side—the goal is to make the code better.

## As a code submitter

In general:

* Try to keep the PRs small. There has been some research to indicate that beyond 400 LOC the ability to detect defects diminishes. (We're talking about LOC proper, vendor code and GUI layouts don't count.)
* If the PR is work in progress, use GitHub's draft pull request feature.
* Make a checklist on what's missing or could be improved in the PR description or as comments.

Your code:

* Explain why the code exists. ("It's like that because of these reasons. Would
  it be more clear if I rename this class/file/method/variable?")
* Extract some changes and refactorings into future issues or pull requests.

Interacting with reviewers:

* Be grateful for the reviewer's suggestions. ("Good call. I'll make that change.")
* A common axiom is "Don't take it personally. The review is of the code, not you." — this means you should be aware of how hard it is to convey emotion online and how easy it is to misinterpret feedback. If a review seems aggressive or angry or otherwise personal, consider if it is intended to be read that way and ask the person for clarification of intent, in person if possible.
* Keeping the previous point in mind: assume the best intention from the reviewer's comments.
* Seek to understand the reviewer's perspective.
* Try to respond to every comment.
* If you are waiting for a review or a response, it's not a problem to ping the #development channel.

If you have merge permissions:

* Wait to merge the branch until continuous integration tells you that the build has passed.
* Merge once you feel confident in the code and its impact on the project.
* Final editorial control rests with you.

## As a reviewer

Understand why the change is necessary (fixes a bug, improves the user
experience, refactors the existing code). Then:

* Seek to understand the author's perspective.
* Communicate which ideas you feel strongly about and those you don't.
* Identify ways to simplify the code while still solving the problem.
* Offer alternative implementations, but assume the author already considered
  them. ("What do you think about using a custom validator here?")
* Remember that you are here to provide feedback, not to be a gatekeeper.
* Ask, don’t tell. (“What do you think about trying…?” rather than “Don’t do…”)
* Offer ways to simplify or improve code.
* Communicate which ideas you feel strongly about and those you don't. Explain your reasons why code should be changed. (Not in line with the style guide? A personal preference?)
* If you disagree strongly, consider giving it a few minutes before responding; think before you react.
* Offer alternative implementations, but assume the author already considered them. ("What do you think about using a custom validator here?")
* If discussions turn too theoretical or touch big architectural questions, move the discussion offline. In the meantime, let the author make the final decision on alternative implementations.
* Don't keep the code hostage. Keep in mind the context and the most important thing - does it work?
* Sign off on the pull request with a :thumbsup: or "Ready to merge" comment.

If the pull request author has merge permissions prefer review approvals instead of merging the PR for them.

## Responding to feedback

* Try to respond to every comment. Be grateful for the reviewer's suggestions. ("Good call. I'll make that change.")
* Be aware of how hard it is to convey emotion online and how easy it is to misinterpret feedback. If a review seems aggressive or angry or otherwise personal, consider if it is intended to be read that way and ask the person for clarification of intent, in person if possible.
* Link to any follow up commits or Pull Requests. (“Good call! Done in 1682851”)

If you have merge permissions:

* Wait to merge the branch until Continuous Integration tells you the build has passed. Merge once you feel confident in the code and its impact on the project.

----

This review guide is based on [work from thoughtbot inc](https://github.com/thoughtbot/guides/tree/master/code-review) and [work from @mrsasha](https://gist.github.com/mrsasha/8d511770ad9b282f3a5d0f5c8acdd10e).