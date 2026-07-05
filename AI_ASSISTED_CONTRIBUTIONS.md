# AI-assisted contributions

Generative AI tools such as ChatGPT, Claude, Claude Code, GitHub Copilot,
Codex, Gemini, Cursor, and similar tools may be used when contributing to
Multi Theft Auto projects.

AI assistance does not reduce the contributor's responsibility for a
contribution. The person submitting the contribution remains its author and
is responsible for its correctness, quality, security, licensing, and impact
on the project.

## Contributor responsibilities

Before submitting AI-assisted work, contributors must:

- review and understand every submitted change
- verify that the change is appropriate for the project
- test the change to the same standard as any other contribution
- be able to explain and defend the design and implementation
- verify claims made in commit messages, pull request descriptions, and review
  responses
- ensure that the contribution can legally be submitted under the project's
  license
- ensure that secrets, credentials, private data, unpublished security
  information, or other sensitive material were not shared with an external AI
  service

Do not submit generated code, tests, documentation, or explanations that you
have not personally reviewed and understood. AI-generated statements claiming
that a build or test passed are not acceptable unless the contributor actually
performed that verification.

Fully autonomous or bot-submitted pull requests are not accepted unless the
project maintainers have explicitly approved the automation in advance.

## When disclosure is required

Disclosure is required when a generative AI tool materially contributed to the
submitted work. This includes AI that generated or substantially modified:

- source code or scripts
- tests or test data
- documentation
- configuration or build files
- architecture or implementation incorporated into the contribution
- commit messages or pull request descriptions containing substantive technical
  explanations

Disclosure is not normally required for trivial spelling corrections,
formatting suggestions, search queries, or small editor completions that did
not materially influence the contribution.

When uncertain, disclose the assistance.

## Commit disclosure

Add an `Assisted-by:` trailer to every affected commit. Identify the tool, and
include the model when it is known:

```text
Fix checkpoint validation for duplicate elements

Reject duplicate checkpoint elements before adding them to the lookup table.

Assisted-by: Claude Code (Claude Sonnet)
```

Other valid examples include:

```text
Assisted-by: ChatGPT
Assisted-by: GitHub Copilot
Assisted-by: Codex (GPT-5)
```

Add a separate trailer for each tool that materially contributed:

```text
Assisted-by: Claude Code
Assisted-by: ChatGPT
```

An automatically generated `Co-authored-by:` trailer that clearly identifies
an AI tool is also accepted as disclosure. `Assisted-by:` is preferred because
the human contributor remains the author and responsible party.

Do not identify an AI tool using `Signed-off-by:`, `Reviewed-by:`, or
`Tested-by:`. Those trailers represent certifications or actions performed by
people.

## Pull request disclosure

The pull request description must also briefly state:

- which AI tools were used
- which parts of the contribution were AI-assisted
- what review and testing the contributor performed

For example:

```text
AI assistance: Claude Code produced the initial implementation and unit-test
scaffolding. I reviewed and modified the generated code and ran the relevant
test suite.
```

A short disclosure is sufficient. Do not paste prompts, complete AI transcripts,
or generated walls of text unless they are directly relevant to the review.

## Review and enforcement

AI-assisted contributions are held to the same coding, testing, licensing,
security, and review standards as all other contributions. The use of AI is not
an exception to any project rule.

Reviewers may ask contributors to explain design decisions, unusual code, or
the verification they performed. A contribution may be rejected when the
contributor cannot adequately explain or support the submitted work.

Maintainers should review the contribution itself and should not rely on
automated AI-content detectors to determine whether disclosure was required.

Missing disclosure should normally be corrected by updating the pull request
and affected commits. Repeated submission of undisclosed, unreviewed, or
low-quality AI-generated work may result in the contribution being closed or
repository privileges being restricted.
