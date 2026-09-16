# 充电加速（内置 WebUI 控制面板）· 二改版

在原版 [turbo-charge v68](https://github.com/chase535/turbo-charge)（酷安 @诺鸡鸭）基础上内置了 WebUI 控制面板，由 **Yxlan-yu** 二改整合。

> 原版模块功能：删除温控，关闭阶梯式充电，持续修改电池温度及充电电流，尽可能让手机满血快充。

## 二改新增内容（WebUI 控制面板）

- **实时充电状态**：当前电量、电压、电流、功率、温度、充电类型、PD 协商档位，无需再敲命令。
- **图形化配置编辑**：直接在页面上修改 option.txt 的 13 个参数，无需手机 Root 管理器找文件。
- **一键回滚配置**：修改前自动备份，可随时还原上次配置。
- **实时日志**：页面内查看 turbo-charge 运行日志。
- **白色主题**，中文状态显示（充电中 / 放电中 / 已充满 / 未充电）。

## 打开方式

安装模块后，手机和电脑（同一局域网）均可访问：

```
http://手机IP:8080
```

或直接打开 KernelSU / Magisk 管理器 → 本模块详情 → 模块 WebUI 入口。

> 所有设备信息均在本机处理，不做任何上传。

## 安装方法

- **KernelSU / KernelSU-Next / Magisk**：管理器内直接安装本 zip 即可。
- 升级自原版：原模块 id 保持一致（`turbo-charge`），直接覆盖安装即可，原配置文件自动保留读取。
- 卸载：在管理器里卸载模块即可，配置目录 `/data/adb/turbo-charge` 会一并清理。

## 配置说明

配置文件：`/data/adb/turbo-charge/option.txt`（WebUI 面板内也可编辑）。

| 参数 | 默认值 | 说明 |
|---|---|---|
| CYCLE_TIME | 1 | 主循环间隔（秒） |
| FORCE_TEMP | 1 | 是否写入电池温度伪装（1 开 0 关） |
| CURRENT_MAX | 50000000 | 最大充电电流 (µA) |
| STEP_CHARGING_DISABLED | 0 | 是否关闭阶梯式充电（1 关 0 开） |
| TEMP_CTRL | 1 | 是否启用高温电流限制（1 开 0 关） |
| POWER_CTRL | 0 | 是否启用断电/恢复充电控制（1 开 0 关） |
| STEP_CHARGING_DISABLED_THRESHOLD | 15 | 阶梯充电关闭阈值（电量百分比） |
| CHARGE_STOP | 95 | 断电电量百分比（需 POWER_CTRL=1） |
| CHARGE_START | 80 | 恢复充电电量百分比（需 POWER_CTRL=1） |
| TEMP_MAX | 52 | 高温限制温度（℃） |
| HIGHEST_TEMP_CURRENT | 2000000 | 高温时允许的充电电流 (µA) |
| RECHARGE_TEMP | 45 | 高温限制解除温度（℃） |
| BYPASS_CHARGE | 0 | 伪旁路充电（1 开 0 关，电流降至 500mA） |

> 警告：本模块删除温控并持续拉高充电电流，**手机体感温度过高时请立即拔下充电器并静置在阴凉处**。

## 与原版差异

1. 内置 WebUI 控制面板（状态 / 配置 / 日志 / 回滚）。
2. busybox 自动探测，兼容 KernelSU / KernelSU-Next / Magisk / 系统 busybox，无需额外安装。
3. 版本号 `v68-1`，与原版 `v68` 区分。
4. 原版所有功能与配置格式保持不变，老用户升级无感。

## 开源协议

本二改版遵循原项目的 **AGPLv3** 开源协议。
原版作者：诺鸡鸭（酷安 [@诺鸡鸭](https://www.coolapk.com/u/1145497)）· [GitHub](https://github.com/chase535/turbo-charge)