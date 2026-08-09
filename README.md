<div align="center">

# ⚔️ Perseus

### An experimental operating system built from scratch.

Starting with a 16-bit x86 bootloader and kernel written in NASM.

<br>

<img src="https://img.shields.io/badge/Status-Idea-red">
<img src="https://img.shields.io/badge/Version-0.0.0-blue">
<img src="https://img.shields.io/badge/Architecture-x86-lightgrey">
<img src="https://img.shields.io/badge/Assembly-NASM-orange">
<img src="https://img.shields.io/badge/License-Apache--2.0-green">

<br><br>

**From bootloader to user OS.**

*Built from scratch. One instruction at a time.*

</div>

---

## 📖 About

**Perseus** is an experimental operating system created as a hobby project, a way to improve low-level programming skills, and a long-term portfolio project.

The project starts with a **16-bit x86 bootloader and kernel written in NASM**.

The long-term goal is to evolve Perseus from a small experimental kernel into a **full user-oriented operating system**, eventually supporting 32-bit and 64-bit x86.

> ⚠️ **Current status:** Perseus is currently at the idea/concept stage. No functional kernel or bootloader has been implemented yet.

---

## 🎯 Goals

<table>
<tr>
<td width="50%">

### Low-level

- Learn x86 architecture
- Build a bootloader
- Build a kernel from scratch
- Work directly with memory
- Work with hardware
- Learn interrupts and I/O

</td>
<td width="50%">

### Operating System

- Filesystem support
- Driver system
- Shell
- User programs
- Hardware support
- Eventually a complete user OS

</td>
</tr>
</table>

---

## 🧠 Architecture

Development starts with **16-bit x86**.

<div align="center">

```text
┌──────────────┐
│   16-bit     │
│     x86      │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   32-bit     │
│     x86      │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   64-bit     │
│     x86      │
└──────────────┘