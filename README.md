# VSL — Väinö Subsystem for Linux

## Linux as a plugin. Not Linux as the operating system.

VSL is the Linux compatibility environment for [VÄINÖ](https://github.com/Mikko-Huuskonen-Pro/V-in-/blob/main)

VSL is inspired by the idea behind WSL2: provide a complete Linux environment that integrates with another operating system and makes the Linux command-line ecosystem available to users.

But VSL takes the concept in a different direction:

Everything in Väinö is a plugin.

Linux is not the core of Väinö.

Linux is one environment Väinö can run.

---

## Architecture

```
                         VÄINÖ
                           │
                  ┌────────┴────────┐
                  │                 │
              Väinö Core       Plugin Runtime
                  │                 │
                  ├─────────────────┤
                  │
                  ▼
                 VSL
                  │
                  ▼
          Linux environment
                  │
        ┌─────────┼─────────┐
        │         │         │
      shell      git      Python
      ssh       tools    compilers
```

VSL provides access to the existing Linux ecosystem without making Linux itself the definition of Väinö.

---

## Snapshot & Recovery

VSL is designed to be a recoverable plugin.

Väinö can create snapshots of a plugin’s state before potentially destructive operations.

```
AI / User
    │
    ▼
 Request change
    │
    ▼
Väinö policy
    │
    ▼
  SNAPSHOT
    │
    ▼
    VSL
    │
    ▼
Linux environment
    │
    ├── success ──────► commit
    │
    └── crash/failure
             │
             ▼
          rollback
             │
             ▼
       known-good state
```

The snapshot mechanism belongs to Väinö Core, not to Linux.

This allows Väinö to treat complex environments such as VSL as isolated, recoverable components.

The long-term goal is to make plugin operations transactional:

**Experiment → Validate → Commit or Rollback**

This becomes especially important when AI-generated code or drivers are involved.

---

## Why Linux?

Linux represents more than 35 years of development, hardware support, drivers, tooling, and software.

Väinö does not need to reproduce all of that work.

Instead, VSL provides a bridge to the existing world:

- Linux command-line tools
- Development environments
- Compilers and interpreters
- Networking tools
- System utilities
- Existing Linux applications
- Decades of Linux hardware support

The goal is not to replace Linux.

The goal is to make Linux one useful component inside a different operating-system architecture.

---

## Native Väinö and VSL

VSL can coexist with native Väinö implementations.

**Native Väinö**
```
Hardware
   ↓
Väinö
   ↓
Native driver
   ↓
Väinö capabilities
```

**VSL**
```
Hardware
   ↓
Väinö
   ↓
VSL
   ↓
Linux
   ↓
Linux driver
```

A device could initially be supported through Linux and later receive a native Väinö driver.

This allows Väinö to experiment with new driver architectures without abandoning existing hardware support.

---

## AI-Native Architecture

Väinö is exploring an operating system where AI can help create drivers and system functionality.

The AI does not receive unrestricted access to the system.

Instead:
```
AI
 │
 ▼
Plan
 │
 ▼
Väinö Policy
 │
 ▼
Capabilities
 │
 ▼
Plugin
 │
 ▼
Validate
 │
 ├── PASS → Commit
 │
 └── FAIL → Rollback
```

VSL provides a practical and familiar environment while this architecture develops.

Snapshot and recovery are therefore not merely convenience features.

They are part of the trust model:

**The AI may experiment, but Väinö remains in control.**

---

### VSL Is

- A Väinö plugin
- A Linux compatibility environment
- A command-line environment
- A bridge to the existing Linux ecosystem
- An isolated and recoverable environment
- A foundation for experimenting with Väinö’s AI-native architecture

### VSL Is Not

- The Väinö kernel
- The Väinö operating system itself
- A Linux distribution renamed as Väinö
- A replacement for native Väinö drivers
- Unrestricted access to the Väinö host

---

## Relationship to Linux

VSL should remain as close to upstream Linux as practical.

The project should:

1. Reuse upstream Linux work.
2. Minimize unnecessary modifications.
3. Keep Väinö-specific integration isolated.
4. Keep Linux complexity outside the Väinö core.
5. Use Linux as a compatibility layer rather than making it the foundation of Väinö.

**Väinö owns the architecture.**
**VSL integrates Linux into it.**

---
## Long-Term Vision

VSL is one part of the larger Väinö experiment.

```
                         VÄINÖ
                           │
             ┌─────────────┴─────────────┐
             │                           │
        Existing world              New world
             │                           │
            VSL                    Native Väinö
             │                           │
           Linux                 AI-generated
         ecosystem                  drivers
             │                           │
             └─────────────┬─────────────┘
                           │
                    Väinö capabilities
                           │
                    Snapshot / Recovery
```

The goal is not to build another Linux distribution.

The goal is to explore an operating system where functionality is modular, isolated, capability-controlled, AI-assisted, and recoverable.

Linux gives Väinö access to the world that already exists.
Väinö provides a framework for exploring what comes next.

---
## Status

VSL is an experimental component of the Väinö project.

The interfaces, isolation model, snapshot mechanism, and Linux integration will evolve together with the Väinö core.

**Everything is a plugin.**
**VSL is Linux as a plugin.**
