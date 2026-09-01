# Browser Automation Excavation

## 1. What Chromium Throne was

Chromium Throne was a **desktop browser orchestration stack** centered on ChatGPT. Its recovered parts were:

- a Manifest V3 Chromium extension;
- a side-panel “throne” interface;
- a service worker that managed queue state, tab identity, prompt injection, checkpoint capture, continuation, and receipts;
- a localhost relay bound to `127.0.0.1` in the recovered configuration;
- a client that submitted commands and could wake the extension;
- a dedicated Chrome for Testing runtime and persistent profile;
- installer, capability, log, scheduled-task, and runtime scaffolding.

It was therefore more than a plugin and less than a complete general-purpose browser automation platform. It was a specialized orchestrator spanning an extension, a local service, a browser session, and Home Center-facing control.

## 2. Recovered v0.7.0 contract

| Property | Recovered behavior |
|---|---|
| Browser | Chrome for Testing, pinned by installer metadata |
| Profile | Dedicated persistent profile |
| Human gate | One-time ChatGPT sign-in in that profile |
| Worker model | One visible persistent authenticated Pro worker |
| Parallelism | Recovered installer set maximum parallel workers to 1 |
| Context | Bounded context with checkpoint/handoff fields |
| UI | Side panel with queue, run, capture, stop, and resume controls |
| Storage | `chrome.storage` for queue, state, context, and receipts |
| Relay | Localhost relay with extension-origin and capability controls |
| Acceptance | Runtime canary required; installer completion was not acceptance |

The recovered `swarm-core.mjs` still contained slice and handoff concepts, including bounded context and Venice directives. The practical installer contract constrained the current design to a single worker. Earlier parallel-swarm language belongs to lineage, not the final observed runtime contract.

## 3. Extension internals

### Manifest

The manifest identified a Manifest V3 extension, version 0.7.0, with permissions for active tabs, tabs, scripting, side panel, storage, and alarms. Host permissions included ChatGPT and the local relay origin.

### Side panel

The panel exposed human-visible queue and control state. It was not itself the worker; it sent messages to the service worker and displayed persisted state.

### Service worker

The service worker was the central browser state machine. Recovered behavior included:

- opening or reusing one persistent ChatGPT tab;
- injecting prompts through the page composer;
- observing assistant output and capturing checkpoints;
- polling the relay on a repeating alarm;
- maintaining queue and work states in extension storage;
- stop/resume and continuation handling;
- Venice-related continuation gates;
- local receipt material.

The implementation made an important semantic distinction: the relay could acknowledge enqueueing while the work remained unaccepted. That distinction is foundational to this graveyard.

### Relay and client

The relay runner exposed a local bridge, capability metadata, and event logging. The client read capability/runtime configuration, posted a command, and could wake the browser through an extension page. Neither file alone proved that the extension, authenticated tab, relay, and downstream completion were simultaneously healthy.

## 4. Installer and runtime footprint

The Windows installer was designed to place a pinned Browser Porch/extension payload and relay into a Chromium Throne directory under the user-local application-data tree, provision a dedicated profile, download a pinned Chrome for Testing build, create launch/runtime material, and emit a receipt. Historical bootstrap material also referenced capability files, logs, scheduled tasks, and Termux/startup coordination in the broader Fortress bundle.

No executable installer or payload is copied here. The source link remains in the inventory.

## 5. Browser Nerve is separate

Browser Nerve was a ticketed Chrome DevTools Protocol executor. Recovered source referred to a worker such as `windows-browser-nerve-01`, browser tickets, heartbeat state, and complete/failed transitions. Browser Nerve was closer to general remote browser control through CDP; Chromium Throne was a ChatGPT-specific extension/relay workflow.

Both could operate “a browser,” but through different mechanisms and contracts:

| Question | Chromium Throne | Browser Nerve |
|---|---|---|
| Primary mechanism | MV3 extension + page scripting + local relay | CDP ticket worker |
| Primary target | Dedicated authenticated ChatGPT tab | Chrome browser tasks |
| Work representation | Extension queue/checkpoints | Home Center browser tickets |
| Human surface | Side panel | Control-plane ticket/status surfaces |
| Key gate | Dedicated-profile authentication | Worker/CDP reachability and ticket lifecycle |

## 6. Computer Hands is broader

Computer Hands represented the general Windows execution body associated in recovery material with `windows-hands-01` and THECAULDRON. Chromium Throne could be installed or launched through that body, but Computer Hands also covered operations outside the browser. Calling Computer Hands “the Chromium extension” erases the authority and execution boundaries.

## 7. Phone browser automation is another lane

The Android source contained `android_chromium_control.py`, which used the phone execution path to find Chrome-family packages, open or navigate URLs, reload, go back, force-stop, run a canary, and record observed state such as focused task, UI state, and screen hashes. This was **Android Chromium control**, not the desktop Chromium Throne extension transplanted to a phone.

That distinction resolves the apparent contradiction in the original vision: the sovereign phone was intended to have browser control, but the surviving source implemented it through Android automation rather than a proven mobile installation of the desktop throne extension.

## 8. Failure and acceptance model

| Failure | What it means | What it does not mean |
|---|---|---|
| Relay unreachable | Local transport unavailable | Extension source absent |
| Extension alarm/poll failure | Browser worker not receiving work | Home Center queue never accepted work |
| ChatGPT profile signed out | Authenticated worker blocked | Installer failed |
| DOM composer changed | Injection/capture path may be broken | CDP Browser Nerve is broken |
| Queue says accepted | Command entered a queue | Requested outcome completed |
| Checkpoint exists | Some assistant output was captured | Final output was reviewed or accepted |
| Installer receipt exists | Files/configuration were provisioned | Runtime canary passed |

## 9. Recovered historical status

- Source existed and was integrated through a historical pull request lineage.
- Browser Porch documentation characterized the stack as implemented in source but not necessarily deployed or accepted.
- A pinned Chrome for Testing build and dedicated profile were part of installer intent.
- Recovery notes described Browser Nerve CDP repair while still identifying dedicated-profile authentication as a Chromium Throne gate.
- Historical CI included Chromium Throne/Home Center failures around the recovered period.
- No fresh end-to-end browser canary was run during this documentation excavation.

## 10. Disposition

Chromium Throne should be remembered as a specialized, stateful desktop ChatGPT browser worker with a local relay and dedicated profile. Browser Nerve and Computer Hands were adjacent desktop control systems. Android Chromium control was the phone-browser lane. The graveyard preserves those identities and their interfaces without distributing the machinery.
