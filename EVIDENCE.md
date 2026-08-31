# Evidence Ledger

This ledger separates recovered facts from historical claims, inference, and open questions. The current commission is excavation only.

## Supported by public repository source

### 1. It was a Chromium extension

The current manifest declares:

- Manifest V3;
- name `Chromium Throne`;
- version `0.7.0`;
- permissions for tabs, scripting, side panel, storage, alarms, and active tab;
- a module service worker;
- a side-panel HTML entry point;
- host access to `https://chatgpt.com/*`;
- host access to `http://127.0.0.1:9234/*`.

Source: [extension manifest](https://github.com/Valar05/home-center/blob/main/browser-porch/extension/manifest.json).

### 2. It was also a local relay/control plane

Recovered source and historical installer evidence identify:

- `browser-porch/throne-relay-runner.mjs`;
- `browser-porch/throne-client.mjs`;
- loopback base URL `http://127.0.0.1:9234/v1/throne`;
- a relay capability stored locally on the desktop;
- events and log files;
- a dedicated Chromium profile.

This means the extension was not self-contained. The browser component depended on a local process and local state.

### 3. It controlled visible ChatGPT sessions

The project README says the worker was a visible ChatGPT Pro reasoning conversation, not API-token compute, cookie scraping, account rotation, or a hidden headless farm.

Source: [Browser Porch / Chromium Throne README](https://github.com/Valar05/home-center/blob/main/browser-porch/README.md).

### 4. The orchestration model changed

Recovered chronology contains at least two designs:

- an earlier service-worker-owned visible worker swarm;
- a later `0.7.0` “single-Pro evolution” contract with `MAX_PARALLEL_WORKERS = 1`, one persistent worker tab, and explicit recovery-only worker rotation.

The record therefore describes an evolving prototype, not one clean settled architecture.

### 5. Persistence was part of the system

Historical installer evidence names scheduled tasks:

- `HomeCenterChromiumThroneRelay`;
- `HomeCenterChromiumThrone`;
- `HomeCenterChromiumThroneWatchdog`;
- `HomeCenterFortressDaemon`.

The intended behavior was to relaunch relay/browser processes when unavailable. This persistence layer is part of the excavation because it materially changes what “a browser plugin” means.

### 6. Phone orchestration was a later adapter

[PR #268](https://github.com/Valar05/home-center/pull/268) describes a phone-local adapter translating campaign tasks through SSH Axis to THECAULDRON, then through the existing `throne-client.mjs` and loopback relay into the extension.

That adapter explicitly claimed it was not a second browser implementation. It belongs in the dependency history, but it does not define the core Chromium Throne body.

## Capability-state evidence

The source README itself states that source was implemented but authoritative deployment and acceptance were not proven. It explicitly lists missing evidence including:

- authoritative CI execution;
- extension installed/reloaded on THECAULDRON;
- visible ChatGPT account verified as using Pro reasoning;
- primary-phone end-to-end routing;
- two real interface-evolution generations;
- runtime acceptance.

Historical GitHub notifications from August 13–14, 2026 show repeated rapid failures of workflows named `Chromium Throne Contract`, `Home Center CI`, `Portal Reflex`, and `Build Android`. Those notifications support “validation failed,” not a diagnosis of why each job failed.

## What the evidence does not prove

- that the extension was ever installed in its final form;
- that the relay and extension completed a real command end to end;
- that one persistent Pro tab behaved reliably;
- that parallel-worker revisions worked;
- that watchdogs recovered a dead runtime safely;
- that the phone adapter reached the desktop lane;
- that a human accepted the system;
- that the current `main` source equals any previously installed bytes.

## Archaeology interpretation

**Finding:** Chromium Throne was an architectural bundle, not a singular artifact.

**Best concise classification:** a local Chromium extension-based orchestration control plane for visible authenticated ChatGPT sessions, embedded in Home Center and surrounded by relay, persistence, governance, and later phone-routing machinery.

**Why classification felt impossible:** each layer was routinely named as though it were the whole:

| Name used | What it actually referred to |
|---|---|
| browser plugin | the Chromium extension |
| side panel | the operator UI |
| orchestration | worker/tab lifecycle and campaign rules |
| relay | the local Node transport |
| Chromium Throne | sometimes the extension; sometimes the entire composite lane |
| Browser Porch | source directory and earlier system name |
| phone swarm | a later client/adapter consuming the desktop lane |

## Excavation questions left open

1. Which commit, if any, was installed on THECAULDRON?
2. Did the `0.6.x` parallel-worker design ever execute successfully?
3. Did the `0.7.0` single-worker design replace it in an installed profile or only in source?
4. Which scheduled tasks actually existed, and were they removed?
5. Are any relay capability, profile, log, or event files still present on the desktop?
6. Did any real ChatGPT conversation receive and complete a Throne commission?
7. Which failures were architectural, and which were immediate CI/bootstrap failures?

Answering those questions would require a separate, explicitly authorized read-only device excavation. This repository does not authorize that action.

## Current ruling

Documentation delivered for public excavation. Reuse remains forbidden by Drew's current commission. No source, secrets, installers, or runnable reconstruction have been copied into this repository.
