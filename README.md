# cic-registry

This repository acts as the central registry for the CIC system, built on a three-layer model:

* **schemas/** – declarative system definition schemas
* **mods/** – executable relay modules (e.g., `onprem-kafka`, `aws-sqs`, ...)
* **agents/** – agent declarations that link supported `schema`–`mod` pairs
* **release-matrix.yaml** – optional central compatibility matrix (only needed in non-decentralized agent setups)

## Current Registry Snapshot

```yaml
schemas:
  messaging:
    - version: v1.0.0
      status: default
      commitid: 7f12d9a
      sign: sha256:6a3c...abc1
    - version: v1.1.0
      status: supported
      commitid: b3c21e4
      sign: sha256:8b2d...def2

agents:
  messaging:
    gcp-agent:
      - version: v0.9.0
        commitid: 95deac3
        schemas:
          messaging:
            - version: v1.0.0
            - version: v1.1.0
      - version: v1.0.0
        commitid: a1bc99d
        schemas:
          messaging:
            - version: v1.1.0

releases:
  messaging:
    v1.0.0: schemas/messaging/releases/v1.0.0.yaml
    v1.1.0: schemas/messaging/releases/v1.1.0.yaml
```

---

The `mods/` and `agents/` directories will contain further detailed content as the system evolves. `release-matrix.yaml` is only necessary if you opt out of decentralized agent registration.

---

## License

This work is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

See `LICENSE.md` for the full terms.
