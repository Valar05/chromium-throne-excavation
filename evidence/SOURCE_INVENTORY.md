# Source and Evidence Inventory

## 1. Provenance rules

This inventory points to the historical public source in [Valar05/home-center](https://github.com/Valar05/home-center). It does not copy runnable implementation. Paths were recovered from the default-branch source and Fortress/Home Center records on 2026-09-01.

Observed file SHAs identify particular blobs seen during excavation, not a complete repository lockfile. The visible source snapshot was around commit `ec5a24d…`; the deployed Home Center bridge reported source commit `75407a…` and revision `homecentermcp-00244-lad`. Because those differ, deployment state must not be inferred from current source.

## 2. Chromium Throne / Browser Porch

| Path | Role | Observed evidence |
|---|---|---|
| [`browser-porch/README.md`](https://github.com/Valar05/home-center/blob/main/browser-porch/README.md) | Source-area orientation and status caveat | Implemented-in-source language; deployment/acceptance not guaranteed |
| [`browser-porch/extension/manifest.json`](https://github.com/Valar05/home-center/blob/main/browser-porch/extension/manifest.json) | MV3 identity, permissions, hosts, version | v0.7.0; ChatGPT and localhost relay permissions |
| [`browser-porch/extension/swarm-core.mjs`](https://github.com/Valar05/home-center/blob/main/browser-porch/extension/swarm-core.mjs) | Queue/slice/context/handoff model | Blob `632912…`; bounded context, Venice directives, slice concepts |
| [`browser-porch/extension/throne-panel.mjs`](https://github.com/Valar05/home-center/blob/main/browser-porch/extension/throne-panel.mjs) | Side-panel UI and control messages | Blob `b421…`; queue/run/capture/stop/resume |
| [`browser-porch/extension/service-worker.js`](https://github.com/Valar05/home-center/blob/main/browser-porch/extension/service-worker.js) | Main browser worker/state machine | Blob `ed2efa…`; tab reuse, DOM injection, capture, polling, storage, receipts |
| [`browser-porch/throne-relay-runner.mjs`](https://github.com/Valar05/home-center/blob/main/browser-porch/throne-relay-runner.mjs) | Local relay | Blob `801904…`; loopback binding, origin/capability checks, event log |
| [`browser-porch/throne-client.mjs`](https://github.com/Valar05/home-center/blob/main/browser-porch/throne-client.mjs) | Command client/wake path | Blob `11d69…`; runtime config, command POST, extension wake page |
| [`tools/install_chromium_throne.ps1`](https://github.com/Valar05/home-center/blob/main/tools/install_chromium_throne.ps1) | Windows install/runtime scaffold | Pinned source/build, dedicated profile, single worker, receipt, auth gate |
| [`tools/fortress-universal-bootstrap.sh`](https://github.com/Valar05/home-center/blob/main/tools/fortress-universal-bootstrap.sh) | Broader Fortress bootstrap lineage | Chromium Throne runtime/config/log/task footprint plus phone startup references |

## 3. Adjacent desktop browser/control lanes

| Path or record | Role | Status caveat |
|---|---|---|
| [`tools/apply_browser_nerve_executor_patch.mjs`](https://github.com/Valar05/home-center/blob/main/tools/apply_browser_nerve_executor_patch.mjs) | Browser Nerve CDP ticket worker patching | Search evidence showed worker/ticket lifecycle; fresh deployment not verified |
| Computer Hands capability records | General Windows execution body (`windows-hands-01`, THECAULDRON) | Capability declarations are not current heartbeat proof |
| Historical PR #245 | Chromium Throne integration lineage | Merge/integration is not runtime acceptance |
| Historical CI/workflow records | Chromium Throne/Home Center contract checks | Failures were observed around 2026-08-13/14 |

## 4. Phone Hands and Android

| Path | Role | Observed evidence |
|---|---|---|
| [`skills/phone-runtime/SKILL.md`](https://github.com/Valar05/home-center/blob/main/skills/phone-runtime/SKILL.md) | Canonical phone runtime contract | Blob `03a9…`; background Termux separated from UI gates |
| [`tools/android_phone_hands_bridge.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_hands_bridge.py) | Protected Android observation/action bridge | Blob `a2d080…`; Shizuku/rish, observe/act primitives |
| [`tools/android_phone_home_center_relay.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_home_center_relay.py) | Cloud queue pull/lease/dispatch/complete relay | Blob `ad90e…`; capability router; background/UI split |
| [`tools/android_operator_overlay.py`](https://github.com/Valar05/home-center/blob/main/tools/android_operator_overlay.py) | Relay-side overlay state/gate integration | Blob `a4cdb…`; fail-closed control and lease state |
| [`android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorOverlayService.java`](https://github.com/Valar05/home-center/blob/main/android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorOverlayService.java) | Native overlay service | Source presence only; current APK/device install not verified |
| [`android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorState.java`](https://github.com/Valar05/home-center/blob/main/android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorState.java) | Native overlay state model | Source presence only |
| [`android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorStateProvider.java`](https://github.com/Valar05/home-center/blob/main/android/operator-overlay/app/src/main/java/com/homecenter/operatoroverlay/OperatorStateProvider.java) | Content-provider state surface | Source presence only |
| [`tools/android_chromium_control.py`](https://github.com/Valar05/home-center/blob/main/tools/android_chromium_control.py) | Phone Chrome-family automation/canary | Blob `385a…`; independent focus/UI/screen observations |
| [`tools/fortress_phone_campaign.sh`](https://github.com/Valar05/home-center/blob/main/tools/fortress_phone_campaign.sh) | Probe/repair/verify/review campaign | Blob `5158…`; isolated worktree; cannot self-release |
| [`tools/start_android_phone_hands.sh`](https://github.com/Valar05/home-center/blob/main/tools/start_android_phone_hands.sh) | Relay startup | Current service state not verified |
| [`tools/home_center_phone_relay_recover.sh`](https://github.com/Valar05/home-center/blob/main/tools/home_center_phone_relay_recover.sh) | Canonical relay recovery path | Recovery mechanism is not recovery receipt |
| [`tools/phone_hands_watchdog.sh`](https://github.com/Valar05/home-center/blob/main/tools/phone_hands_watchdog.sh) | Phone Hands supervision | Source presence only |
| [`tools/phone_hands_relay_contract_test.mjs`](https://github.com/Valar05/home-center/blob/main/tools/phone_hands_relay_contract_test.mjs) | Relay contract test | Contract test is not device E2E acceptance |
| [`tools/phone_ssh_service.sh`](https://github.com/Valar05/home-center/blob/main/tools/phone_ssh_service.sh) | Phone SSH service support | Current service state not verified |
| [`tools/ssh_axis.py`](https://github.com/Valar05/home-center/blob/main/tools/ssh_axis.py) | SSH Axis validation/control | Current axis not verified |
| [`tools/android_phone_termux_shell.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_termux_shell.py) | Background Termux command path | Must remain independent of overlay/UI authority |
| [`tools/android_phone_diagnostics.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_diagnostics.py) | Background device diagnostics | Observation scope varies by available authority |
| [`tools/android_phone_local_executive.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_local_executive.py) | Phone-local executive | Source presence only |
| [`tools/android_window_composer.py`](https://github.com/Valar05/home-center/blob/main/tools/android_window_composer.py) | Window/UI coordination | Screen gate and lease still apply |
| [`tools/android_phone_factory_tools.py`](https://github.com/Valar05/home-center/blob/main/tools/android_phone_factory_tools.py) | Device factory capabilities | Source presence only |
| [`tools/android_armory_driver.py`](https://github.com/Valar05/home-center/blob/main/tools/android_armory_driver.py) | Device-specific armory driver | Source presence only |
| [`tools/home_center_status_menu.sh`](https://github.com/Valar05/home-center/blob/main/tools/home_center_status_menu.sh) | Phone-local status surface | Displayed status is only as current as probes |
| [`tools/deploy_adam_overlay_phone.sh`](https://github.com/Valar05/home-center/blob/main/tools/deploy_adam_overlay_phone.sh) | Adam overlay/CLI/Vlad deployment bundle | Deployment script is not deployment receipt |
| [`tools/recover_adam_overlay_phone.sh`](https://github.com/Valar05/home-center/blob/main/tools/recover_adam_overlay_phone.sh) | Overlay recovery | Recovery intent only without canary |

## 5. Vlad / Atom / Judgment Jars

| Path | Role | Observed evidence |
|---|---|---|
| [`tools/vlad_swarm_daemon.py`](https://github.com/Valar05/home-center/blob/main/tools/vlad_swarm_daemon.py) | Persistent Vlad daemon / Jar sync heartbeat | Source found; current process and sync not verified |
| [`tools/setup_vlad_swarm_daemon.sh`](https://github.com/Valar05/home-center/blob/main/tools/setup_vlad_swarm_daemon.sh) | State/log/service-receipt/source-hash setup | Search evidence showed retained state and receipt layout |
| [`tools/install_atom_vlad_phone.sh`](https://github.com/Valar05/home-center/blob/main/tools/install_atom_vlad_phone.sh) | Combined Atom + Vlad phone setup/probe | Installer receipt is not accepted service |
| [`tools/install_atom_phone.sh`](https://github.com/Valar05/home-center/blob/main/tools/install_atom_phone.sh) | Atom install and Vlad prerequisite/boot linkage | Source presence only |
| [`docs/VLAD_JUDGMENT_JAR_FAST_ACCESS.md`](https://github.com/Valar05/home-center/blob/main/docs/VLAD_JUDGMENT_JAR_FAST_ACCESS.md) | Fast context, typed receipts, review-verdict import | Captured/pending/delivered distinctions preserved |
| Fortress phone campaign | Vlad PID/receipt probe, repair, and GO/GO-WITH-SCAR review gate | Campaign result not freshly run |
| Overlay/Jar tests | Vlad/Jar integration and recovery lineage | Test presence does not prove field deployment |

## 6. Historical acceptance scars

Recovered workflow history around 2026-08-13 and 2026-08-14 included failures labeled or associated with:

- Chromium Throne Contract;
- Home Center CI;
- Build Android;
- Phone Hands Relay Wiring.

These are integration scars, not a universal verdict. The excavation found no authoritative later receipt proving the entire browser + phone + Vlad chain passed under the final intended topology.

## 7. Evidence ledger

| Claim | Evidence grade |
|---|---|
| Chromium Throne had an MV3 extension, relay, client, installer, and profile contract | Strong source evidence |
| Browser Nerve was a separate CDP ticket executor | Strong source/search evidence |
| Phone Hands separated background Termux from guarded UI work | Strong source contract evidence |
| Android Chromium control was separate from desktop Chromium Throne | Strong source evidence |
| Vlad synchronized Judgment Jar fast context for Atom/review paths | Strong source/documentation evidence |
| Vlad directly controlled taps or Chromium tabs | Unsupported; rejected |
| The full organism was currently live on 2026-09-01 | Not tested; unknown |
| The full organism ever achieved stable accepted E2E operation | No authoritative acceptance receipt recovered |

## 8. Exclusions

This inventory excludes credentials, access tokens, private addresses, device-specific secrets, copied implementation bodies, binaries, APKs, extension packages, service files, activation commands, and anything that would turn the graveyard into a revival kit.
