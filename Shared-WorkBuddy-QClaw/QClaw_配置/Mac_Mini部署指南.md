# QClaw Mac Mini 安装配置指南

> 在 Mac Mini 上部署 QClaw 调度中心的完整步骤
> 创建：2026-06-20

---

## 第一步：确保 iCloud Drive 可用

```bash
# Mac Mini 终端执行，确认iCloud路径存在
ls ~/Library/Mobile\ Documents/com~apple~CloudDocs/

# 如果看到文件列表，说明iCloud已启用
```

如果未启用：
- 系统设置 → Apple ID → iCloud → 开启「iCloud Drive」
- 勾选「桌面与文稿文件夹」（可选，但推荐）

---

## 第二步：复制共享文件夹到 iCloud

### 方式A：从WorkBuddy这台机器推送（推荐）

在WorkBuddy（这台机器）上执行：
```bash
# 复制整个共享文件夹到iCloud
cp -r /Users/kk/WorkBuddy/2026-06-19-11-07-30/Shared-WorkBuddy-QClaw \
  ~/Library/Mobile\ Documents/com~apple~CloudDocs/Shared-WorkBuddy-QClaw
```

等待iCloud同步完成（Mac Mini上出现同样文件夹）

### 方式B：从Mac Mini拉取

在Mac Mini上执行：
```bash
# 等WorkBuddy端上传完成，Mac Mini自动同步iCloud后
ls ~/Library/Mobile\ Documents/com~apple~CloudDocs/Shared-WorkBuddy-QClaw/
```

---

## 第三步：在 QClaw 中设置工作区

在QClaw中打开共享文件夹作为工作区：
```
工作区路径：~/Library/Mobile Documents/com~apple~CloudDocs/Shared-WorkBuddy-QClaw/
```

QClaw启动后，加载 `QClaw_配置/QClaw_MEMORY.md` 作为项目记忆。

---

## 第四步：安装 Bark（手机端）

1. iPhone打开 App Store
2. 搜索「Bark」→ 安装
3. 打开Bark → 允许通知
4. 右上角「+」→ 复制推送测试链接
5. 粘贴到Mac Mini终端测试：
   ```bash
   curl "https://api.day.app/你复制的链接中的key部分/测试消息"
   ```
6. 手机收到推送 = 成功

**记录你的 Bark Key：** `____________________`

---

## 第五步：在 QClaw 创建自动化

在QClaw中创建3个自动化任务（具体配置见 `QClaw_配置/QClaw_自动化配置.md`）：

1. **每日简报** — 每天 9:00
2. **逾期检查** — 每2小时（9:00-21:00）
3. **素材进度** — 每天 18:00

---

## 第六步：验证系统互通

### 测试1：WorkBuddy写入 → QClaw读取
1. WorkBuddy修改统一工作日志，新增一条测试任务
2. 等待iCloud同步（通常10秒内）
3. 在Mac Mini上确认QClaw能读取到新任务

### 测试2：QClaw写入 → WorkBuddy读取
1. QClaw在统一工作日志中标记任务完成
2. 等待同步
3. WorkBuddy端确认能读到更新

### 测试3：Bark推送
1. QClaw执行一次测试推送
2. 确认三少手机收到通知

---

## 日常维护

### 每周检查
- iCloud同步是否正常（两边文件修改时间一致）
- Bark推送是否正常

### 每月
- 清理简报存档（保留最近30天）
- 更新月度计划和素材计划

### 故障排查

**iCloud不同步：**
```bash
killall bird
# 重启iCloud同步进程
```

**QClaw无法访问共享文件：**
```bash
# 检查iCloud Drive是否挂载
ls ~/Library/Mobile\ Documents/com~apple~CloudDocs/
```

**Bark不推送：**
- 检查Mac Mini网络连接
- 检查Bark App是否允许通知
- 测试API：`curl "https://api.day.app/{key}/test"`
