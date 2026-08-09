 # ⚔️ Perseus

> *An experimental operating system built from scratch, starting with a 16-bit x86 bootloader and kernel written in NASM.*

[![status: idea](https://img.shields.io/badge/status-idea-red)](https://github.com/HighwayToHell-git/Perseus)
[![version -1.0](https://img.shields.io/badge/version--1.0-blue)](https://github.com/HighwayToHell-git/Perseus)
[![architecture x86](https://img.shields.io/badge/architecture-x86-lightgrey)](https://github.com/HighwayToHell-git/Perseus)
[![assembly NASM](https://img.shields.io/badge/assembly-NASM-orange)](https://github.com/HighwayToHell-git/Perseus)
[![license Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-green)](https://github.com/HighwayToHell-git/Perseus/blob/main/LICENSE)

---

## 📖 About

**Perseus** is an experimental operating system created as a hobby project, a way to improve low-level programming skills, and a long-term portfolio project.

The project starts with a **16-bit x86 bootloader** and **kernel** written in **NASM**.  
The long-term goal is to evolve Perseus from a tiny experimental kernel into a fully usable user‑oriented operating system, eventually supporting 32‑bit and 64‑bit x86.

> ⚠️ **Project status:** Perseus is currently at the *idea/concept* stage. No functional kernel or bootloader has been implemented yet.

---

## 🎯 Goals

The main goals of Perseus are:

- Learn how computers boot and operate at a low level
- Build a bootloader from scratch
- Build a kernel from scratch
- Work directly with memory and hardware
- Develop a custom driver system
- Implement disk and filesystem support
- Build a simple shell
- Run user programs
- Eventually create a complete user‑oriented operating system

> *Perseus is primarily a hobby, learning, and portfolio project.*

---

## 🚧 Current Status

- **Version:** `-1`
- **Status:** `Idea / Concept`

Currently, Perseus exists mainly as a concept and development plan.

### MVP

The first major milestone is a system that can:

- Boot on real hardware
- Run in 32‑bit mode
- Provide a basic shell
- Access a filesystem
- Support FAT32 or EXT4
- Provide an interface for custom drivers
- Run basic user programs

> 💡 **The main idea is simple:**  
> *«Perseus should eventually run on real hardware, not only inside a virtual machine.»*  
> Virtualization and emulation tools such as QEMU will be used during development and testing.

---

## 🧠 Architecture

Development starts with **16‑bit x86**. The planned evolution is:
