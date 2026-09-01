# Phone Automation Excavation

## 1. What Phone Hands was

Phone Hands was a layered Android/Termux execution system. Home Center queued commands for a phone; the phone pulled and leased them; a relay dispatched each command to the appropriate local capability; the phone returned completion or failure material.

The key design decision was that **background execution and screen-touch execution had different authority paths**.

## 2. Layer map

| Layer | Recovered responsibility |
|---|---|
| Home Center phone relay | Queue, pull, lease, complete/fail, heartbeat |
| Device relay | Authentication, polling, capability dispatch, receipts |
| Termux shell | Background shell work independent of screen-control gates |
| Diagnostics | Device/status observations; designed for background use |
| Android bridge | Observe and act through Android privileged-command lane |
| Operator overlay | Visible control/mute/hide/collapse state, heartbeat, screen lease |
| Window composer | Higher-level screen/window coordination |
| Factory/armory drivers | Device-specific bounded capabilities |
| Android Chromium control | Chrome-family navigation and observed-state canaries |
| SSH Axis | Secondary phone/computer connectivity and service verification lane |
| Campaign runner | Probe, repair, verify, preserve receipts, assemble review packet |

## 3. Background Termux contract

The phone-runtime contract explicitly separated `phone_shell` from screen automation. Background Termux work was not supposed to depend on:

- Shizuku or `rish`;
- Wireless Debugging;
- an active overlay control gate;
- a screen activity lease;
- a visible UI session.

This separation mattered because an overlay or Android privilege failure should not erase the phone’s ability to run background maintenance, diagnostics, or recovery commands.

## 4. Android bridge

The recovered Android bridge exposed observation and action primitives through a protected HTTP service inside the Termux environment. Observations included foreground application, display, battery, UI hierarchy, and screenshots. Actions included tap, swipe, text entry, key events, home/back/recents, app launch, force-stop, and an optional shell capability.

The bridge was designed around private-network/loopback access plus bearer authorization and used Shizuku/`rish` for Android-side authority. This graveyard omits addresses, tokens, device identifiers, and runnable invocation details.

## 5. Cloud relay

The phone Home Center relay performed a repeating pull/lease/complete cycle for a named device queue. It declared capabilities and routed work to local modules including the Android bridge, Termux shell, diagnostics, overlay, Venice, window composition, factory tools, and armory drivers.

Recovered semantics:

1. A queued command was not yet leased.
2. A leased command was not yet executed.
3. A subprocess exit was not automatically an independently observed device outcome.
4. A completion receipt was not automatically human acceptance.
5. Screen-changing commands required overlay and lease authority.
6. Background shell and diagnostic commands bypassed the screen gate by design.

## 6. Operator overlay

The native Android package used the `com.homecenter.operatoroverlay` identity and exposed state through an Android content provider. Recovered state included control enabled/disabled, muted, collapsed, hidden, heartbeats, and screen-activity lease data.

The relay-side overlay reader was designed to fail closed if the package was missing, state could not be read, or control was disabled. This protected Drew’s manual control from invisible automation. Overlay failure was therefore expected to block UI work while leaving background Termux work recoverable.

## 7. Screen lease and coexistence

The screen lease coordinated automation with human use. A UI action should acquire or honor the lease, perform bounded work, and yield. This avoided two automation lanes or an automation lane and Drew fighting for the same screen. A stale heartbeat or unreadable state was a reason to stop, not permission to guess.

## 8. Android Chromium control

The phone-browser module identified installed Chrome-family packages and supported bounded operations such as open/navigate, reload, back, force-stop, and canary checks. It captured independent observations—focused task, UI evidence, and screen hashes—so “the command returned” could be compared with “the phone visibly changed.”

This module provided the phone side of the browser-automation vision. It did not establish that the desktop Chromium Throne extension ran on Android.

## 9. Campaign and recovery machinery

The recovered Fortress phone campaign script used an isolated runtime worktree so the live source tree remained untouched. It maintained state, history, a latest pointer, locks, and logs. It probed and attempted bounded repair for Atom, Vlad, SSH, the overlay, Phone Hands, and status surfaces. It also assembled review packets and required named review gates, including Vlad, Venice, and Tetsuya in recovered paths.

The campaign could reach an internal operational judgment but was not authorized to self-release. Review packet success and human acceptance remained distinct.

Other recovered support paths included:

- relay startup and recovery scripts;
- watchdogs and status menus;
- SSH service and Axis verification;
- Adam overlay deployment/recovery;
- local executive, diagnostics, factory tools, armory, and window composition;
- relay contract tests and Android build/overlay tests.

## 10. Phone-side trust boundaries

| Boundary | Fail-closed expectation |
|---|---|
| Queue authentication | No valid device/cloud material, no lease or completion |
| Local bridge authentication | No bearer authority, no bridge action |
| Android privilege | No Shizuku/rish, no privileged UI action |
| Overlay state | Missing/unreadable/disabled blocks screen control |
| Screen lease | Contention or stale authority blocks/yields UI action |
| Background shell | Must remain independent of UI gate failures |
| Observation | Action without observed state is incomplete evidence |
| Review | Machine completion does not grant release/acceptance |

## 11. Historical status and scars

- Source existed for the relay, bridge, overlay integration, Android native overlay, phone Chromium control, campaign, SSH, diagnostics, and support modules.
- Historical CI included Android build and Phone Hands relay-wiring failures.
- Recovery scripts attempted to detect and repair missing services; the existence of repair logic is not proof that repair succeeded on the current device.
- No current phone heartbeat, overlay state, Shizuku state, SSH Axis, browser canary, or end-to-end command receipt was freshly verified for this graveyard.

## 12. Disposition

Phone Hands should be understood as a receipted device-control fabric with two bodies: a resilient background Termux lane and a guarded Android UI lane. Android Chromium control sat on the UI/device side. Atom and Vlad supplied local command/context support. The graveyard preserves interfaces, safety gates, and known scars while withholding everything needed to reactivate the stack.
