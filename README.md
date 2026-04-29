# `admiralty-dist` — distribution channel for the Admiralty CLI

This repository ships built wheels for the [Admiralty Fleet Command System](https://admiraltyai.com).
**It contains no source code** — the source lives in a private repository under proprietary licence.

## Install

```bash
pip install admiralty --extra-index-url https://tavisbasing.github.io/admiralty-dist/
```

That's it. After installation:

```bash
adm version
adm licence activate <YOUR-KEY>
adm quickstart
```

See **[admiraltyai.com](https://admiraltyai.com)** for the product, **[docs.admiraltyai.com](https://docs.admiraltyai.com)** for the documentation, and **`adm licence activate --help`** for the licence onboarding flow.

## How updates work

A GitHub Actions workflow on the (private) source repo builds a wheel on every `v*.*.*` tag-push and:

1. Commits the wheel to [`wheels/`](wheels/) here.
2. Updates the [PEP 503 `simple/` index](simple/) so `pip` can discover it.
3. Publishes a [GitHub Release](https://github.com/tavisbasing/admiralty-dist/releases) with the wheel attached.

## Verifying a download

Every release page lists the wheel's SHA-256 hash. Recommended pip invocation in production environments:

```bash
pip install admiralty==<VERSION> \
    --extra-index-url https://tavisbasing.github.io/admiralty-dist/ \
    --require-hashes
```

(With a `requirements.txt` that pins the hash from the release page.)

## Licence

The wheels published here are **proprietary software**. See [`LICENSE`](LICENSE). Reverse-engineering, redistribution, or sublicensing is prohibited. Reading the bytecode is technically possible (it's a Python wheel), but any commercial reuse of the source you reconstruct is a breach of the licence and a breach of confidence.

The source repository is private. Customer support requests go to `admiralty@tech127.com`.

## Issues

For bugs in the **package** (install, runtime, CLI behaviour), open issues at the public repo: https://github.com/tavisbasing/Admiralty/issues.

For bugs in the **distribution** itself (wheel won't download, GH Pages 404s, hash mismatch), open an issue here.
