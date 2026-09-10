# vibe designing skill

> 写 PRD 这件事，费脑子的是想清楚要做什么，费时间的却是把想清楚的东西按模板码成一份规范文档。这套技能（Claude / Claude Code Skills）接手后半段：给一份业务需求或原始诉求，它分析需求、拆解抽象成产品方案、整理成结构规范的 PRD。

后台管理类产品的 PRD 翻来覆去就那几样：摘要、背景期望、产品方案、名词解释、流程架构图、需求功能清单，每个功能模块再配上**搜索/编辑/列表字段表、功能说明表、状态-操作矩阵、交互原型图**。这套技能把这些写法沉淀下来，既能从零整理，也能拿去质检已有的 PRD。

---

## ✨ 能力概述

- **端到端**：业务需求 →（产品方案）→ 结构规范的 PRD；
- **不只依赖原始需求**：按现有 PRD ＞ 交互原型/项目资料 ＞ 原始需求的优先级取信；
- **四种情形自适应**：无 PRD 就从零生成，有但不完善就补全，仅细微不规范就检查修正，已完善就不动；
- **结构与规范统一**：阿拉伯数字序号、三级章节结构、字段表列名规范、🔶 假设 / 🔵 待确认 行内标记、产出末尾自检；
- **行文文风**：产出的是【人话】——口语连接词、真实取值举例、主语点名到具体角色或系统、规则不带目的从句；配 15 条 AI 味自检表，机器腔在交付前就扫掉；
- **交互原型**：UI 图来自交互原型截图，交互概览用**画板/故事板**把截图串起来。

## 🧩 技能组成（1 入口 + 6 分件 + 3 姊妹分件）

整理顺序跟着做事的顺序走：体检 → 需求 → 产品方案 → 详细文档。

| Skill | 角色 | 覆盖 PRD 内容 |
|---|---|---|
| **vibe-designing** | 总入口 / 编排 | 判断阶段并路由到各分件，内置完整 pipeline、章节地图、正向↔反向双向流转说明，并附 **PRD 骨架模板** 与 **行文文风规范**（人味十条 + AI 味自检表 + 句式模板库，六个产文字的分件共用）|
| **vibe-designing-intake** | 第 0 段 · 体检 | 拿到需求先体检：六维度查缺失/矛盾/口径存疑 → **澄清清单**（每条带建议默认值）+ **可开工判断**（可直接写 / 边写边问 / 必须先澄清）（产清单非 PRD）|
| **vibe-designing-describe** | Why | 需求摘要、版本信息、变更日志、背景和业务期望 |
| **vibe-designing-businessflow** | What·宏观 | 需求目标+成功指标、使用场景、名词解释、关键业务流程、产品架构图、需求功能清单 |
| **vibe-designing-field** | What·字段 | 功能详细说明里的**搜索 / 编辑 / 列表**三类字段说明表 |
| **vibe-designing-feature** | What·规则 | 需求概述、功能说明表、状态-操作矩阵、权限节点/操作日志表、三级章节结构 |
| **vibe-designing-uiux** | What·界面 | 交互概览（画板）、UI 页面图、交互说明、复杂功能点的核心业务流程交互图 |
| **vibe-designing-prototype** | 姊妹分件·原型 | 需求 → 可交互 HTML 原型：多源提取、分层归属、控件模式库、交互范式、防坑清单、DOM 断言验证（产原型非 PRD）|
| **vibe-designing-testcase** | 姊妹分件·用例 | 成文 PRD → **测试用例表**（校验/功能/状态流转/权限/交互/展示/动效等九类，含边界与异常）+ **PRD 可验证性体检报告**——推不出用例的地方就是 PRD 的缺口（产用例非 PRD）|
| **vibe-designing-publish** | 姊妹分件·发布 | 成文 PRD md → 发布到云文档（如 Lark/飞书），对齐团队模板样式；⚠️ 会写外部系统，发布前先备份，范围要用户确认 |

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

`field / feature / uiux` 三个分件在【功能详细说明】里协作：feature 搭章节结构与业务规则，field 填字段表，uiux 贴 UI 图与交互说明，三者拼成每个功能模块的完整说明。

> 姊妹分件 **prototype** 不产 PRD 章节：PRD 的功能清单和字段表告诉原型要做什么；原型反过来供 uiux 截图、供 field 核对字段与控件。
> 姊妹分件 **publish** 消费成文 PRD，把它发到云文档并对齐模板样式——它是唯一会写外部系统的分件，默认先备份、经确认后再执行。

## 📐 全局约定

1. **输入优先级**：现有 PRD（基准）＞ 交互原型/项目资料（落地，常修正原始需求）＞ 原始需求（方向）。
2. **四种情形**：按现有 PRD 完善度逐项判断动作——从零生成、补全、修正、不动。
3. **章节序号**：统一用阿拉伯数字（`1` / `1.1` / `7.1.2`），不用中文大写。
4. **字段表三类**：搜索和编辑＝11 列（含交互类型、数据来源、提示文案、反馈、规则描述）；列表＝6 列。
5. **缺口标记**：🔶 未验证假设、🔵 待确认，就地标注，不编造。
6. **交互概览**：用画板或故事板（截图 + 箭头 + 步骤串联），不用纯文字主线。
7. **行文文风**：写的是【交代事情】不是【定义系统】——用口语连接词（就、即、暂时）不用书面连接词（从而、以便、旨在）；举例落到真实取值不用占位符；主语点名到具体角色或系统，不写 `系统自动…`；规则只说做什么，不补 `用于…` 的尾巴。
8. **标点**：一段需求说明里每行以 `；` 结尾、最后一行以 `。` 收尾；不用行尾裸奔、不每行句号、不用 `1. 2. 3.` + `a. b. c.` 两级编号。
9. **标注**：（）写补充说明、【】标重点词汇、变量值进 code（`Draft`、`Please input game name`、`48×48，JPG/PNG，≤2MB`）；⛔ 不用直角引号。
10. **读云文档走块结构**：⛔ 不用 `纯文本导出` 接口——它会丢标题层级、表格结构、列表符号、加粗链接和图片位置，表格还会被拍平成一行一格；要先列出块树再还原成 Markdown；导出固化成一条命令，并内置自检（结构计数 + 图片引用完整性）。

## 📁 仓库结构

```
.
├── vibe-designing.skill              # 总入口（.skill = ZIP，内含 SKILL.md + references/：PRD 骨架模板、行文文风规范等）
├── vibe-designing-intake.skill       # 第 0 段：需求体检与澄清
├── vibe-designing-describe.skill
├── vibe-designing-businessflow.skill
├── vibe-designing-field.skill        # 内含控件映射 / 报错文案库 / 字段范例等 references
├── vibe-designing-feature.skill
├── vibe-designing-uiux.skill         # 内含截图与制图操作手册
├── vibe-designing-prototype.skill    # 内含控件模式库与防坑清单
├── vibe-designing-publish.skill      # 内含 API 机制、样式映射、脚本骨架
├── vibe-designing-testcase.skill     # PRD → 测试用例 + 可验证性体检
├── Public-log/public-log.md          # 公开更新日志
└── README.md
```

## 🚀 使用

1. 在 Claude / Claude Code 里加载本套 skill；
2. 给输入：业务需求、现有 PRD 或交互原型；
3. 直接说诉求就行，比如：
   - `这份需求清楚吗` / `有什么要跟业务确认的` → 先体检，出澄清清单；
   - `把这份需求整理成 PRD` → 总入口按 pipeline 跑全程；
   - `梳理功能说明` / `整理字段说明表` / `给功能模块补 UI 图` → 路由到对应分件；
   - `根据 PRD 出测试用例` → 产用例表，顺带反向体检 PRD 的可验证性。
4. 产出结构规范的 PRD 内容，缺口以 🔵 标注，末尾附自检与下一步建议。

## 🛠️ 二次开发（编辑与打包）

每个 `.skill` 就是一个 ZIP 包，内部结构为 `<name>/SKILL.md`，多数分件另含 `references/`。改法：解压 → 改 `SKILL.md` → 重新打包（内部路径保持 `<name>/SKILL.md`）。环境里没有 `zip` 命令就用 Python：

```bash
python -c "import os,zipfile;n='vibe-designing-uiux';src=n;z=zipfile.ZipFile(n+'.skill','w',zipfile.ZIP_DEFLATED);[z.write(os.path.join(r,f),os.path.join(n,os.path.relpath(os.path.join(r,f),src)).replace(os.sep,'/')) for r,_,fs in os.walk(src) for f in fs];z.close()"
```

## 🔌 交互原型截图（uiux 配套技巧）

给功能模块配 UI 图，推荐**用无头浏览器直接把原型页面写成 PNG**——落盘可靠，能直接嵌进文档：

```bash
# 原型若需本地服务，先起静态服务器；再用无头浏览器截图
chrome --headless=new --hide-scrollbars \
  --force-device-scale-factor=2 \        # 2× 高清
  --virtual-time-budget=5000 \           # 等图标/字体加载
  --screenshot="out.png" --window-size=1280,1400 "http://localhost:PORT/页面.html"
```

- **交互态**（要点击才展开的抽屉、弹窗）：复制原型页为临时副本，在 `</body>` 前注入自动展开脚本，截完删掉副本；
- **自动裁白**：截完用 PIL `ImageChops.difference + getbbox` 裁掉四周纯色边，小卡片页只留元素；
- **交互概览故事板**：用 PIL 把多张截图横排、画箭头、加步骤说明，拼成一张画板图；
- **经验**：浏览器扩展类截图可能不回传可用的磁盘路径，**务必用无头浏览器落盘**，截图后和嵌入后各复查一次。

## 📜 更新日志

见 [`Public-log/public-log.md`](Public-log/public-log.md)。当前版本 **V1.2**（tag `V1.2`）。

## 设计依据

归纳自实践中沉淀的 PRD 写作 house style + 团队需求文档模板，再吸收通用 PM 方法论（摘要句式、成功指标三件套、行内缺口标记、产出自检）。文风部分单独归纳自 8 份真实 PRD，逐句对照过人写与 AI 写的同一条规则。
