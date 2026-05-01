> **Note:** 本仓库为内部 Skill 集合。关于 Agent Skills 标准规范，请参阅 [agentskills.io](http://agentskills.io)。

# Skills

Skills 是包含指令、脚本和资源的文件夹，Claude 加载后可在特定任务中提供更专业、更贴合团队规范的输出。Skills 能够以可复现的方式完成专项任务，无论是生成符合客户汇报风格的 PPT 内容、梳理数据工程 Agent 的功能架构，还是撰写口语化的产品功能清单。

更多信息请参阅：
- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Equipping agents for the real world with Agent Skills](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

# 关于本仓库

本仓库收录面向数据平台产品规划、技术方案设计、项目交付文档编写等场景的 Skills。涵盖产品架构描述、PPT 文案生成、数据标注流程梳理、竞标策略分析、标准需求文档输出等工作流。

每个 Skill 均为独立文件夹，内含 `SKILL.md` 文件（指令与元数据）及必要的参考资源。浏览这些 Skills 既可了解不同模式与写法，也可作为自建 Skill 的参考。

## 免责声明

**本仓库中的 Skills 仅供内部学习、演示及项目交付辅助使用。** Claude 实际加载后的行为可能与 Skill 描述存在差异。这些 Skills 旨在展示模式与可能性，在用于关键任务前，请务必在真实环境中充分测试。

# 仓库目录结构

## 1. 根目录结构

```
skills-repo/                    # 仓库根目录
├── README.md                   # 本文件，仓库说明与使用指南
├── skills/                     # 所有 Skill 的存放目录（核心）
│   ├── ppt-content-generator/  # 示例：PPT 文案生成 Skill
│   ├── product-architecture/   # 示例：产品架构描述 Skill
│   └── ...                     # 其他 Skill 文件夹
├── spec/                       # Agent Skills 规范文档（可选）
│   └── skill-spec.md           # 规范参考文件
└── template/                   # 新建 Skill 的空白模板
    └── SKILL.md                # 空白模板文件
```

## 2. 单个 Skill 内部目录结构

每个 Skill 必须是一个**独立文件夹**，文件夹名称即为 Skill 的标识名称（小写，单词间用连字符 `-` 连接）。

### 2.1 强制文件

每个 Skill 文件夹内**必须且只能有一个**核心文件：

| 文件名 | 说明 | 是否必填 |
|:---|:---|:---|
| `SKILL.md` | 包含 YAML frontmatter + Markdown 指令内容 | **必填** |

Claude 通过识别 `SKILL.md` 来加载 Skill，缺少此文件则 Skill 无法被识别。

### 2.2 可选子目录

根据 Skill 的复杂程度，可在 Skill 文件夹内创建以下子目录存放辅助资源：

| 子目录名 | 用途 | 存放内容 | 使用建议 |
|:---|:---|:---|:---|
| `examples/` | 示例参考 | 输入文件、期望输出文件、示例对话记录 | 当 Skill 对输出格式有严格要求时，提供 1-3 组完整的输入/输出示例 |
| `assets/` | 静态资源 | 图片、图表、架构图、模板截图、品牌素材 | 当指令中需要引用特定图片或模板样式时使用 |
| `scripts/` | 辅助脚本 | Python、Shell、JS 等辅助处理脚本 | 当 Skill 涉及数据转换、格式校验等需要脚本辅助的场景 |
| `resources/` | 参考资料 | 术语表、规范文档、竞品分析材料、背景知识 | 当 Skill 需要引用外部知识库或特定业务背景时使用 |
| `templates/` | 输出模板 | Markdown 模板、PPT 结构模板、表格模板 | 当 Skill 要求按固定模板输出时，将模板文件独立存放 |

### 2.3 目录层级规范

- Skill 文件夹内部**最多两层**子目录，避免过度嵌套
- 所有资源文件应使用**语义化命名**，避免 `1.md`、`a.png` 等无意义名称
- 资源文件名统一使用**小写 + 连字符**，与 Skill 文件夹命名风格保持一致

### 2.4 三种典型结构示例

#### 极简结构（纯文本指令）

适用于逻辑简单、无需外部参考的 Skill：

```
skills/
└── text-polisher/              # Skill 文件夹
    └── SKILL.md                # 仅包含核心指令文件
```

#### 标准结构（指令 + 示例）

适用于需要明确输入输出范式的 Skill：

```
skills/
└── ppt-content-generator/        # Skill 文件夹
    ├── SKILL.md                # 核心指令文件
    └── examples/               # 示例目录
        ├── input-topic.md      # 输入示例：原始话题/需求描述
        └── output-slides.md    # 输出示例：生成的 PPT 文案
```

#### 完整结构（指令 + 示例 + 资源 + 脚本）

适用于复杂业务场景，需要多类资源协同：

```
skills/
└── product-architecture/       # Skill 文件夹
    ├── SKILL.md                # 核心指令文件
    ├── examples/               # 示例目录
    │   ├── input-requirement.md
    │   └── output-architecture.md
    ├── assets/                 # 资源目录
    │   ├── module-diagram.png  # 架构图参考
    │   └── style-guide.png     # 风格示例图
    ├── resources/              # 参考资料目录
    │   ├── terminology.md      # 术语表
    │   └── competitor-analysis.md  # 竞品分析材料
    └── scripts/                # 脚本目录
        └── validate-format.py  # 输出格式校验脚本
```

### 2.5 命名规则汇总

| 层级 | 规则 | 正确示例 | 错误示例 |
|:---|:---|:---|:---|
| 仓库名 | 小写，可带连字符 | `ai-data-skills` | `AI_Data_Skills` |
| Skill 文件夹名 | 小写，连字符连接，无空格 | `ppt-content-generator` | `PPT Content Generator` |
| `SKILL.md` 文件名 | 固定大写 | `SKILL.md` | `skill.md` |
| 资源文件夹名 | 小写，语义化 | `examples/`, `assets/` | `Examples/`, `ASSETS/` |
| 资源文件名 | 小写，连字符，语义化 | `module-diagram.png` | `模块图.png`, `1.png` |

## 3. 本仓库完整示例结构

```
skills-repo/
├── README.md
├── skills/
│   ├── ppt-content-generator/
│   │   ├── SKILL.md
│   │   └── examples/
│   │       ├── input-topic.md
│   │       └── output-slides.md
│   ├── product-architecture/
│   │   ├── SKILL.md
│   │   ├── examples/
│   │   │   ├── input-requirement.md
│   │   │   └── output-architecture.md
│   │   └── assets/
│   │       └── module-diagram.png
│   ├── data-annotation-workflow/
│   │   ├── SKILL.md
│   │   └── resources/
│   │       └── terminology.md
│   ├── data-flywheel-design/
│   │   └── SKILL.md
│   ├── bid-strategy/
│   │   ├── SKILL.md
│   │   ├── examples/
│   │   │   └── competitor-analysis.md
│   │   └── resources/
│   │       └── risk-matrix-template.md
│   └── requirement-doc-standard/
│       ├── SKILL.md
│       └── templates/
│           └── standard-prd-template.md
├── spec/
│   └── skill-spec.md
└── template/
    └── SKILL.md
```

# SKILL.md 文件格式

`SKILL.md` 是每个 Skill 的唯一必填文件，采用 **YAML frontmatter + Markdown** 格式：

```markdown
---
name: skill-name               # 必填：唯一标识，与文件夹名保持一致
description: 描述该 Skill 的用途及触发场景  # 必填：完整描述何时使用
---

# Skill 名称

[在此处编写 Claude 加载该 Skill 后应遵循的指令、输出格式、风格要求等]

## 示例
- 示例用法 1
- 示例用法 2

## 规范
- 规范 1
- 规范 2
```

## Frontmatter 必填字段

- `name`：Skill 的唯一标识（小写，空格用连字符替换，必须与文件夹名一致）
- `description`：完整描述该 Skill 的功能及何时使用，Claude 会根据此描述判断是否激活该 Skill

## Markdown 正文内容

正文部分包含 Claude 加载后将遵循的具体指令，建议包含以下章节：

| 章节 | 说明 |
|:---|:---|
| `# Skill 名称` | 一级标题，Skill 的显示名称 |
| `## 任务说明` | 描述该 Skill 解决什么问题 |
| `## 输出格式` | 规定输出结构、层级、字数、是否使用表格等 |
| `## 风格要求` | 语气（口语化/正式）、用词规范、禁用词汇 |
| `## 示例` | 提供 1-2 个完整的输入输出示例 |
| `## 注意事项` | 边界情况、常见错误、审核要点 |

# 新建 Skill 的标准流程

1. **复制模板**：将 `template/SKILL.md` 复制到 `skills/` 下新建的文件夹中
2. **命名文件夹**：`mkdir skills/my-new-skill`
3. **编辑 frontmatter**：填写 `name` 和 `description`
4. **编写指令**：在 Markdown 正文中详细描述任务流程、输出规范、风格约束
5. **添加资源**（可选）：如需参考文件，按规范放入 `examples/`、`assets/`、`resources/` 等子目录
6. **测试验证**：在 Claude 中加载并测试输出是否符合预期
7. **提交仓库**：`git add skills/my-new-skill/` 并提交

# 在 Claude 中使用

## Claude Code

将本仓库注册为 Claude Code 的 Plugin Marketplace：

```bash
/plugin marketplace add <your-org>/skills-repo
```

然后安装并使用指定 Skill：

1. 选择 `Browse and install plugins`
2. 选择 `<your-org>-skills-repo`
3. 选择 `document-skills` 或 `example-skills`
4. 选择 `Install now`

或直接安装：

```bash
/plugin install document-skills@<your-org>-skills-repo
/plugin install example-skills@<your-org>-skills-repo
```

安装后，在对话中直接提及 Skill 名称即可使用，例如：

> "使用 ppt-content-generator 帮我写一份数据供给中心模块的汇报 PPT 文案"

## Claude.ai

付费计划用户可直接上传本仓库中的 Skill 文件夹或单个 `SKILL.md` 文件。操作路径：设置 → 个性化 → 添加 Skill。

## Claude API

可通过 API 上传并使用自定义 Skills，详见 [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide)。

# 创建基础 Skill

创建 Skill 非常简单——只需一个文件夹，其中包含带有 YAML frontmatter 和指令内容的 `SKILL.md` 文件。可基于本仓库的 **template** 目录作为起点：

```markdown
---
name: my-skill-name
description: 清晰描述该 Skill 的用途及适用场景
---

# Skill 名称

[在此处编写 Claude 加载该 Skill 后应遵循的指令、输出格式、风格要求等]

## 示例
- 示例用法 1
- 示例用法 2

## 规范
- 规范 1
- 规范 2
```

Frontmatter 仅需两个必填字段：
- `name` — Skill 的唯一标识（小写，空格用连字符替换）
- `description` — 完整描述该 Skill 的功能及何时使用

下方的 Markdown 内容包含指令、示例与规范，Claude 加载后将遵循这些内容执行任务。更多细节请参阅 [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)。

# 维护说明

- **新增 Skill**：基于 `template/SKILL.md` 创建，确保 `name` 和 `description` 准确无误，文件夹名与 `name` 保持一致
- **迭代更新**：当客户汇报风格、技术架构规范或产品功能定义发生变化时，及时更新对应 Skill 的指令内容
- **版本同步**：建议定期 `git pull` 同步最新仓库版本，确保 Claude 输出与当前项目阶段及客户要求保持一致
- **测试验证**：关键 Skill 更新后，务必在 Claude 中重新加载并验证输出质量，避免直接用于正式交付材料
```

---

**使用建议：**

1. 在 GitHub 创建仓库后，将上述内容保存为根目录的 `README.md`
2. 创建 `template/SKILL.md` 作为空白模板（可直接复制上文中"创建基础 Skill"部分的代码块）
3. 创建 `spec/` 目录存放规范参考（可选，初期可为空）
4. 将之前生成的各类功能清单规则、PPT 文案风格等，按 Skill 文件夹结构逐一放入 `skills/` 目录
5. 每个 Skill 的 `name` 务必与文件夹名完全一致，否则 Claude 可能无法正确识别
