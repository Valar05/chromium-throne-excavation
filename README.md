# Chromium Throne / Browser / Phone / Vlad Graveyard

**Classification:** public archaeological documentation  
**System family:** Fortress Online / Home Center  
**Disposition:** retired, incomplete, or unaccepted mechanisms preserved for excavation  
**Reuse status:** **NO REUSE**

This is a documentation graveyard, not a distributable application and not a source-code transplant. It identifies what the browser and phone automation pieces were, how they related, what source artifacts existed, and what remained unproved. It deliberately excludes executable copies, credentials, bearer tokens, private endpoints, device identifiers, and instructions that would revive the system.

## The short answer

Chromium Throne was not one clean product. The name covered a desktop ChatGPT browser-control stack built from a Chromium extension, a localhost relay, a client, a dedicated Chromium profile, queue/state logic, and installer/runtime scaffolding. It lived beside—but was not identical to—Browser Nerve, Computer Hands, Android Chromium control, Phone Hands, the Android operator overlay, Atom, Venice, and Vlad.

Vlad belongs to the phone/control plane. Vlad was a long-running synchronization and Judgment Jar access daemon used by Atom and campaign/review paths. Vlad did not drive Chromium tabs or Android taps directly. Treating Vlad as “part of it” is correct at the Fortress-system level; treating Vlad as the Chromium Throne extension is not.

## Repository map

| Path | Purpose |
|---|---|
| `README.md` | Scope, classification, and first orientation |
| `docs/SYSTEM_ARCHITECTURE.md` | Whole-system boundaries, topology, states, and claims |
| `docs/BROWSER_AUTOMATION.md` | Chromium Throne, Browser Porch, Browser Nerve, Computer Hands, Android Chromium |
| `docs/PHONE_AUTOMATION.md` | Phone Hands, Termux, relay, overlay, Shizuku/rish, SSH, campaign machinery |
| `docs/VLAD.md` | Vlad daemon, Atom/Judgment Jar linkage, receipts, gates, and limits |
| `evidence/SOURCE_INVENTORY.md` | Source-path inventory, observed hashes, provenance, and acceptance gaps |
| `state.md` | Excavation state and stop condition |

## Status vocabulary

The excavation never treats one stage as proof of the next:

1. **Present in source** — a file or declaration exists.
2. **Installed** — artifacts were copied to an execution environment.
3. **Wired** — endpoints, queues, tasks, or capabilities were connected.
4. **Deployed** — the relevant runtime revision was actually serving.
5. **Executed** — a command ran on the intended target.
6. **Receipted** — an independently readable result was recorded.
7. **Accepted** — the named end-to-end test passed under the intended conditions.

No source file, installer message, queue acceptance, heartbeat, or passing unit test is silently upgraded to end-to-end acceptance.

## Public mirror and authority

The outward mirror is [Valar05/chromium-throne-excavation](https://github.com/Valar05/chromium-throne-excavation). The graveyard copy in Fortress Online Home Center Drive is the archival package requested by Drew. The historical implementation source remains in [Valar05/home-center](https://github.com/Valar05/home-center); this graveyard links to it without copying runnable implementation.

## Non-goals

- No installation or activation procedure.
- No copied extension package, relay, daemon, APK, shell script, or automation payload.
- No promise that any worker, phone, browser, daemon, queue, or endpoint is currently live.
- No licensing grant. Historical source remains governed by its own repository and history.
- No cleanup of contradictions by invention. Intention, implementation, deployment, and acceptance remain separate.

## Bottom line

The recovered architecture was a collection of cooperating control planes. Chromium Throne automated a dedicated desktop ChatGPT browser. Browser Nerve handled CDP-style browser tickets. Computer Hands was the broader workstation body. Phone Hands carried commands to Android and Termux. The overlay guarded screen-touch authority. Android Chromium control operated phone Chrome separately. Atom provided a phone-local command/intelligence aperture. Vlad synchronized fast Judgment Jar context and receipts. Venice and review gates participated in continuation and acceptance. The pieces formed a Fortress automation organism, but the surviving evidence does not prove that the complete organism reached stable end-to-end acceptance.
