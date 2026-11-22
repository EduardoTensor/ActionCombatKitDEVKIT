# Action Combat Kit

> **Note:** This repository contains an Unreal Engine 5 gameplay-system prototype developed as a study and portfolio project. Its primary focus is demonstrating modular gameplay architecture, reusable Actor Components, Blueprint Interfaces, and organized gameplay logic.

## Technical Details

* **Engine:** Unreal Engine 5
* **Implementation:** 100% **Blueprints**
* **Architecture:** Component-Based Architecture
* **Communication:** Blueprint Interfaces
* **Status:** In Development / Portfolio Project
* **Main Components:** `BPC_LockOn`, `BPC_Health`
* **Main Interface:** `BPI_Targettable`
* **UI:** `WBP_LockOnMarker`, `WBP_HealthBar`

## Documentation

Technical documentation and project development notes are available in the `Documentation/` directory.

* **Technical Documentation:** Detailed explanation of system architecture, implemented components, planned combat systems, and development conventions.
* **Project Development Notes:** Development phases, Blueprint function references, implementation progress, and technical decisions.

## Project Overview

Action Combat Kit is a modular third-person action-combat system prototype inspired by games such as Devil May Cry, Bayonetta, and God of War.

Instead of concentrating all gameplay logic inside a single Character Blueprint, the project focuses on separating responsibilities into independent and reusable components.

The main objective is to create a foundation where individual gameplay systems can be developed, tested, maintained, and extended independently.

## Implemented Systems

| System | Component | Description |
| :--- | :--- | :--- |
| **Lock-On System** | `BPC_LockOn` | Handles target acquisition, target validation, target switching, camera behavior, and strafing. |
| **Target Interface** | `BPI_Targettable` | Provides interface-based communication with valid targets, reducing direct dependencies on specific enemy classes. |
| **Health System** | `BPC_Health` | Handles health management, damage, healing, death states, and communication with the Lock-On system. |
| **Lock-On Marker** | `WBP_LockOnMarker` | Displays a visual indicator for the currently selected target. |
| **Health Bar** | `WBP_HealthBar` | Widget associated with the Health System. |

### Lock-On System

The Lock-On system is responsible for managing target interactions and camera behavior.

Implemented functionality includes:

* Target acquisition and validation.
* Automatic target selection based on distance and visibility.
* Target switching using mouse or analog stick input.
* Camera behavior that follows the selected target.
* Over-the-shoulder camera positioning.
* Character strafing while locked on.
* Visual target marker.
* Automatic unlocking when the target dies, is removed, or moves beyond the allowed range.
* Line-of-sight validation to prevent locking onto enemies behind walls.

The system uses `BPC_LockOn` together with `BPI_Targettable` to avoid depending on a specific enemy Blueprint class.

### Health System

The Health System is implemented through the reusable `BPC_Health` Actor Component.

Its responsibilities include:

* Health management.
* Receiving damage through Unreal Engine's damage system.
* Healing.
* Death handling.
* Health change notifications.
* Death event communication.
* Communication with the Lock-On system through the target interface.

The component is designed to operate independently from the Lock-On system.

The `WBP_HealthBar` widget is associated with the Health System. Its final integration and behavior are still subject to verification.

## Controls & Core Mechanics

| Input | Action | Description |
| :--- | :--- | :--- |
| **Q (Hold)** | **Lock-On** | Locks onto a valid target while the key is held. Releasing the key unlocks the target. |
| **Mouse / Analog Stick** | **Switch Target** | Changes the currently selected target. |

*Note: Input mappings may depend on the project configuration.*

## Architecture & Development Practices

The project follows a component-oriented architecture designed to improve code organization, reusability, and maintainability.

Current development conventions include:

* **Actor Components:** Each gameplay system has its own responsibility and can be developed independently.
* **Blueprint Interfaces:** Systems communicate through interfaces instead of relying on direct references to project-specific classes.
* **Function-Based Organization:** Complex logic is divided into clearly named functions with limited responsibilities.
* **Pure Functions:** Functions responsible only for calculations use Pure functions whenever appropriate.
* **Readable Blueprints:** Numbered comments and color-coded comment boxes help explain execution flow.
* **Independent Testing:** Each system is tested before being integrated with other gameplay systems.
* **Git Version Control:** Development progress is organized into phases and committed as systems reach functional milestones.

## Planned Features & Development Roadmap

The project is being developed in phases. The following features represent planned work and should not be considered fully implemented.

| Phase | System | Planned Functionality |
| :--- | :--- | :--- |
| **Phase 3** | Ground Combat & Combos | Light and heavy attacks, animation montages, input buffering, and hit detection. |
| **Phase 4** | Impact Reactions | Enemy hit reactions, hitstop, camera shake, and knockback. |
| **Phase 5** | Lunge System | Movement toward the locked-on target during specific attacks. |
| **Phase 6** | Dodge System | Directional dodging and invincibility frames. |
| **Future** | Air Combat | Additional combat interactions and aerial mechanics. |

### Planned Combat Architecture

The combat system is intended to use a dedicated Actor Component to coordinate attack execution and combo states.

Planned elements include:

* **Attack Data Assets:** Store attack configuration, damage values, animation montages, combo transitions, and hit-detection settings.
* **Animation Montages:** Handle attack sequences.
* **Animation Notifies / Notify States:** Synchronize hit windows, combo input windows, and attack transitions.
* **Input Buffering:** Allow players to queue attacks during valid combo windows.
* **Hit Detection:** Use Line Traces or Sphere Traces during active attack windows.
* **Duplicate-Hit Prevention:** Track actors already hit during an individual attack.

The intended architecture separates attack configuration, execution logic, and animation timing to make future extensions easier to implement.

## Known Limitations

* The project is a technical prototype, not a finished commercial combat framework.
* The complete attack and combo system is still under development.
* Suitable attack and reaction animations must be integrated and validated.
* Some UI integration details remain subject to verification.
* Multiplayer replication is not documented as an implemented feature.

## Next Development Goals

The main objective is to continue expanding the kit while preserving its modular architecture.

Future development will prioritize:

* Reusable gameplay components.
* Clear separation of responsibilities.
* Interface-based communication.
* Data-driven attack configuration.
* Improved Blueprint readability.
* Better animation and gameplay synchronization.
* Technical documentation for each implemented system.

**The goal is to build a reusable and extensible combat foundation while maintaining clean, organized, and maintainable Blueprint architecture.**
