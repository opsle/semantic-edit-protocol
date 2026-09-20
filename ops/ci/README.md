# ops/ci — canonical lifecycle for opsle/semantic-edit-protocol

```
AI → PR → TEST → MERGE → TEST merged SHA → DEPLOY → VERIFY
```

| Command | Runs on | Holds |
| --- | --- | --- |
| `ops/ci/test` | `platform-ci,semantic-edit-protocol` runner (`ci.yml`, job `quality`) | no production credentials |
| `ops/ci/deploy SHA` | `semantic-edit-protocol-deploy` runner (`deploy.yml`) | write access (POSIX ACL) to `/opt/opsle-components/semantic-edit-protocol` |
| `ops/ci/verify SHA` | deploy runner, or anywhere | nothing; read-only |

- **Merge enforcement:** `opsle` is on a free GitHub plan (no rulesets, branch protection or auto-merge). Merge only with `gh pr merge --squash --delete-branch` after `quality` passes.
- **Exact SHA:** `deploy.yml` is a `workflow_run` of the `push`-to-`main` CI run and checks out and deploys `workflow_run.head_sha`. `ops/ci/deploy` refuses anything that is not the tip of main (exit 75 = superseded) or a checkout that is not exactly that SHA.
- **Atomic switch:** releases are deployed under `/opt/opsle-components/semantic-edit-protocol/releases/<sha>` and atomically pointed to by `current`.
- **Single release owner:** `deploy.yml` does nothing unless repository variable `SEMANTIC_EDIT_PROTOCOL_DEPLOY_ENABLED` is `true`.

## Operator gates (root; not doable by agents)

Run `bash ops/ci/operator-gate test deploy` in a terminal. It mints the registration tokens and installs the self-hosted runners.
