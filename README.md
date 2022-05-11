# module-manifests

## Overview

Module [Repo](https://gerrit.googlesource.com/git-repo/) Manifests

This controls how different Nexient Platform tooling dependencies are handled.

## Manifests

Manifests in the root directory are either global (eg [`remote.xml`](./remote.xml)) or consumed directly (eg [`tf_modules.xml`](./tf_modules.xml)). If something is in a subdirectory (eg [`components/platform-components.xml`](./components/platform-components.xml)) it is not intended to be consumed directly and is used by one of the root files.

## Notes

### Release Pipeline

This repo does not contain a release pipeline, for a few reasons.
- `module-manifests` is a "metadata" repository. It essentially is a container repo that holds manifest xmls. Given the nature of the manifest xml files themselves, versioning the repository results in no beneficial gain as oppose to say an API repo where breaking changes to occur.
- The repo is intended to be "monolithic" where release/versioning would be needed.
- Versioning can be tracked better within the Manifest files themselves (pinned `git` revisions for the repositories being referenced). Good practice to create a pinned manifest that refers to a working version of a project.
    ```
    <manifest>
        <remote name="nanopb" fetch="https://github.com/nanopb"/>
        ...
        <project name="musllibc.git" path="projects/musllibc" revision="aa82031dd861f7ade4c3738b417de34120b01f15" upstream="sel4" dest-branch="sel4"/>
    </manifest>
    ```
