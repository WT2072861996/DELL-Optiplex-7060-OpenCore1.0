# 🖥️ DELL Optiplex 7060 · OpenCore Hackintosh

<p align="center">
  <img src="https://img.shields.io/badge/CPU-Intel_Core_i5_8500T-0071C5?logo=intel&logoColor=white" alt="CPU" />
  <img src="https://img.shields.io/badge/GPU-Intel_UHD_630-0071C5" alt="GPU" />
  <img src="https://img.shields.io/badge/RAM-16GB_DDR4-8B5CF6" alt="RAM" />
  <img src="https://img.shields.io/badge/Chipset-Q370-00A3E0" alt="Chipset" />
  <img src="https://img.shields.io/badge/Status-Working-success" alt="Status" />
</p>

<div align="center">
  <i>DELL Optiplex 7060 Micro 黑苹果 OpenCore EFI 配置方案。</i>
  <br>
  <b>Intel Core i5-8500T · UHD 630 · Q370 · OpenCore</b>
</div>

---

## 💻 硬件规格

| 项目 | 规格 |
|------|------|
| **型号** | DELL Optiplex 7060 Desktop |
| **CPU** | Intel Core i5-8500T |
| **内存** | 16 GB（Kingston DDR4 2666MHz 8GB + Micron DDR4 2400MHz 4GB × 2）|
| **显卡** | Intel UHD Graphics 630 (128 MB) |
| **主板** | Dell 0NC2VH (Q370 芯片组) |
| **硬盘** | WD BLACK SN770 500GB NVMe |
| **网卡** | Intel Ethernet I219-LM |
| **声卡** | Intel HD Audio (ALC255) |

---

## ⚙️ BIOS 设置

| 选项 | 设置 |
|------|:----:|
| SATA Operation | AHCI |
| Secure Boot | 🔴 关闭 |
| Intel SGX | 🔴 关闭 |

---

## 🔧 DVMT 修改（关键步骤）

显卡驱动需要使用 modGRUBShell 修改以下参数：

```
setup_var 0x8DC 0x02    # 修改 DVMT 为 64MB
setup_var 0x5BE 0x00    # 关闭 CFG Lock
```

> modGRUBShell 已包含在本 EFI 启动项中，无需额外下载。

---

## ✅ 驱动情况

| 功能 | 状态 |
|:----:|:----:|
| 声卡 | ✅ |
| 网卡 | ✅ |
| 核显 | ✅ |
| DisplayPort 输出 | ✅ |
| 3.5mm 耳机接口 | ✅ |
| 睡眠 / 唤醒 | ✅ |

---

## 📦 使用说明

1. 按 BIOS 设置表调整主板设置
2. 使用 modGRUBShell 修改 DVMT
3. 将 EFI 复制到 U 盘 EFI 分区
4. U 盘启动安装 macOS
5. 安装完成后将 EFI 复制到系统盘

---

<div align="center">
  <img src="https://img.shields.io/badge/Built_with_❤️_for_the_Hackintosh_Community-FF6B6B" alt="Built with love">
</div>
