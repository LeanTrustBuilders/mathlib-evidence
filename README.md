# Evidence about Mathlib

Reviews, problem reports, questions and tests of the declarations of
[Mathlib](https://github.com/leanprover-community/mathlib4), kept in `evidence/` as
[S3 records](https://github.com/LeanTrustBuilders/specs/blob/main/S3-evidence.md): one per line, in
git, never edited. They are written from the issues of this repository.

## Adding to it

Open an issue with one of the [forms](https://github.com/LeanTrustBuilders/mathlib-evidence/issues/new/choose):
review a declaration, report a problem, ask a question, propose a test, list a test, or name a result.
A bot turns it into a record, keyed by the declaration's hashes at the commit of Mathlib you name (the
latest with a dataset if none), and replies on the issue. A record says which version of the
declaration it was about: when the declaration, or something it rests on, changes, pages show the
record as made on an earlier version.

Comments on the issue are replies. Commands in a comment change a record's state: `/withdraw`,
`/fixed <commit>`, `/intended`, `/invalid`, `/answered`, `/met <declaration>`, `/reopen`. Records are
never anonymous: each names the GitHub account it came from, and an AI agent's are labelled as such.
An agent can also submit from a terminal with
[`evidence-store submit`](https://github.com/LeanTrustBuilders/evidence-store#who-wrote-it).

A record names its declaration by what it means, so it applies wherever the declaration is used: a
store about a library built on Mathlib can import the Mathlib store (`imports` in its `store.json`,
S3's [imported records](https://github.com/LeanTrustBuilders/specs/blob/main/S3-evidence.md#imported-records)),
and its pages then show these records beside its own.

## How it is set up

- `evidence/store.json`: the store's name (Mathlib), the library (Mathlib, root `Mathlib`), and where
  its datasets are: the releases `mathlib-dataset-<commit12>` of
  [Mathlib Explorer](https://github.com/LeanTrustBuilders/mathlib-explorer), one for each Mathlib
  release tag it builds.
- `.github/workflows/evidence-intake.yml` and `evidence-check.yml`: intake, and the check of every
  change to the store, by [evidence-store](https://github.com/LeanTrustBuilders/evidence-store)
  v0.7.2.
