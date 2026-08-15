# FakeLocation

Fake Location（定位模拟）LSPosed 模块公开仓库。

这个仓库主要用于收集用户 issue 与公测反馈。模块本体发布在 Xposed 仓库。

## 反馈入口

- Xposed 仓库 / 最新版本：<https://github.com/Xposed-Modules-Repo/com.yinshibai.location>
- 提交问题或建议：<https://github.com/Mai-xiyu/FakeLocation/issues/new/choose>
- 公测反馈清单：<https://github.com/Mai-xiyu/FakeLocation/blob/main/PUBLIC_TEST_CHECKLIST.md>

## 它能做什么

- **定位模拟**：把手机位置固定到任意坐标，或沿自定义路线移动
- **路线模拟**：规划路径行走/跑步，支持实时调速、步频调节、GPS 抖动
- **基站 / WiFi 模拟**：伪造基站与 WiFi 信息
- **运动传感器**：伪造步数、步频、加速度计等运动数据
- **黑名单**：对指定 App 放行真实数据

## 使用要求

- Android 设备已获取 root 权限（推荐 KernelSU）
- 已安装 LSPosed（libxposed API 102+）
- 目前仅在 HyperOS 3 测试

## 提 issue 前建议准备的信息

- FakeLocation 版本
- 目标 App 名称与版本（如果只在某个 App 失效）
- Android 版本、机型、root 方案、LSPosed 版本
- 模拟模式（点模拟 / 路线模拟）和复现步骤
- 复现后的日志、截图或录屏

建议在复现后导出日志：

```powershell
adb logcat -d -s FakeLocation:D Location:D *:S
```

如果问题和定位、路线或某个 App 有关，尽量同时说明：

- 模拟模式：点模拟、路线模拟
- 是否同时开启基站 / WiFi / 运动传感器模拟
- 失效的目标 App，以及是否已加入黑名单
- 是否稳定复现，以及大概复现概率

## 公测重点

当前更建议优先反馈这些回归风险较高的项目：

- 点模拟固定坐标后，目标 App 读到的位置是否正确
- 路线模拟行走/跑步、实时调速、步频、GPS 抖动
- 基站 / WiFi 模拟是否被目标 App 采信
- 运动传感器（步数、加速度）是否同步变化
- 黑名单 App 是否仍能读到真实位置
- HyperOS 3 / 不同机型与 LSPosed 兼容性

详细清单见 <https://github.com/Mai-xiyu/FakeLocation/blob/main/PUBLIC_TEST_CHECKLIST.md>。

## 免责声明

本模块仅供学习研究使用，请勿用于任何违法违规用途。
