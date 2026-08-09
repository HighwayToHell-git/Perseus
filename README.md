⚔️ Perseus

«An experimental operating system built from scratch, starting with a 16-bit x86 bootloader and kernel written in NASM.»

"Status" (https://img.shields.io/badge/status-idea-red)
"Version" (https://img.shields.io/badge/version--1.0-blue)
"Architecture" (https://img.shields.io/badge/architecture-x86-lightgrey)
"Assembly" (https://img.shields.io/badge/assembly-NASM-orange)
"License" (https://img.shields.io/badge/license-Apache--2.0-green)

---

📖 About

Perseus is an experimental operating system created as a hobby project, a way to improve low-level programming skills, and a long-term portfolio project.

The project starts with a 16-bit x86 bootloader and kernel written in NASM.

The long-term goal is to evolve Perseus from a tiny experimental kernel into a fully usable user-oriented operating system, eventually supporting 32-bit and 64-bit x86.

«⚠️ Project status: Perseus is currently at the idea/concept stage. No functional kernel or bootloader has been implemented yet.»

---

🎯 Goals

The main goals of Perseus are:

- Learn how computers boot and operate at a low level
- Build a bootloader from scratch
- Build a kernel from scratch
- Work directly with memory and hardware
- Develop a custom driver system
- Implement disk and filesystem support
- Build a simple shell
- Run user programs
- Eventually create a complete user-oriented operating system

Perseus is primarily a hobby, learning, and portfolio project.

---

🚧 Current Status

Version: "-1"
Status: "Idea / Concept"

Currently, Perseus exists mainly as a concept and development plan.

MVP

The first major milestone is a system that can:

- Boot on real hardware
- Run in 32-bit mode
- Provide a basic shell
- Access a filesystem
- Support FAT32 or EXT4
- Provide an interface for custom drivers
- Run basic user programs

The main idea is simple:

«Perseus should eventually run on real hardware, not only inside a virtual machine.»

Virtualization and emulation tools such as QEMU will be used during development and testing.

---

🧠 Architecture

Development starts with 16-bit x86.

The planned evolution is:

16-bit x86
    │
    ▼
32-bit x86
    │
    ▼
64-bit x86

NASM Assembly will be the primary language during the early stages.

At a later stage, especially around the 32-bit LTS release, C may be introduced for parts of the kernel.

---

🛠️ Technology

Current planned technology stack:

- NASM — bootloader and kernel
- C — possible future kernel components
- x86 — target architecture
- QEMU — development and testing

No external libraries are currently planned.

---

💿 Boot & Installation

Release builds are planned to be distributed as ".iso" images.

The expected workflow:

1. Download the latest Perseus ISO
2. Write it to a USB drive
3. Boot a computer from the USB drive
4. Start Perseus

The future installation process may look something like:

Perseus OS

perseus> Perseus-install

Installing Perseus...
[████████████████████] 100%

Installation complete.

perseus> _

«"Perseus-install" is currently only a concept and is not implemented.»

---

🖥️ User Interface

The early versions of Perseus will use a text-based shell.

Example:

Perseus OS
Copyright ...

perseus> _

The long-term goal is to move beyond a simple shell and provide a complete environment for users.

---

🗂️ Filesystem

Planned filesystem support includes:

- FAT32
- EXT4

The exact implementation order has not yet been decided.

---

🔌 Drivers

A major goal of Perseus is to provide an environment where developers can create their own drivers.

The long-term idea is to make hardware support modular rather than tightly coupled to the entire kernel.

---

🗺️ Roadmap

There is no fixed roadmap yet. The current development direction looks approximately like this:

[ ] 16-bit bootloader
[ ] Kernel loading
[ ] 16-bit kernel
[ ] Basic memory management
[ ] Basic I/O
[ ] Enter protected mode
[ ] 32-bit kernel
[ ] Shell
[ ] Disk access
[ ] Filesystem support
[ ] FAT32 / EXT4
[ ] Driver system
[ ] User programs
[ ] C integration
[ ] 32-bit LTS
[ ] 64-bit support
[ ] Full user-oriented OS

The roadmap will change as development progresses.

---

📦 Releases

Official builds are planned to be distributed as ".iso" images through the project's GitHub repository.

Development builds may be unstable and should only be used for testing.

---

🤝 Contributing

Perseus is intended to be an open-source project.

Contribution guidelines will be added once the project reaches a stage where external contributions become practical.

Future documentation may include:

- Contribution guidelines
- Source tree structure
- Coding style
- Pull request requirements
- Driver development documentation
- Kernel development documentation

---

📜 License

Perseus is licensed under the Apache License 2.0.

You are free to:

- Use the project privately
- Use it commercially
- Modify the source code
- Redistribute the original or modified version
- Create derivative works
- Use the code in proprietary projects

When redistributing the project, you must:

- Include a copy of the Apache License 2.0
- Preserve applicable copyright notices
- Clearly indicate modified files
- Follow the terms of the license

The software is provided without warranty.

The complete license text is available in:

LICENSE

---

👤 Author

HighwayToHell-git

Daniil

💬 Telegram: "@daniil_21_36" (https://t.me/daniil_21_36)

---

✍️ README

This README was initially written by ChatGPT based on the project's description and development plans provided by the author.

---

⚠️ Disclaimer

Perseus is an experimental operating system project.

Early versions are not intended for production use or for storing important data.

When experimenting with bootloaders, kernels, disks, and filesystems, use a virtual machine or dedicated test hardware.

---

<div align="center">⚔️ Perseus

From bootloader to user OS.

Built from scratch. One instruction at a time.

</div>