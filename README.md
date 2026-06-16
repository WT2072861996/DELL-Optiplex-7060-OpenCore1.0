# 🖥️ DELL Optiplex 7060 Hackintosh OpenCore EFI

**Intel Core i5-8500T · UHD 630 · Q370 芯片组 · macOS Sequoia · OpenCore 1.0.4**

<div align="center">

![CPU](https://img.shields.io/badge/CPU-i5_8500T_8C-0071C5?style=flat-square)
![GPU](https://img.shields.io/badge/GPU-UHD_630-0071C5?style=flat-square)
![RAM](https://img.shields.io/badge/RAM-16_GB_DDR4-8B5CF6?style=flat-square)
![Chipset](https://img.shields.io/badge/Chipset-Q370-00A3E0?style=flat-square)
![OpenCore](https://img.shields.io/badge/OpenCore-1.0.4-9cf?style=flat-square)
![Status](https://img.shields.io/badge/Status-Working_✓-brightgreen?style=flat-square)

**[📋 硬件清单](#硬件配置) · [⚙️ BIOS 设置](#bios-设置) · [✅ 驱动状态](#驱动状态) · [🚀 快速开始](#快速开始) · [🔧 故障排除](#故障排除)**

</div>

---

## 🖥️ 硬件配置

| 组件 | 型号 | 规格 |
|:-----|:-----|:-----|
| **主板** | DELL Optiplex 7060 | Q370 Chipset |
| **CPU** | Intel Core i5-8500T | 6C/6T @ 2.1-3.5 GHz |
| **GPU** | Intel UHD Graphics 630 | 128 MB Shared Memory |
| **RAM** | Kingston + Micron DDR4 | 16 GB @ 2666/2400 MHz |
| **存储** | WD BLACK SN770 | 500 GB NVMe SSD |
| **网卡** | Intel I219-LM | 1 Gbps |
| **声卡** | Realtek ALC255 | 高保真音频 |
| **显示** | 内置接口 | DisplayPort / VGA |

---

## ✅ 驱动状态（完全工作）

| 功能 | 状态 | 功能 | 状态 |
|:-----|:---:|:-----|:---:|
| **核显** | ✅ | **GPU 加速** | ✅ |
| **声卡** | ✅ | **音频输出** | ✅ |
| **有线网卡** | ✅ | **网络连接** | ✅ |
| **DisplayPort** | ✅ | **视频输出** | ✅ |
| **USB 2.0/3.0** | ✅ | **设备识别** | ✅ |
| **睡眠/唤醒** | ✅ | **电源管理** | ✅ |
| **NVRAM** | ✅ | **启动参数** | ✅ |

---

## ⚙️ BIOS 设置

| 设置 | 值 | 说明 |
|:-----|:---:|:-----|
| **SATA Operation** | AHCI | SSD 最优性能 |
| **Secure Boot** | Disabled | macOS 不支持 |
| **Intel SGX** | Disabled | 可能导致问题 |

### 🔧 DVMT 修改（必需）

使用 modGRUBShell 修改 BIOS NVRAM：

```bash
# 步骤 1：进入 modGRUBShell
# OpenCore 菜单 → Tools → modGRUBShell

# 步骤 2：修改 DVMT 为 64 MB
setup_var 0x8DC 0x02

# 步骤 3：禁用 CFG Lock
setup_var 0x5BE 0x00

# 步骤 4：退出并重启
exit
```

---

## 🛠️ EFI 配置

### Kexts 清单

```
EFI/OC/Kexts/
├── Lilu.kext              ✅ 内核补丁框架
├── VirtualSMC.kext        ✅ SMC 模拟
├── WhateverGreen.kext     ✅ GPU 修复
├── AppleALC.kext          ✅ 声卡驱动
├── IntelMausiEthernet.kext ✅ 网卡驱动
├── SMCProcessor.kext      ⚠️ CPU 传感器
├── SMCSuperIO.kext        ⚠️ 风扇/温度
├── USBToolBox.kext        ✅ USB 工具
├── UTBMap.kext            ✅ USB 映射
└── XHCI-unsupported.kext  ✅ XHCI 兼容
```

### SSDT 热补丁

```
EFI/OC/ACPI/
├── SSDT-EC.aml          ✅ EC 修复
├── SSDT-PLUG.aml        ✅ CPU 电源管理
├── SSDT-PMC.aml         ✅ NVRAM 补丁
├── SSDT-MCHC.aml        ✅ MCHC 仿冒
├── SSDT-SBUS.aml        ✅ SMBus 支持
├── SSDT-HPET.aml        ✅ HPET IRQ 修复
├── SSDT-RTCAWAC.aml     ✅ RTC 兼容性
└── [其他定制 SSDT...]    ✅
```

---

## 🚀 快速开始

### 1️⃣ BIOS 配置

1. 重启进入 BIOS（DEL 键）
2. 找到对应设置并按上述表格配置
3. 保存退出

### 2️⃣ DVMT 修改

1. 制作 OpenCore USB 安装盘
2. 启动到 OpenCore 菜单
3. 按 Space 显示工具
4. 进入 modGRUBShell 执行命令

### 3️⃣ EFI 部署

```bash
# 挂载 EFI 分区
mount -t msdos /dev/disk0s1 /mnt/efi

# 复制 EFI
cp -R EFI /mnt/efi/

# 生成三码（重要！）
# 使用 GenSMBIOS 或 OCAT
```

### 4️⃣ 重启安装

1. 从 USB 启动
2. 选择「Install macOS」
3. 按提示完成安装（2-3 次重启）
4. 最后将 EFI 复制到硬盘

---

## 📊 性能验证

### ✅ 应该看到

- ✅ CPU 频率动态变化（空闲 800 MHz → 满载 3.5 GHz）
- ✅ GPU 硬件加速正常
- ✅ 系统响应流畅
- ✅ 睡眠/唤醒稳定

### 🔍 检验命令

```bash
# 查看 CPU 频率
watch "sysctl -n hw.cpufrequency_current"

# 验证 GPU
ioreg -l | grep -i "gpu"

# 检查 Kext 加载
kextstat | grep -E "Lilu|WhateverGreen|VirtualSMC"
```

---

## 🆘 故障排除

### 问题 1：启动卡顿或黑屏

**原因**：DVMT 未正确修改或显卡配置错误

**解决**：
1. 重新执行 DVMT 修改
2. 尝试调整 `framebuffer-stolenmem` 值
3. 检查 WhateverGreen 参数

### 问题 2：无法识别 USB 设备

**原因**：USB 端口未映射

**解决**：
1. 使用 Hackintool 或 USBToolBox 创建映射
2. 生成 UTBMap.kext
3. 放入 EFI/OC/Kexts 并重启

### 问题 3：声卡无声

**原因**：Layout ID 不匹配或 AppleALC 未启用

**解决**：
1. 尝试其他 Layout ID（如 11, 12, 66）
2. 在 config.plist 中修改 `alcid=`
3. 重启测试

---

## 📋 检查清单

在生成三码和启动前，确认：

- [ ] BIOS 已按要求配置
- [ ] DVMT 已修改为 64 MB
- [ ] CFG Lock 已禁用
- [ ] EFI 文件夹结构完整
- [ ] config.plist 已修改三码
- [ ] 所有 Kexts 权限正确（755）
- [ ] USB 启动盘已测试

---

## 🎯 支持的 macOS 版本

| 版本 | 支持度 |
|:-----|:-----:|
| macOS Sequoia | ✅ |
| macOS Sonoma | ✅ |
| macOS Ventura | ✅ |
| macOS Monterey | ✅ |

---

## 📄 许可证

MIT License - 仅供学习和研究

> ⚠️ 在非 Apple 硬件上安装 macOS 可能违反 EULA

---

<p align="center">
  <b>为 Hackintosh 社区贡献 ❤️</b><br/>
  <sub>DELL Optiplex 7060 · OpenCore 1.0.4 · 2026年</sub>
</p>
