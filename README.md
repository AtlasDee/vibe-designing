# vibe designing skill

> 一套**产品文档整理技能**（Claude / Claude Code Skills）：给一份业务需求或原始诉求，自动**分析需求 → 拆解抽象成产品方案 → 整理成结构规范的 PRD**。

把后台管理类产品文档反复出现的写法——摘要、背景期望、产品方案、名词解释、流程架构图、需求功能清单，以及每个功能模块的**搜索/编辑/列表字段表、功能说明表、状态-操作矩阵、交互原型图**——沉淀为可复用的技能，对需求做结构化整理与质检。

---

## ✨ 能力概述

- **端到端**：业务需求 →（产品方案）→ 结构规范的 PRD。
- **不只依赖原始需求**：按「现有 PRD ＞ 交互原型/项目资料 ＞ 原始需求」的优先级取信。
- **四种情形**自适应：无 PRD→从零生成 / 有但不完善→补全 / 仅细微不规范→检查修正 / 已完善→不动。
- **结构与规范统一**：阿拉伯数字序号、三级章节结构、字段表列名规范、🔶 假设 / 🔵 待确认 行内标记、产出末尾自检。
- **交互原型**：UI 图来自交互原型截图；交互概览以**画板/故事板**形式串联截图。

## 🧩 技能组成（1 入口 + 5 分件）

整理顺序镜像「需求 → 产品方案 → 详细文档」：

| Skill | 角色 | 覆盖 PRD 内容 |
|---|---|---|
| **vibe-designing** | 总入口 / 编排 | 判断阶段并路由到下面五件，内置完整 pipeline 与章节地图 |
| **vibe-designing-describe** | Why | 需求摘要、版本信息、变更日志、背景和业务期望 |
| **vibe-designing-businessflow** | What·宏观 | 需求目标+成功指标、使用场景、名词解释、关键业务流程、产品架构图、需求功能清单、Out-of-Scope |
| **vibe-designing-field** | What·字段 | 功能详细说明里的**搜索 / 编辑 / 列表**三类字段说明表 |
| **vibe-designing-feature** | What·规则 | 需求概述、功能说明表、状态-操作矩阵、权限节点/操作日志表、三级章节结构 |
| **vibe-designing-uiux** | What·界面 | 交互概览（画板）、UI 页面图、交互说明、复杂功能点的核心业务流程交互图 |
| **vibe-designing-prototype** | 姊妹分件·原型 | 需求 → 可交互 HTML 原型：多源提取、分层归属、控件模式库、交互范式、防坑清单、DOM 断言验证（产原型非 PRD）|
| **vibe-designing-publish** | 姊妹分件·发布 | 成文 PRD md → 发布到云文档（如 Lark/飞书），对齐团队模板样式；⚠️ 涉及外部系统写操作，发布前须备份、范围须用户确认 |

**Pipeline**：

```
业务需求 / 现有 PRD / 交互原型
        │
        ▼
  vibe-designing（总入口：盘点输入 → 判断情形 → 路由）
        │
  describe ──► businessflow ──►  功能详细说明：field ∥ feature ∥ uiux
   (Why)        (What·宏观)        (字段)  (规则)  (界面)
```

`field / feature / uiux` 在「功能详细说明」内协作：feature 搭章节结构与业务规则，field 填字段表，uiux 贴 UI 图与交互说明，三者拼成每个功能模块的完整说明。

> 姊妹分件 **prototype** 不产 PRD 章节：PRD 的功能清单/字段表指导原型做什么；原型反过来供 uiux 截图、供 field 核对字段与控件。
> 姊妹分件 **publish** 消费成文 PRD，把它发布到云文档并对齐模板样式——是唯一会写外部系统的分件，默认先备份、经确认后再执行。

## 📐 全局约定

1. **输入优先级**：现有 PRD（基准）＞ 交互原型/项目资料（落地，常修正原始需求）＞ 原始需求（方向）。
2. **四种情形**：按现有 PRD 完善度逐项判断动作（生成/补全/修正/不动）。
3. **章节序号**统一阿拉伯数字（`1` / `1.1` / `7.1.2`），不用中文大写。
4. **字段表三类**：搜索/编辑＝11 列（含交互类型/数据来源/提示文案/反馈/规则描述），列表＝6 列。
5. **缺口标记**：🔶 未验证假设 / 🔵 待确认，就地标注，不编造。
6. **交互概览**＝画板/故事板（截图+箭头+步骤串联），非纯文字主线。

## 📁 仓库结构

```
.
├── vibe-designing.skill              # 总入口（.skill = ZIP，内含 SKILL.md）
├── vibe-designing-describe.skill
├── vibe-designing-businessflow.skill
├── vibe-designing-field.skill        # 内含 references/field-examples.md
├── vibe-designing-feature.skill
├── vibe-designing-uiux.skill
├── vibe-designing-prototype.skill
├── vibe-designing-publish.skill
├── Public-log/public-log.md          # 公开更新日志
└── README.md
```

## 🚀 使用

1. 在 Claude / Claude Code 中加载本套 skill。
2. 提供输入：业务需求 / 现有 PRD / 交互原型。
3. 直接说诉求即可，例如：
   - 「把这份需求整理成 PRD」→ 总入口按 pipeline 跑全程；
   - 「梳理功能说明 / 整理字段说明表 / 给功能模块补 UI 图」→ 路由到对应分件。
4. 产出结构规范的 PRD 内容；缺口以 🔵 标注，末尾附自检与下一步建议。

## 🛠️ 二次开发（编辑与打包）

每个 `.skill` 是一个 ZIP 包，内部结构为 `<name>/SKILL.md`（field 另含 `references/`）。编辑流程：解压 → 改 `SKILL.md` → 重新打包（保持内部路径 `<name>/SKILL.md`）。环境无 `zip` 命令时可用 Python：

```bash
python -c "import os,zipfile;n='vibe-designing-uiux';src=n;z=zipfile.ZipFile(n+'.skill','w',zipfile.ZIP_DEFLATED);[z.write(os.path.join(r,f),os.path.join(n,os.path.relpath(os.path.join(r,f),src)).replace(os.sep,'/')) for r,_,fs in os.walk(src) for f in fs];z.close()"
```

## 🔌 交互原型截图（uiux 配套技巧）

为功能模块配 UI 图时，推荐用**无头浏览器直接把原型页面写成 PNG**（可靠落盘、可嵌入文档）：

```bash
# 原型若需本地服务，先起静态服务器；再用无头浏览器截图
chrome --headless=new --hide-scrollbars \
  --force-device-scale-factor=2 \        # 2× 高清
  --virtual-time-budget=5000 \           # 等图标/字体加载
  --screenshot="out.png" --window-size=1280,1400 "http://localhost:PORT/页面.html"
```

- **交互态**（需点击展开的抽屉/弹窗）：复制原型页为临时副本，在 `</body>` 前注入「自动展开」脚本，截后删除副本。
- **自动裁白**：截后用 PIL `ImageChops.difference + getbbox` 裁掉四周纯色边，小卡片页只留元素。
- **交互概览故事板**：用 PIL 把多张截图横排、画箭头、加步骤说明，拼成一张画板图。
- 经验：浏览器扩展类截图可能不回传可用磁盘路径，**务必用无头浏览器落盘**，并对「截图后 / 嵌入后」各复查一次。

## 📜 更新日志

见 [`Public-log/public-log.md`](Public-log/public-log.md)。当前版本 **V1.0**（tag `v1.0`）。

## 设计依据

归纳自实践中沉淀的 PRD 写作 house style + 团队需求文档模板，并吸收通用 PM 方法论（摘要句式、成功指标三件套、显式 Out-of-Scope、行内缺口标记、产出自检）。
