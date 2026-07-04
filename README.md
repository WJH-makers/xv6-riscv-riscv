<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2d3436,100:636e72&height=180&section=header&text=xv6-riscv&fontSize=60&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Unix%20V6%20%E9%87%8D%E5%AE%9E%E7%8E%B0%20%E2%80%93%20RISC-V%20%E5%A4%9A%E6%A0%B8%E7%89%88%E6%9C%AC&descAlignY=55&descAlign=50" width="100%" />
</p>

| 类别 | 技术栈 |
|------|--------|
| **语言** | ANSI C |
| **架构** | RISC-V (rv64) |
| **平台** | QEMU |
| **许可证** | MIT |

## 📋 简介

xv6 是 Unix V6 的 RISC-V 重实现，源自 MIT 6.1810。完整操作系统内核：进程管理、虚拟内存、文件系统、设备驱动、用户态工具，代码量 < 10K LoC。

## 🚀 快速开始

```bash
# 安装 RISC-V 交叉编译器
sudo apt-get install gcc-riscv64-linux-gnu

# 编译并运行
make
make qemu           # 单核
make qemu CPUS=2    # 双核
```

## ✨ 功能特性

- **进程管理**：fork/exec/wait/kill，时间片轮转调度，sleep/wakeup
- **虚拟内存**：Sv39 页表，写时复制，按需调页
- **文件系统**：日志型（journaling），崩溃恢复，缓存，inode
- **设备驱动**：UART 串口、Virtio 磁盘、PLIC 中断控制器
- **系统调用**：完整 Unix 接口（30+ 个）
- **用户程序**：Shell、ls、cat、grep、wc 等

## 🏗️ 项目结构

```
xv6-riscv/
├── kernel/                     # 内核源码
│   ├── main.c                 # 启动初始化
│   ├── proc.c                 # 进程管理与调度
│   ├── vm.c                   # 虚拟内存
│   ├── trap.c                 # 中断/异常处理
│   ├── syscall.c              # 系统调用分发
│   ├── fs.c                   # 文件系统
│   ├── bio.c / log.c          # 缓存与日志
│   ├── kalloc.c               # 物理页分配
│   ├── uart.c                 # UART 驱动
│   ├── virtio_disk.c          # Virtio 磁盘驱动
│   ├── plic.c                 # 中断控制器
│   └── spinlock.c             # 同步原语
├── user/                       # 用户程序
│   ├── sh.c                   # Shell
│   ├── cat.c, ls.c, grep.c    # 标准工具
│   └── usertests.c            # 用户态测试
├── mkfs/                       # 文件系统镜像工具
└── Makefile
```

## ❓ 常见问题

| 问题 | 回答 |
|------|------|
| **如何调试内核？** | QEMU 加 `-gdb tcp::26000`，用 riscv64-linux-gnu-gdb 连接 |
| **如何添加系统调用？** | 3 步：加编号 → 实现 → 添加用户态存根 |
| **能在真机上跑吗？** | QEMU 专用，适配 SiFive/Kendryte 板需修改驱动 |

## 🔗 相关项目

- [Pipeline CPU](/WJH-makers/project4) — 硬件层面的流水线处理器
- [File Management](/WJH-makers/FileManagementTool) — 用户态文件系统概念应用

## 🎓 课程背景

武汉大学计算机学院 · 操作系统课程（2024 春）。

### 参考

- [MIT 6.1810: Operating System Engineering](https://pdos.csail.mit.edu/6.828/)
- [xv6 Book (RISC-V)](https://pdos.csail.mit.edu/6.828/2022/xv6/book-riscv-rev3.pdf)

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:636e72,100:2d3436&height=100&section=footer" width="100%" />
</p>
