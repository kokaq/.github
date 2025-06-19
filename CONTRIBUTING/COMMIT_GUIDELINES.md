
<!-- TOC --><a name="commit-guidelines"></a>
# Commit Guidelines

> ## Why Proper commits are important?
> - Automatically generating CHANGELOGs.
> - Automatically determining a semantic version bump (based on the types of commits landed).
> - Communicating the nature of changes to teammates, the public, and other stakeholders.
> - Triggering build and publish processes.
> - Making it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

The commit message should be structured as follows:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```


   * [Rules of writing a good commit message](#rules)
   * [Examples](#examples)
      + [Commit message with description and breaking change footer](#commit-message-with-description-and-breaking-change-footer)
      + [Commit message with `!` to draw attention to breaking change](#commit-message-with-to-draw-attention-to-breaking-change)
      + [Commit message with scope and `!` to draw attention to breaking change](#commit-message-with-scope-and-to-draw-attention-to-breaking-change)
      + [Commit message with both `!` and BREAKING CHANGE footer](#commit-message-with-both-and-breaking-change-footer)
      + [Commit message with no body](#commit-message-with-no-body)
      + [Commit message with scope](#commit-message-with-scope)
      + [Commit message with multi-paragraph body and multiple footers](#commit-message-with-multi-paragraph-body-and-multiple-footers)
   * [💬 Conventional Commits FAQ](#-conventional-commits-faq)
      + [🔠 Are commit types in the title uppercase or lowercase?](#-are-commit-types-in-the-title-uppercase-or-lowercase)
      + [🧩 What if a commit fits multiple types?](#-what-if-a-commit-fits-multiple-types)
      + [🚀 Does this slow down rapid development or iteration?](#-does-this-slow-down-rapid-development-or-iteration)
      + [🔁 How does this relate to Semantic Versioning (SemVer)?](#-how-does-this-relate-to-semantic-versioning-semver)

<!-- TOC end -->

<!-- TOC --><a name="rules"></a>
## Rules of writing a good commit message
1. Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc., followed
  by the OPTIONAL scope, OPTIONAL `!`, and REQUIRED terminal colon and space.
1. The type `feat` MUST be used when a commit adds a new feature to your application or library.
1. The type `fix` MUST be used when a commit represents a bug fix for your application.
1. A scope MAY be provided after a type. A scope MUST consist of a noun describing a
  section of the codebase surrounded by parenthesis, e.g., `fix(parser):`
1. A description MUST immediately follow the colon and space after the type/scope prefix.
The description is a short summary of the code changes, e.g., _fix: array parsing issue when multiple spaces were contained in string_.
1. A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
1. A commit body is free-form and MAY consist of any number of newline separated paragraphs.
1. One or more footers MAY be provided one blank line after the body. Each footer MUST consist of
 a word token, followed by either a `:<space>` or `<space>#` separator, followed by a string value (this is inspired by the
  [git trailer convention](https://git-scm.com/docs/git-interpret-trailers)).
1. A footer's token MUST use `-` in place of whitespace characters, e.g., `Acked-by` (this helps differentiate
  the footer section from a multi-paragraph body). An exception is made for `BREAKING CHANGE`, which MAY also be used as a token.
1. A footer's value MAY contain spaces and newlines, and parsing MUST terminate when the next valid footer
  token/separator pair is observed.
1. Breaking changes MUST be indicated in the type/scope prefix of a commit, or as an entry in the
  footer.
1. If included as a footer, a breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon, space, and description, e.g.,
_BREAKING CHANGE: environment variables now take precedence over config files_.
1. If included in the type/scope prefix, breaking changes MUST be indicated by a
  `!` immediately before the `:`. If `!` is used, `BREAKING CHANGE:` MAY be omitted from the footer section,
  and the commit description SHALL be used to describe the breaking change.
1. Types other than `feat` and `fix` MAY be used in your commit messages, e.g., _docs: update ref docs._
1. The units of information that make up Conventional Commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
1. BREAKING-CHANGE MUST be synonymous with BREAKING CHANGE, when used as a token in a footer.

<!-- TOC --><a name="examples"></a>
## Examples

<!-- TOC --><a name="commit-message-with-description-and-breaking-change-footer"></a>
### Commit message with description and breaking change footer
```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

<!-- TOC --><a name="commit-message-with-to-draw-attention-to-breaking-change"></a>
### Commit message with `!` to draw attention to breaking change
```
feat!: send an email to the customer when a product is shipped
```

<!-- TOC --><a name="commit-message-with-scope-and-to-draw-attention-to-breaking-change"></a>
### Commit message with scope and `!` to draw attention to breaking change
```
feat!: send an email to the customer when a product is shipped
```

<!-- TOC --><a name="commit-message-with-both-and-breaking-change-footer"></a>
### Commit message with both `!` and BREAKING CHANGE footer
```
refactor!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

<!-- TOC --><a name="commit-message-with-no-body"></a>
### Commit message with no body
```
docs: correct spelling of CHANGELOG
```

<!-- TOC --><a name="commit-message-with-scope"></a>
### Commit message with scope
```
feat(lang): add Polish language
```

<!-- TOC --><a name="commit-message-with-multi-paragraph-body-and-multiple-footers"></a>
### Commit message with multi-paragraph body and multiple footers
```
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```

<!-- TOC --><a name="-conventional-commits-faq"></a>
## 💬 Conventional Commits FAQ

<!-- TOC --><a name="-are-commit-types-in-the-title-uppercase-or-lowercase"></a>
### 🔠 Are commit types in the title uppercase or lowercase?

While any casing is technically valid, it’s best to **stick with lowercase** for consistency across the project.

---

<!-- TOC --><a name="-what-if-a-commit-fits-multiple-types"></a>
### 🧩 What if a commit fits multiple types?

If your changes cover more than one type (e.g., both a `feat` and a `fix`), consider **splitting them into multiple commits**.  
One of the main benefits of Conventional Commits is encouraging more organized and focused commits and PRs.

---

<!-- TOC --><a name="-does-this-slow-down-rapid-development-or-iteration"></a>
### 🚀 Does this slow down rapid development or iteration?

Not exactly. It discourages **moving fast in a disorganized way**.  
By enforcing structure, it actually enables your team to move faster and more confidently over time—especially across large projects and distributed teams.

---

<!-- TOC --><a name="-how-does-this-relate-to-semantic-versioning-semver"></a>
### 🔁 How does this relate to Semantic Versioning (SemVer)?

Conventional Commits directly map to SemVer release types:

| Commit Type             | SemVer Release |
|-------------------------|----------------|
| `refactor!:`            | PATCH          |
| `fix:`                  | PATCH          |
| `feat:`                 | MINOR          |
| `BREAKING CHANGE:` note | MAJOR          |

> Any commit with a `BREAKING CHANGE:` footer (regardless of type) signals a **major** version bump.


> ### Next
> [Create a pull request](./PULL_REQUEST.md)