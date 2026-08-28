# linux-zinux

### The hardware compatibility layer of Zinux

linux-zinux is a Linux fork maintained as part of the Zinux project.

Its purpose is simple:

> **Do not throw away decades of working hardware support.**

Linux contains decades of practical knowledge about real hardware:
drivers, protocols, firmware, hardware quirks and workarounds.

Zinux intends to stand on those shoulders.

### Why?

Zinux explores a different model of hardware support:

> **Can local AI construct a hardware-specific driver when it is needed,
> instead of requiring every possible driver to be permanently maintained?**

That is an ambitious question.

Reimplementing decades of existing hardware support first would be
wasteful. linux-zinux therefore provides a bridge to the existing world.

```text
                    ZINUX
                      │
          ┌───────────┴───────────┐
          │                       │
   Existing hardware        New hardware
          │                       │
    linux-zinux drivers      AI-generated
                              Zig drivers
          │                       │
          └───────────┬───────────┘
                      │
                 Zinux system




## What is linux-zinux?

linux-zinux focuses on:

- existing Linux drivers
- hardware compatibility
- firmware and device support
- established driver interfaces
- hardware-specific workarounds

Code remains in whatever language is appropriate.

C is fine.  
Rust is fine.  
Assembly is fine.

This is **not** an attempt to rewrite Linux in Zig.

## Relationship with Zinux

The two repositories have different purposes.

### linux-zinux — the existing world

Provides access to proven hardware support and preserves accumulated
Linux driver knowledge.

### Zinux — the experiment

Primarily written in Zig and focused on:

- capability-based hardware access
- isolated drivers
- local AI
- Driver Plans
- validation
- sandboxing
- dynamic device support
- AI-generated hardware-specific logic

## Not a competition with Linux

Linux has already solved an enormous part of the hardware problem.

If an existing driver works, there is little reason to replace it.

The interesting question is what happens when a device has no suitable
driver, or maintaining one becomes unnecessarily expensive.

## Drivers as knowledge

Linux drivers contain more than code. They encode practical knowledge
about:

- register behavior
- timing
- interrupts
- DMA
- hardware quirks
- firmware
- failure recovery

linux-zinux may therefore also become a source of knowledge for future
AI-assisted driver synthesis.

A Linux driver is not automatically a formal specification.

**It is evidence.**

## Compatibility before reinvention

> **Use existing solutions when they are good enough. Reinvent them when
> there is a reason.**

The goal is coexistence, not replacement for its own sake.

Some drivers may remain permanently maintained.

Others may eventually be generated on demand.

Zinux does not need to decide that in advance.

## A bridge, not a destination

linux-zinux exists so Zinux can experiment with a new operating-system
model without discarding decades of engineering.

> **Stand on Linux’s shoulders. Build something different from there.**

## License

This repository is derived from Linux and retains the applicable Linux
licensing and attribution requirements.

See the repository’s license and individual source files for details.

Zinux-specific additions must include their applicable licensing and
copyright information.

## Zinux

Zinux is an experimental AI-native operating system project focused on
the future of dynamically constructed, capability-constrained hardware
interfaces.

