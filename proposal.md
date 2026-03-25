# Google Summer of Code 2026 Proposal

**Organization:** Sugar Labs  
**Project:** GTK4 Transition Part 2 Sugar Shell  
**Proposal Title:** Completing GTK4 Migration and Wayland Support for the Sugar Shell  
**Submitted by:** Dev

## About Me

| Field                 | Details                                                                        |
| --------------------- | ------------------------------------------------------------------------------ |
| **Name**              | Dev                                                                            |
| **Degree**            | B.Tech in Computer Science                                                     |
| **Current Role**      | Undergraduate Student                                                          |
| **Email**             | kalpanagola9897@gmail.com                                                      |
| **Phone**             | +91 8077907751                                                                 |
| **GitHub**            | [https://github.com/dev10-sys](https://github.com/dev10-sys)                   |
| **LinkedIn**          | [https://www.linkedin.com/in/dev10-sys](https://www.linkedin.com/in/dev10-sys) |
| **Matrix**            | Dev (@dev10-sys:matrix.org)                                                    |
| **Time Zone**         | IST (GMT +5:30)                                                                |
| **Coding Mentors**    | Krish Pandya, Ibiam Chihurumnaya                                               |
| **Assisting Mentors** | Walter Bender, Juan Pablo Ugarte                                               |

## Previous Open Source Work

I have been contributing to Sugar Labs repositories, mainly focusing on the Sugar desktop environment and core shell components. My work includes fixing runtime issues, improving stability, fixing UI behavior issues, and working on GTK related migration and Wayland compatibility changes. I have worked on different parts of the Sugar desktop such as Journal, Frame, Clipboard, Control Panel, Datastore integration, and GTK related components. Along with Sugar desktop, I have also contributed to other Sugar Labs projects and open source networking test infrastructure.

### Contributions Table (Sugar Desktop – sugarlabs/sugar)

| Area              | Issue                         | What I Did                                                                                          | PR Link                                                                                      | Status |
| :---------------- | :---------------------------- | :-------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- | :----- |
| Datastore / DBus  | Datastore restart crash       | Fixed stale DBus proxy issue and implemented automatic reconnection and retry logic                 | [https://github.com/sugarlabs/sugar/pull/1030](https://github.com/sugarlabs/sugar/pull/1030) | Merged |
| Wayland Stability | Clipboard tray display issue  | Moved screen size lookup from import time to initialization to avoid Wayland startup crash          | [https://github.com/sugarlabs/sugar/pull/1059](https://github.com/sugarlabs/sugar/pull/1059) | Merged |
| Wayland Stability | Runtime display access crash  | Added guards for Gdk.Display and Gdk.Screen to prevent crashes during early startup                 | [https://github.com/sugarlabs/sugar/pull/1060](https://github.com/sugarlabs/sugar/pull/1060) | Merged |
| Control Panel     | Modem configuration crash     | Prevented crash when ISO country name missing by adding fallback to country code                    | [https://github.com/sugarlabs/sugar/pull/1061](https://github.com/sugarlabs/sugar/pull/1061) | Merged |
| Control Panel     | Excess disk writes            | Reused Gio.Settings instance to prevent repeated disk writes when moving age slider                 | [https://github.com/sugarlabs/sugar/pull/1063](https://github.com/sugarlabs/sugar/pull/1063) | Merged |
| Journal UI        | Activity chooser modal issue  | Set ActivityChooser transient for Journal window to ensure correct modal behavior                   | [https://github.com/sugarlabs/sugar/pull/1062](https://github.com/sugarlabs/sugar/pull/1062) | Open   |
| Frame / Clipboard | Clipboard paste failure       | Fixed paste failure when multiple clipboard items exist                                             | [https://github.com/sugarlabs/sugar/pull/1064](https://github.com/sugarlabs/sugar/pull/1064) | Open   |
| Journal           | Search focus lost             | Preserved search entry focus during async model refresh                                             | [https://github.com/sugarlabs/sugar/pull/1065](https://github.com/sugarlabs/sugar/pull/1065) | Open   |
| GTK4 Migration    | GTK3 deprecated API migration | Migrated deprecated GTK3 container, layout, and display APIs to GTK4 equivalents across Sugar shell | [https://github.com/sugarlabs/sugar/pull/1092](https://github.com/sugarlabs/sugar/pull/1092) | Open   |
| GTK4 Migration    | GTK4 container migration      | Replaced Gtk.VBox, Gtk.HBox, Gtk.Alignment, Gtk.EventBox and old container APIs                     | [https://github.com/sugarlabs/sugar/pull/1093](https://github.com/sugarlabs/sugar/pull/1093) | Open   |

### Other Sugar Labs Contributions (Music Blocks)

| Project         | Work                                                  | PR Link                                                                                                              | Status |
| :-------------- | :---------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------- | :----: |
| Music Blocks v4 | Cooperative scheduler and execution monitoring system | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/149](https://github.com/sugarlabs/musicblocks-v4-lib/pull/149) |  Open  |
| Music Blocks v4 | Recursive routine execution with call frame stack     | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/151](https://github.com/sugarlabs/musicblocks-v4-lib/pull/151) |  Open  |
| Music Blocks v4 | Variable tables by data type namespace                | [https://github.com/sugarlabs/musicblocks-v4-lib/pull/152](https://github.com/sugarlabs/musicblocks-v4-lib/pull/152) |  Open  |

### Other Open Source Contributions (SONiC Networking)

| Project                   | Work                                                                             | PR Link                                                                                                  | Status |
| :------------------------ | :------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------- | :----- |
| SONiC Test Infrastructure | Added IPv6 support for COPP tests and extended VOQ tests for single ASIC systems | [https://github.com/sonic-net/sonic-mgmt/pull/23181](https://github.com/sonic-net/sonic-mgmt/pull/23181) | Open   |
| SONiC Test Infrastructure | Extended VOQ counter test to support single ASIC systems                         | [https://github.com/sonic-net/sonic-mgmt/pull/23171](https://github.com/sonic-net/sonic-mgmt/pull/23171) | Open   |

These SONiC PRs add IPv6 support and extend test coverage for single ASIC VOQ systems.

Through these contributions, I have worked on different layers of the Sugar desktop including UI behavior, system integration, runtime stability, and ongoing GTK4 migration work. This experience helped me understand the Sugar shell architecture and the challenges involved in migrating a large GTK3 codebase to GTK4 while maintaining stability.

## Project Details

### What are you making

In this project I am working on migrating the Sugar Shell from GTK3 to GTK4 and improving its compatibility with Wayland based Linux systems.

From what I have studied while working on the Sugar desktop, the Sugar Shell is the core environment that manages the user interface, activity launching, Journal, and system integration. Right now most of the Sugar Shell is still based on GTK3 and some parts assume X11 behavior.

From the issues I worked on, I noticed that the main problem is not only deprecated APIs but the platform change from X11 to Wayland and from GTK3 to GTK4. The Linux desktop ecosystem is moving towards GTK4 and Wayland, and if Sugar stays on GTK3 and X11, it will become harder to run and maintain Sugar on modern systems.

So the goal of this project is to keep the Sugar behavior the same for users, but update the internal implementation so that it works on GTK4 and Wayland.

The main parts I will be working on are the Frame, Journal, Clipboard, Control Panel, and Activity launching system, because these components form the core of the Sugar desktop environment.

### System Architecture Overview

Before explaining the migration work, I want to explain how the Sugar system is structured, because the migration work depends on how different parts of the system interact with each other.

#### Sugar System Architecture

The Sugar Shell is written mostly in Python and uses PyGObject to interact with GTK. GTK then interacts with the display server which can be X11 or Wayland. The Sugar Shell also communicates with system services like DBus, GSettings, NetworkManager, and the Sugar Datastore.
This means the Sugar Shell sits between the user and the Linux system and acts as the main environment where everything runs.

```mermaid
flowchart TD
    %% Top Level User Interaction
    User((👤 User / Input Devices))

    %% User Interface & System Display Layer
    subgraph UI_Layer ["User Interface & Display Level"]
        direction LR
        GTK["GTK4 Toolkit"]
        Display["Wayland / X11 Server"]
    end

    %% The Middle Layer (Core)
    Shell{{"Sugar Shell\n(Python GTK)"}}

    %% System Configuration
    subgraph Config_Layer ["System Configuration Level"]
        direction LR
        GSettings["GSettings"]
        NetworkManager["NetworkManager"]
    end

    %% IPC Communication Layer
    DBus(("DBus Session Bus"))

    %% Background Services
    subgraph Services_Layer ["Sugar Microservices & Applications"]
        direction LR
        Activities["Activities (Apps)"]
        Journal["Journal Service"]
        Notifications["Notifications"]
        Datastore["Sugar Datastore"]
    end

    %% Persistence Layer
    Storage[("File System Storage")]

    %% Interactions emphasizing Sugar Shell as the Middle Layer
    User -->|Interacts with| Shell

    Shell -->|Renders UI via| GTK
    GTK -->|Displays on| Display

    Shell -->|Reads / Writes Config| GSettings
    Shell -->|Monitors Network| NetworkManager

    Shell ===>|Primary Communication| DBus

    DBus -->|Spawns & Tracks| Activities
    DBus -->|Logs Events| Journal
    DBus -->|Displays| Notifications
    DBus -->|Read / Write Metadata| Datastore

    Datastore -->|Persists Data| Storage

    %% Styling for Professional Architectural Look
    style Shell fill:#ff9f43,stroke:#ee5253,stroke-width:4px,color:#fff,font-weight:bold
    style DBus fill:#1dd1a1,stroke:#10ac84,stroke-width:2px,color:#fff
    style GTK fill:#54a0ff,stroke:#2e86de,stroke-width:2px,color:#fff
    style Display fill:#c8d6e5,stroke:#8395a7,stroke-width:1px
    style GSettings fill:#c8d6e5,stroke:#8395a7,stroke-width:1px
    style NetworkManager fill:#c8d6e5,stroke:#8395a7,stroke-width:1px
    style Storage fill:#576574,stroke:#222f3e,stroke-width:2px,color:#fff
    style Activities fill:#feca57,stroke:#ff9f43,stroke-width:1px
    style Journal fill:#feca57,stroke:#ff9f43,stroke-width:1px
    style Datastore fill:#feca57,stroke:#ff9f43,stroke-width:1px
    style Notifications fill:#feca57,stroke:#ff9f43,stroke-width:1px
```

_This diagram shows how the Sugar system is structured. The Sugar Shell sits between the user and the Linux system. It uses GTK for the user interface and communicates with system services using DBus. Activities, Journal, Datastore, NetworkManager, and Notifications all communicate with the Sugar Shell through DBus. This shows that the Sugar Shell is the central layer of the system._

### How Activities Depend on the Sugar Shell

This is important because the GTK4 migration of the Shell also affects activities.

From this architecture, I understand that activities do not run independently. They depend on the Sugar Shell for launching, saving data, accessing the Journal, clipboard, and network services.

Because of this, I think that migrating the Sugar Shell to GTK4 is a base step. Once the Shell is stable on GTK4, activities can run on top of a GTK4 environment and activity migration becomes easier and more stable.

```mermaid
sequenceDiagram
    participant User
    participant HomeView
    participant ShellModel
    participant DBus
    participant Activity

    User->>HomeView: Click Activity Icon
    HomeView->>ShellModel: Launch Request
    ShellModel->>DBus: Start Activity Service
    DBus->>Activity: Launch Process
    Activity->>DBus: Register Service
    DBus->>ShellModel: Activity Started
    ShellModel->>Activity: Set Active
```

_This diagram shows how activities are launched. The user clicks an activity icon, the Home View sends a launch request to the ShellModel, the ShellModel starts the activity through DBus, and the activity registers its DBus service and opens its window. The ShellModel then tracks the activity and manages its lifecycle._

### GTK3 to GTK4 Migration Architecture

Now the migration itself is not just replacing widgets. It is a transition from an older GTK3 and X11 based architecture to a GTK4 and Wayland compatible architecture.

In GTK3 many APIs like old container widgets, screen based display handling, and some styling methods are deprecated. GTK4 uses new container APIs, event controllers, CSS based styling, and different display handling methods which are more compatible with Wayland.
So this migration involves updating container APIs, layout handling, display handling, styling, and input handling so that the Sugar Shell works correctly on GTK4.

```mermaid
flowchart LR
    %% Deprecated Components
    subgraph Legacy ["🛑 GTK3 Legacy APIs"]
        direction TB
        EventBox["Gtk.EventBox"]
        GdkScreen["Gdk.Screen"]
        ContainerAPI["Old Container APIs\n(VBox, HBox, pack_start)"]
        OldSignals["Old Event Signals\n(button-press-event)"]
        ModifyBG["Legacy Styling\n(modify_bg, modify_color)"]
    end

    %% Modern Equivalents
    subgraph Modern ["✅ GTK4 Modern APIs"]
        direction TB
        GestureController["Gtk.GestureClick / Controllers"]
        GdkDisplay["Gdk.Display / Monitors"]
        NewLayoutAPI["New Layout APIs\n(Gtk.Box, append/prepend)"]
        EventControllers["Gtk.EventController"]
        CSSStyling["GTK CSS Providers &\nStyleContext"]
    end

    %% Mapping connections
    Legacy ===>|Structured Migration| Modern

    EventBox --> GestureController
    GdkScreen --> GdkDisplay
    ContainerAPI --> NewLayoutAPI
    OldSignals --> EventControllers
    ModifyBG --> CSSStyling

    %% Styling
    classDef legacy fill:#ffcccc,stroke:#e74c3c,stroke-width:2px,color:#c0392b;
    classDef modern fill:#d5f5e3,stroke:#2ecc71,stroke-width:2px,color:#27ae60;

    class Legacy,EventBox,GdkScreen,ContainerAPI,OldSignals,ModifyBG legacy;
    class Modern,GestureController,GdkDisplay,NewLayoutAPI,EventControllers,CSSStyling modern;
```

_This diagram shows what changes are required for GTK4. Several GTK3 APIs such as EventBox, old container APIs, screen based display APIs, old event signals, and old styling methods are removed in GTK4 and must be replaced with new GTK4 APIs and event controllers._

### Internal Sugar Shell Components

To make the migration structured, I will work component by component inside the Sugar Shell.

```mermaid
flowchart TD
    %% Base Level
    Main["⚙️ main.py (Entry Point)"]

    %% Core Components
    subgraph Core ["Sugar Shell Internal Modules"]
        direction TB
        ShellModel{{"ShellModel\n(Central State & Logic)"}}

        %% Views Section
        subgraph Views ["Shell Views & Logic"]
            Home["🏠 Home View"]
            Journal["📓 Journal"]
            ControlPanel["⚙️ Control Panel"]
        end

        %% Frame Section
        subgraph FrameSystem ["Frame Overlay Elements"]
            Frame["🔲 Frame System"]
            Clipboard["📋 Clipboard Tray"]
            Devices["💾 Device Tray"]
            Friends["🌐 Network Tray"]
            ActivitiesTray["🔄 Running Activities"]
        end

        %% Management Section
        subgraph Mngmt ["Lifecycle & App Management"]
            Launcher["🚀 Activity Launcher"]
            ActivityManager["📦 Activity Lifecycle Manager"]
        end
    end

    %% External Systems via DBus
    subgraph Env ["OS Environment"]
        DBus(("🔌 DBus Services"))
        WindowManager["🪟 Window Tracking"]
    end

    %% Core routing
    Main ===>|Initializes| ShellModel

    %% Model tracking to views
    ShellModel -->|Manages| Home
    ShellModel -->|Provides Context to| Journal
    ShellModel -->|Provides Configuration to| ControlPanel
    ShellModel ==>|Controls Layout for| Frame

    %% Routing inside the frame
    Frame -.->|Contains| Clipboard
    Frame -.->|Contains| Devices
    Frame -.->|Contains| Friends
    Frame -.->|Contains| ActivitiesTray

    %% Lifecycle Logic
    ShellModel ==>|Triggers Actions on| Launcher
    ShellModel ==>|Monitors state via| ActivityManager

    %% Interaction with Operating System
    ActivityManager ===>|Orchestrates processes via| DBus
    ActivityManager -.->|Observes events from| WindowManager

    %% Styling
    style Main fill:#bdc3c7,stroke:#95a5a6,stroke-width:2px
    style ShellModel fill:#f39c12,stroke:#d35400,stroke-width:4px,color:#fff
    style DBus fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff
    style ActivityManager fill:#9b59b6,stroke:#8e44ad,stroke-width:2px,color:#fff
    style FrameSystem fill:#e8f8f5,stroke:#1abc9c,stroke-width:1px
```

_The ShellModel is the central component that manages the Home View, Frame, Journal, Control Panel, and Activity Launcher, and also manages the activity lifecycle and DBus communication._

This helps in planning the migration because each of these components uses GTK widgets and display handling in different ways.

### DBus Communication Architecture

Sugar components communicate using DBus, especially for launching activities and accessing the datastore.

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant SS as Sugar Shell
    participant DB as DBus System/Session Bus
    participant AM as Activity Manager
    participant Act as Activity Runtime
    participant DS as Datastore

    User->>SS: Initiates Activity Launch
    SS->>DB: Send Launch Request (org.laptop.Activity)
    DB->>AM: Forward Request & Parameters
    AM->>Act: Initialize GTK Runtime Environment
    Act->>DB: Request Service Connections
    Act->>DB: Read/Write Application State
    DB->>DS: Execute Datastore I/O Operations
    DS-->>DB: State Acknowledgment
    DB-->>Act: Data Ready
    Act-->>SS: Window Mapped & UI Rendered
```

This is important because GTK4 migration should not break DBus communication or activity lifecycle.

### What Work Will Be Done

I will divide the work into several technical parts.

```mermaid
flowchart TD
    %% Workflow steps
    Phase1(["Phase 1: Critical Safety Fixes\n(Crashing bugs)"])
    Phase2(["Phase 2: Display & Monitor API\nMigration"])
    Phase3(["Phase 3: Container and Widget\nMigration"])
    Phase4(["Phase 4: Event Handling &\nInput Migration"])
    Phase5(["Phase 5: CSS & Styling\nMigration"])
    Phase6(["Phase 6: Wayland API\nCompatibility Fixes"])
    Phase7{{"Phase 7: Final Testing &\nStabilization"}}

    %% Connections
    Phase1 ===> Phase2
    Phase2 ===> Phase3
    Phase3 ===> Phase4
    Phase4 ===> Phase5
    Phase5 ===> Phase6
    Phase6 ===> Phase7

    %% Styling
    classDef phaseNode fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff,font-weight:bold;
    classDef finalNode fill:#2ecc71,stroke:#27ae60,stroke-width:4px,color:#fff,font-weight:bold;

    class Phase1,Phase2,Phase3,Phase4,Phase5,Phase6 phaseNode;
    class Phase7 finalNode;
```

_The migration will be done in phases. After each phase, the system will be tested to make sure the Sugar Shell remains stable._

I will migrate and test the system at the same time. After each migration phase, I will run the Sugar Shell and test activity launch, Journal, Frame, and Control Panel on both X11 and Wayland to make sure the system remains stable.

One of the most complex parts of this migration is the Frame system because it depends on screen geometry, window positioning, and input events. These areas are affected by GTK4 API changes and Wayland restrictions. So I will migrate the Frame carefully and test it on both X11 and Wayland to make sure the overlay panels, hot corners, and clipboard tray work correctly.

**1. GTK4 API Migration**
I will replace deprecated GTK3 APIs with GTK4 equivalents. This includes container APIs, layout APIs, widget APIs, and dialog APIs. This work will be done component by component in the Sugar Shell.

**2. Display and Monitor Handling**
GTK4 uses a different display and monitor system compared to GTK3. Old screen based APIs need to be replaced with GTK4 display and monitor APIs. This is important for Wayland compatibility.

**3. Styling Migration**
Old styling methods are deprecated in GTK4, so styling will be migrated to GTK CSS using CSS providers.

**4. Wayland Compatibility**
Some parts of Sugar assume X11 behavior. These parts need to be updated so that Sugar works correctly under Wayland where some X11 specific features are not available.

**5. Testing and Stability**
After migration, I will test the Frame, Journal, Clipboard, Control Panel, and Activity launching system to make sure the system works correctly and does not crash.

### How Will It Impact Sugar Labs

The Sugar Shell is the main environment where all activities run. Activities depend on the Sugar Shell for launching, window management, datastore access, Journal integration, and system services.
Because of this, I think that migrating the Sugar Shell to GTK4 is a base platform step. Once the Shell runs on GTK4 and Wayland, activities can be migrated and tested on a stable GTK4 environment.

Right now many Linux distributions have already moved to Wayland and GTK4, but Sugar is still mostly based on GTK3 and X11.

```mermaid
flowchart TD
    %% Current State
    subgraph LegacyEnv ["Old Application Environment"]
        OldSugar["Sugar Window Handling\n(Legacy Patterns)"]

        subgraph X11Features ["X11 Specific Methods (Deprecated in Wayland)"]
            direction TB
            X11Calls{"X11 APIs"}
            WindowMove["Absolute Window Positioning / Move"]
            ScreenSize["Global Screen Geometry Lookups"]
            ForeignWindows["Foreign Window Interception"]
        end

        OldSugar --> X11Calls
        X11Calls -.-> WindowMove
        X11Calls -.-> ScreenSize
        X11Calls -.-> ForeignWindows
    end

    %% Target State
    subgraph ModernEnv ["Modern Display Ecosystem"]
        NewLinux{"Modern Linux Distributions\n(GNOME / KMS)"}
        Wayland(("Wayland Compositor"))

        subgraph WaylandRestrictions ["Wayland Protocol Restrictions (Security & Design)"]
            direction TB
            Restriction1["🚫 No Absolute Window Moves (Client-side)"]
            Restriction2["🚫 No Arbitrary Foreign Window Tracking"]
            Restriction3["✅ Monitor-Based Local Geometry Only"]
        end

        NewLinux --> Wayland
        Wayland --> Restriction1
        Wayland --> Restriction2
        Wayland --> Restriction3
    end

    %% The Clash
    LegacyEnv ===>|Compatibility Conflict| WaylandRestrictions
    WaylandRestrictions ===>|necessitates| Result

    Result{{"GTK4 & Wayland Migration Required\n(Updating APIs & Focus Systems)"}}

    %% Styling
    classDef legacy fill:#ffeaa7,stroke:#fdcb6e,stroke-width:2px;
    classDef conflict fill:#ff7675,stroke:#d63031,stroke-width:2px,color:#fff;
    classDef modern fill:#74b9ff,stroke:#0984e3,stroke-width:2px,color:#fff;
    classDef target fill:#55efc4,stroke:#00b894,stroke-width:3px,color:#2d3436,font-weight:bold;

    class LegacyEnv,X11Features legacy;
    class WaylandRestrictions,Restriction1,Restriction2,Restriction3 conflict;
    class ModernEnv,NewLinux,Wayland modern;
    class Result target;

```

_This diagram shows why Wayland support requires changes in Sugar. The old Sugar system depends on X11 specific features like window positioning and foreign windows, which are not supported in Wayland. Therefore the Sugar Shell needs to be updated to work correctly on Wayland._

If Sugar is not migrated, it may face compatibility and maintenance problems in the future.
So I see this project not just as a UI migration, but as a platform transition that helps Sugar run on modern Linux systems and makes future development easier.

This project reduces technical debt in the Sugar Shell and makes future development easier because new features can be built on GTK4 instead of maintaining deprecated GTK3 code.

### Technologies I Will Be Using

| Component                | Technology      |
| :----------------------- | :-------------- |
| **Programming Language** | Python 3        |
| **GUI Framework**        | GTK3 to GTK4    |
| **Python Bindings**      | PyGObject       |
| **Display Systems**      | Wayland and X11 |
| **IPC**                  | DBus            |
| **Settings**             | GSettings       |
| **Storage**              | Sugar Datastore |
| **Build System**         | Autotools       |
| **Styling**              | GTK CSS         |
| **Networking**           | NetworkManager  |

Most of the Sugar Shell code is written in Python and uses PyGObject to interact with GTK, so most of the migration work will involve updating GTK APIs and display handling in Python code.
