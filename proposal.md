# Google Summer of Code 2026 Proposal

**Organization:** Sugar Labs  
**Project:** GTK4 Transition Part 2 Sugar Shell  
**Proposal Title:** Completing GTK4 Migration and Wayland Support for the Sugar Shell  
**Submitted by:** Dev  

## About Me

| Field | Details |
| --- | --- |
| **Name** | Dev |
| **Degree** | B.Tech in Computer Science |
| **Current Role** | Undergraduate Student |
| **Email** | kalpanagola9897@gmail.com |
| **Phone** | +91 8077907751 |
| **GitHub** | [https://github.com/dev10-sys](https://github.com/dev10-sys) |
| **LinkedIn** | [https://www.linkedin.com/in/dev10-sys](https://www.linkedin.com/in/dev10-sys) |
| **Matrix** | Dev (@dev10-sys:matrix.org) |
| **Time Zone** | IST (GMT +5:30) |
| **Coding Mentors** | Krish Pandya, Ibiam Chihurumnaya |
| **Assisting Mentors** | Walter Bender, Juan Pablo Ugarte |

## Previous Open Source Work

I have been contributing to Sugar Labs repositories, mainly focusing on the Sugar desktop environment and core shell components. My work includes fixing runtime issues, improving stability, fixing UI behavior issues, and working on GTK related migration and Wayland compatibility changes. I have worked on different parts of the Sugar desktop such as Journal, Frame, Clipboard, Control Panel, Datastore integration, and GTK related components. Along with Sugar desktop, I have also contributed to other Sugar Labs projects and open source networking test infrastructure.

### Contributions Table (Sugar Desktop – sugarlabs/sugar)

| Area | Issue | What I Did | PR Link | Status |
| :--- | :--- | :--- | :--- | :--- |
| Datastore / DBus | Datastore restart crash | Fixed stale DBus proxy issue and implemented automatic reconnection and retry logic | [https://github.com/sugarlabs/sugar/pull/1030](https://github.com/sugarlabs/sugar/pull/1030) | Merged |
| Wayland Stability | Clipboard tray display issue | Moved screen size lookup from import time to initialization to avoid Wayland startup crash | [https://github.com/sugarlabs/sugar/pull/1059](https://github.com/sugarlabs/sugar/pull/1059) | Merged |
| Wayland Stability | Runtime display access crash | Added guards for Gdk.Display and Gdk.Screen to prevent crashes during early startup | [https://github.com/sugarlabs/sugar/pull/1060](https://github.com/sugarlabs/sugar/pull/1060) | Merged |
| Control Panel | Modem configuration crash | Prevented crash when ISO country name missing by adding fallback to country code | [https://github.com/sugarlabs/sugar/pull/1061](https://github.com/sugarlabs/sugar/pull/1061) | Merged |
| Control Panel | Excess disk writes | Reused Gio.Settings instance to prevent repeated disk writes when moving age slider | [https://github.com/sugarlabs/sugar/pull/1063](https://github.com/sugarlabs/sugar/pull/1063) | Merged |
| Journal UI | Activity chooser modal issue | Set ActivityChooser transient for Journal window to ensure correct modal behavior | [https://github.com/sugarlabs/sugar/pull/1062](https://github.com/sugarlabs/sugar/pull/1062) | Open |
| Frame / Clipboard | Clipboard paste failure | Fixed paste failure when multiple clipboard items exist | [https://github.com/sugarlabs/sugar/pull/1064](https://github.com/sugarlabs/sugar/pull/1064) | Open |
| Journal | Search focus lost | Preserved search entry focus during async model refresh | [https://github.com/sugarlabs/sugar/pull/1065](https://github.com/sugarlabs/sugar/pull/1065) | Open |
| GTK4 Migration | GTK3 deprecated API migration | Migrated deprecated GTK3 container, layout, and display APIs to GTK4 equivalents across Sugar shell | [https://github.com/sugarlabs/sugar/pull/1092](https://github.com/sugarlabs/sugar/pull/1092) | Open |
| GTK4 Migration | GTK4 container migration | Replaced Gtk.VBox, Gtk.HBox, Gtk.Alignment, Gtk.EventBox and old container APIs | [https://github.com/sugarlabs/sugar/pull/1093](https://github.com/sugarlabs/sugar/pull/1093) | Open |

### Other Sugar Labs Contributions (Music Blocks)

| Project | Work | PR Link | Status |
| :--- | :--- | :--- | : :--- |
| Music Blocks v4 | Cooperative scheduler and execution monitoring system | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/149](https://github.com/sugarlabs/musicblocks-v4-lib/pull/149) | Open |
| Music Blocks v4 | Recursive routine execution with call frame stack | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/151](https://github.com/sugarlabs/musicblocks-v4-lib/pull/151) | Open |
| Music Blocks v4 | Variable tables by data type namespace | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/152](https://github.com/sugarlabs/musicblocks-v4-lib/pull/152) | Open |

### Other Open Source Contributions (SONiC Networking)

| Project | Work | PR Link | Status |
| :--- | :--- | :--- | :--- |
| SONiC Test Infrastructure | Added IPv6 support for COPP tests and extended VOQ tests for single ASIC systems | [https://github.com/sonic-net/sonic-mgmt/pull/23181](https://github.com/sonic-net/sonic-mgmt/pull/23181) | Open |
| SONiC Test Infrastructure | Extended VOQ counter test to support single ASIC systems | [https://github.com/sonic-net/sonic-mgmt/pull/23171](https://github.com/sonic-net/sonic-mgmt/pull/23171) | Open |

These SONiC PRs add IPv6 support and extend test coverage for single ASIC VOQ systems.

Through these contributions, I have worked on different layers of the Sugar desktop including UI behavior, system integration, runtime stability, and ongoing GTK4 migration work. This experience helped me understand the Sugar shell architecture and the challenges involved in migrating a large GTK3 codebase to GTK4 while maintaining stability.
