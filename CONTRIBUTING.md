### Contents:
- [What is mtasa-docs?](#what-is-mtasa-docs)
- [Contributing to mtasa-docs](#contributing-to-mtasa-docs)
  - [Where to contribute](#where-to-contribute)
    - [Project structure](#project-structure)
  - [What to contribute](#what-to-contribute)
    - [Existing guidelines/documentation/practices](#existing-guidelinesdocumentationpractices)
    - [Discussions](#discussions)
  - [Who can contribute](#who-can-contribute)

# What is mtasa-docs?

The main goal of this repository is to provide a place for collaboration on documentation relating 
to multitheftauto projects (such as mtasa-blue, mtasa-resources, etc).

As a member of this community, you provide the time and effort (through your contributions) which helps 
keep our projects alive, and therefore should have a right to involvement in discussions around 
contribution guidelines and practices.

# Contributing to mtasa-docs

A lot of the ideas in our [Code review](CODE_REVIEW.md) document are 
applicable here.

## Where to contribute

From the root of this repository, each multitheftauto project lives within its own folder. 
For example `mtasa-blue` or `mtasa-resources`.

### Project structure
General contribution information should be kept in `CONTRIBUTING.md`; where/what/how contributions should be made, 
as well as information on best practices.

Coding guidelines (exploring real code snippets and scenarios) should be kept in `CODING_GUIDELINES.md`

If a document requires a large snippet of code, it's best to store the code snippet separately under `examples/<example_name>`

For example (pun not intended), if writing the section on "Securing element data" for the [Script security](#) guide, the script example would be under `mtasa-resources/examples/securing_element_data.lua` and you'd link to that file in the guide.

## What to contribute

### Existing guidelines/documentation/practices
If you're sure that something isn't quite right with any of our documentation, or is out of date by modern standards
feel free to make a pull request addressing these changes. It's always worth having a quick search beforehand, through
existing and previous issues/discussions, to ensure it hasn't already been discussed and decided on (at least, recently).

### Discussions
Discussions may be created for topics which require some extra thought: 
https://github.com/multitheftauto/mtasa-docs/discussions

Please only contribute to discussions if what you are submitting adds value to the conversation.

- Have a solid point: "I just prefer it" isn't always going to win the argument.
- Don't repeat previous points
- Keep it friendly and encouraging for others to join in the discussion, see [Code review](CODE_REVIEW.md)

## Who can contribute

Anyone can contribute to the improvement of our documentation. We ask that you read this entire document well before 
doing so, as well as our [Code review](CODE_REVIEW.md) document. Please note, any kind of uncivilized behaviour may lead to restriction from the mtasa-docs repository.

- **Contributors** (regular users) are able to start discussions, open pull requests and issues.
- **Members** (those with write access) are able to submit reviews for pull requests & merge them.
- **Admins** (overlords) are able to manage everything, and have final say on any proposals that are 'stuck' due to lack of agreement

Pull requests must be reviewed by at least one repository member before they can be merged.

There _will be_ certain topics or discussions which are opinionated/preference-based, and we would like to avoid 
such topics going stale due to lack of agreement.

In this case, an admin of the repository is able to make a final decision on any proposals.
