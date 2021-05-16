# Virtual Machines Ch2</br> Emulation: Interpretation and Binary Translation

## Overview + Jargon
**Goal of this chapter**: Understand mechanism of **instructions emulation**, the process on which virtual machines are based.

- _Emulation_: the process of implementing interfaces and functionality for one system with different interfaces and functionality.
  - [Terminal emulator](https://en.wikipedia.org/wiki/Terminal_emulator) provide interfaces and functionality for terminal.
  - [Game Boy emulator](https://emulation.gametechwiki.com/index.php/Game_Boy/Game_Boy_Color_emulators) provide interfaces and functionality for Game Boy on different hadware(e.g., PC, Smartphone).
  - Virtual Machine provide interfaces and functionality for _guest_ system.
  - **Instruction set emulator** provide interfaces and functionality for _guest's_ ISA.

- ISA (Instruction Set Architecture): interface between software and hardware
  - define
    - instructions
    - register and memory architecture
    - trap and interrupt architecture

- **Instruction set emulation**
  - emulate _guest's (source)_ ISA using _host's (target)_ ISA.
  - consist of
    - **user-level instructions emulation** (Chapter 2)
    - memory architecture, traps and interrupts emulation (Chapter 3, 4)

![](https://g.gravizo.com/svg?
  digraph {
    node [shape = box]
    guest [label = "Guest\nSource ISA"]
    host  [label = "Host\nTarget ISA"]
    guest -> host [label = "emulated by"]
  }
)

- Methods of instruction set emulation
  - _Interpretation_
    - repeat the following:
      1. fetch a source instruction
      2. analyze it
      3. perform the required operation
    - Pros: smaller initial cost
    - Cons: bigger execution cost
  - _Binary translation_
    - translate a source instructions block into a target instructions block
    - save it for repeated use
    - Pros: smaller execution cost
    - Cons: bigger initial cost
  
