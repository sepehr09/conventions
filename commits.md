## General Guidance

- All the codes that is pushed into the project repository should be easily forked/cloned and built by the community.
  It shouldn't be hard-wired to your particular development environment, and should include build scripts or quick
  instructions on how to get the code working.

- The code that is pushed into the project repo should not include debug statements. e.g. `console.log()`.

- Production-level code needs to be accompanied by a reasonable suite of unit tests. This helps others confirm that the
  code is working as intended, and allows the community to adopt more agile refactoring techniques while being more
  confident in our ability to avoid regressions.

## Do Atomic Commit

Commits should be atomic as far as possible. An `atomic` change revolves around one task or one fix. It means that never
commit an issue including `a bug fix` and `change in the color of layout`. Even if these two are included in a single
task, break it down to two or more tasks.

## Repository names

All repository names should follow the `kebab-case` naming convention and be in lower case.

## Subject

#### Separate subject from body with a blank line.

Not every commit requires both a subject and a body. Sometimes a single line is fine, especially when the change is so
simple, that no further context is necessary.

For example:

```
Fix typo in introduction to user guide
```

When a commit merits a bit of explanation and context, you need to write a body.
For example:

```
Derezz the master control program

MCP turned out to be evil and had become intent on world domination.
This commit throws Tron's disc into MCP (causing its deresolution)
and turns it back into a chess game.
```

With blank line after first line let commands like `git log --oneline` or `git shortlog` can show the first line correctly.

#### Subject length

50 characters is not a hard limit, just a rule of thumb. Keeping subject lines at this length ensures that they are
readable, and forces the author to think for a moment about the most concise way to explain what’s going on.

_So aims for `50` characters, but consider `72` the hard limit._

#### Capitalize the subject line

This is as simple as it sounds. Begin all subject lines with a capital letter.
Example:

```
Accelerate to 88 miles per hour
```

Instead of:

```
accelerate to 88 miles per hour
```

#### No ending dot is required

Trailing punctuation is unnecessary in subject lines. Besides, space is precious when you’re trying to keep them to `50`
characters, or less.

Example:

```
Open the pod bay doors
```

Instead of:

```
Open the pod bay doors.
```

#### Be Imperative

The imperative can sound a little rude; that’s why we don’t often use it. Although it’s perfect for Git commit subject
lines. One reason for this is that Git itself uses the imperative whenever it creates a commit on your behalf.

So when you write your commit messages in the imperative, you’re following Git’s own built-in conventions. For example:

```
Refactor subsystem X for readability

Update getting started documentation

Remove deprecated methods

Release version 1.0.0
```

A properly formed Git commit subject line should always be able to complete the following sentence:

```
    If applied, this commit will your subject line here
```

For example:

```
If applied, this commit will refactor subsystem X for readability

If applied, this commit will update getting started documentation

If applied, this commit will remove deprecated methods

If applied, this commit will release version 1.0.0

If applied, this commit will merge pull request #123 from user/branch
```

Notice how this doesn’t work for the other non-imperative forms:

```
If applied, this commit will fixed bug with Y

If applied, this commit will changing behavior of X

If applied, this commit will more fixes for broken stuff

If applied, this commit will sweet new API methods
```

**Remember**: Use of the imperative is important only in the subject line. You can relax this when you’re writing the body.

## Body

#### Body length

The recommendation is to do this at `72` characters.

#### Use the body to explain `what` and `why` vs. `how`

This commit from Bitcoin Core is a great example of explaining what changed and why:

```
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

Simplify serialize.h's exception handling

Remove the 'state' and 'exceptmask' from serialize.h's stream
implementations, as well as related methods.

As exceptmask always included 'failbit', and setstate was always
called with bits = failbit, all it did was immediately raise an
exception. Get rid of those variables, and replace the setstate
with direct exception throwing (which also removes some dead
code).

As a result, good() is never reached after a failure (there are
only 2 calls, one of which is in tests), and can just be replaced
by !eof().

fail(), clear(n) and exceptions() are just never called. Delete
them.
```

## Commit Structure

The structure of commit message should be as follows:

```
[type][jira-issue-id] subject
<BLANK LINE>
body
<BLANK LINE>
[reviewer: reviewer]
[BREAKING CHANGES]
```

- **`type`**

  - **`build`:** Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
  - **`task`:** A task that needs to be done.
  - **`feature`:** A new feature of the product, which has yet to be developed.
  - **`fix`:** A problem which impairs or prevents the functions of the product.
  - **`docs`:** Documentation only changes
  - **`style`:** Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
  - **`refactor`:** A code change that neither fixes a bug or adds a feature
  - **`performance`:** A code change that improves performance
  - **`test`:** Adding missing tests
  - **`chore`:** Changes to the build process or auxiliary tools and libraries such as documentation generation
  - **`ci`:** Changes to our CI configuration files and scripts (example scopes: Circle, BrowserStack, SauceLabs)

- **`jira-issue-id`**
  - The id of jira issue.
  - Note that even trivial or entirely cosmetic (code reformatting, fixing typos in comments, etc) changes should have
    JIRA reference.
- **`subject`**
  - The subject of commit.
- **`body`**
  - The body of commit
- **`reviewer`**
  - the name of a colleague that review this code before commit.
- **`Breaking Changes`**
  - Any information about Breaking Changes will be placed here. This is optional and can be a multi-line description.

## Branch Name Structure

The structure of the branch name should be as follows:

```
jira-id/source_branch-name_of_branch
```

For example:

```
FP-1234/develop-remove_cart_purchase_from_basket_summary
```

## Sources:

- [Distributed Git - Contributing to a Project](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Git style guide](https://datasciencecampus.github.io/coding-standards/version-control.html#git-style-guide)
- [Coding and Commit Standards](https://wiki.fluidproject.org/display/fluid/Coding+and+Commit+Standards)
- [Contributing to Angular](https://github.com/angular/angular/blob/master/CONTRIBUTING.md)
