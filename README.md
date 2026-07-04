<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2d3436,100:636e72&height=180&section=header&text=xv6-riscv&fontSize=60&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Unix%20V6%20Re-implementation%20for%20RISC-V%20Multiprocessors&descAlignY=55&descAlign=50" width="100%" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Language-ANSI%20C-555555?style=flat-square&logo=c" />
  <img src="https://img.shields.io/badge/Architecture-RISC--V%20(rv64)-00A1E9?style=flat-square" />
  <img src="https://img.shields.io/badge/Platform-QEMU-FF6600?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" />
</p>

## 📋 Overview

xv6 is a modern re-implementation of **Unix V6** for **RISC-V multiprocessors**, written in ANSI C. Originally from MIT's 6.1810, this version was completed at **Wuhan University** (2024 Spring). It provides a complete, minimal OS kernel with process management, virtual memory, file systems, device drivers, and full user-space utilities.

> **Why xv6?** xv6 is the cleanest pedagogical kernel in existence — small enough to read in a semester (< 10K LoC) but complete enough to run real Unix programs. Building it from the ground up teaches every core OS abstraction: syscalls, scheduling, virtual memory, file systems, and drivers.

## 🚀 Quick Start

### Prerequisites

```bash
# Install RISC-V cross-compiler
sudo apt-get install gcc-riscv64-linux-gnu
```

### Build & Run

```bash
# Build the kernel and file system
make

# Run in QEMU (single-core)
make qemu

# Run with 2 cores
make qemu CPUS=2
```

### Inside xv6

```
$ ls
.              1 1 1024
..             1 1 1024
README         2 2 2270
cat            2 3 24968
$ cat README
xv6 is a re-implementation of Dennis Ritchie's and Ken Thompson's Unix
Version 6 (v6).
```

## ✨ Key Features

- **Process Management**: Fork/exec/wait/kill, round-robin scheduling, sleep/wakeup
- **Virtual Memory**: Sv39 page tables, COW, demand paging
- **File System**: Journaling (logging), crash recovery, buffer cache, inodes
- **Drivers**: UART console, Virtio disk, PLIC interrupt controller
- **System Calls**: Complete Unix syscall interface (30+ syscalls)
- **User Programs**: Shell, ls, cat, grep, wc, echo, mkdir, rm, and more

## 🏗️ Architecture

```
xv6-riscv/
├── kernel/                     # Kernel source
│   ├── main.c                  # Boot sequence & initialization
│   ├── proc.c / proc.h         # Process management & scheduling
│   ├── vm.c                    # Virtual memory (page tables)
│   ├── trap.c                  # Trap/interrupt handling
│   ├── syscall.c / syscall.h   # Syscall dispatch table
│   ├── sysfile.c / sysproc.c   # Syscall implementations
│   ├── fs.c / fs.h             # File system implementation
│   ├── bio.c / log.c           # Buffer cache & journaling
│   ├── kalloc.c                # Physical page allocator
│   ├── uart.c / console.c      # UART console driver
│   ├── virtio_disk.c           # Virtio block device driver
│   ├── plic.c                  # PLIC interrupt controller
│   ├── spinlock.c / sleeplock.c # Synchronization primitives
│   ├── entry.S / start.c       # Boot entry point
│   └── kernel.ld               # Linker script
├── user/                       # User-space programs
│   ├── sh.c                    # Shell (command interpreter)
│   ├── cat.c, echo.c, ls.c, grep.c, wc.c  # Standard utilities
│   ├── usertests.c             # User-mode test suite
│   ├── init.c / initcode.S     # Init process
│   └── ulib.c / umalloc.c      # User-mode C library
├── mkfs/                       # File system image builder
└── Makefile                    # Build system
```

## 🎓 Academic Context

This project was completed as part of the **Operating Systems** course (2024 Spring) at **Wuhan University**, School of Computer Science.

### References

- [MIT 6.1810: Operating System Engineering](https://pdos.csail.mit.edu/6.828/)
- [xv6 Book (RISC-V)](https://pdos.csail.mit.edu/6.828/2022/xv6/book-riscv-rev3.pdf)
- [RISC-V Specification](https://riscv.org/technical/specifications/)

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:636e72,100:2d3436&height=100&section=footer" width="100%" />
</p>
