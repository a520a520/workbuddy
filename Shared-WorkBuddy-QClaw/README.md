# WorkBuddy + QClaw 双系统工作枢纽

> 创建日期：2026-06-20 | 最后更新：2026-06-20（改用腾讯文档）
> 维护者：三少

---

## 系统定位

| 系统 | 角色 | 运行位置 | 核心职责 |
|------|------|----------|----------|
| **WorkBuddy** | 🧠 主力大脑 | MacBook（随身） | 内容创作、方案策划、数据分析、决策执行 |
| **QClaw** | 📋 调度中心 | Mac Mini（家里） | 任务追踪、日程提醒、外出记录、进度跟进 |

## 工作原理

```
三少外出 → QClaw → 更新腾讯文档
                          ↓
三少回家 → WorkBuddy → 读取腾讯文档 → 知悉最新状态
                          ↓
WorkBuddy完成工作 → 更新腾讯文档 → QClaw感知进度
```

## 共享方式：腾讯文档

不使用 iCloud 同步。两个系统通过**腾讯文档**共享数据：

### 📋 统一工作日志（腾讯文档）
- **文档ID：** `HIxUZUSFNJsj`
- **链接：** https://docs.qq.com/doc/DSEl4VVpVU0ZOSnNq?_fid=HIxUZUSFNJsj
- **用途：** 所有任务的唯一记录，QClaw 外出记录也写在此
- **规则：**
  - WorkBuddy 负责写入任务和更新状态
  - QClaw 负责追踪进度、记录外出情况
  - 素材计划确定的具体工作 → 放进此文档

### 📊 月度素材制作计划（腾讯文档）
- **文档ID：** `HStWoBTkKDVK`
- **链接：** https://docs.qq.com/doc/DSFN0V29CVGtLRFZL?_fid=HStWoBTkKDVK
- **用途：** 每月新媒体素材制作计划和进度追踪
- **规则：**
  - WorkBuddy 制定计划、更新完成状态
  - QClaw 每日读取、追踪进度、推送提醒
  - 每月新建一个文档

### ⚖️ 账号运营原则
- 存储在 WorkBuddy 本地，QClaw 加载为记忆
- 内容制作前两个系统都必须对照

---

## QClaw 配置要点

在 QClaw 中：
1. 加载 `QClaw_配置/QClaw_MEMORY.md` 作为项目记忆
2. 通过腾讯文档接口读取两个文档
3. 设置定时任务：每日检查任务进度
4. 安装 Bark App 推送提醒到三少手机
