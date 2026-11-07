# CommGate releases

Public download mirror for CommGate gateway release artifacts. **This repository holds no source code.**

- **Downloads page:** https://automation.commvergent.com/downloads/commgate
- **Release manifest (the contract):** https://automation.commvergent.com/downloads/commgate/channels/stable.json

Binary artifacts are attached to this repository's GitHub Releases (tag `v<version>`). Download URLs inside the manifest point here, but those URLs are just data. Clients (including the gateway's update checker) must read the first-party manifest above, never this repository's release list.

## Layout

```
channels/<channel>.json          channel manifest (served first-party by automation.commvergent.com)
channels/<channel>.json.minisig  detached minisign signature of the manifest (when signing is enabled)
releases/<version>/RELEASE_NOTES.md
releases/<version>/legal/        open-source notices and the GPL written source offer for that version
```

Everything in this repository is written by the publish pipeline (`scripts/commgate/publish_release.py` in the automation-web-next repo). Do not edit the manifests by hand. Use the pipeline's `publish`, `yank` and `unyank` commands.

## Retention rule: legal files are never deleted

Files under `releases/<version>/legal/` are **never deleted or rewritten**, even when that version's binaries are yanked or its GitHub Release assets are removed. A GPL written offer must stay valid for at least three years after the last distribution of that version. Keeping these files in git history is how that obligation is met. The publish pipeline refuses to overwrite an existing legal file with different contents.

Published release assets are likewise immutable. Republishing a version with a file whose contents differ from what is already uploaded is refused. To ship a fix, publish a new version.
