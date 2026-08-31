---
name: gitflow
description: Design, adopt, or operate an explicitly selected Gitflow branching model for release-oriented projects. Do not use as the default branching strategy.
---

# Gitflow

Use Gitflow only when the user, repository policy, or an adopted project decision selects it. During project conception or refinement, help compare it with other branching strategies; do not presume it is appropriate.

## Decision criteria

- Gitflow fits projects with planned release cycles, a need to stabilize releases independently from ongoing feature work, or a dedicated production hotfix path.
- Call out that Gitflow has long-lived branches and more merge coordination. It can be a poor fit for trunk-based, continuous-delivery workflows.
- Record the selected branching model in the project specification or a decision record, including branch names, protections, merge policy, release/versioning convention, and any permitted deviations.

## Branch model

- `main` contains official production releases and is tagged with release versions.
- `develop` is the integration branch for the next release.
- Create `feature/<name>` branches from `develop`; merge completed work back into `develop`, never directly into `main`.
- Create `release/<version>` from `develop` to stabilize a release. Limit it to release preparation, fixes, security updates, and documentation. When ready, merge it to both `main` and `develop`, then tag the `main` release.
- Create `hotfix/<name-or-version>` from `main` for urgent production fixes. Merge the completed hotfix to both `main` and `develop`, then tag the production release.

## Guardrails

- Inspect the repository's existing branches, protections, release process, and local instructions before proposing or creating branches.
- Create pull requests only against an existing `main`/`master`, `staging`, or `develop`/`development` branch; never target a feature, release, or hotfix branch.
- Do not rename default branches, create remote branches, merge, tag, push, change protections, or alter CI without explicit authorization.
- Do not use the `git-flow` extension as a prerequisite; standard Git commands are sufficient. If the extension is requested, verify it is installed before relying on it.
- Preserve local naming, review, and release conventions when they differ from these defaults.

## Reference

Use Atlassian's [Gitflow workflow guide](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow) for the branching model and release/hotfix lifecycle.
