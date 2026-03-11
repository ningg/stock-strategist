---
name: template-skill
description: Provides a minimal template for creating new Cursor skills, including recommended structure, sections, and placeholders. Use when setting up a new Agent Skill and you want a starting skeleton to customize.
---

# Template Skill

这个模板 skill 用来演示一个典型的 Cursor Skill 结构。复制本文件并按需修改占位内容即可。

## Instructions

按照下面步骤基于本模板创建新 skill：

1. **复制目录**：将整个 `template-skill` 目录复制为你自己的 skill 名称，例如 `my-new-skill`。
2. **修改 frontmatter**：
   - 更新 `name` 为新 skill 名（全小写、数字、短横线）。
   - 更新 `description`，描述该 skill 做什么、在什么场景下使用。
3. **替换标题与说明**：
   - 把 `# Template Skill` 改成你的 skill 名称或简短描述。
   - 删除本段“使用说明”，改成与你场景相关的指导。
4. **根据需要添加文件**：
   - 如果需要更详细的文档，在同目录下创建 `reference.md`。
   - 如果需要示例，在同目录下创建 `examples.md`。
   - 如果有脚本，在 `scripts/` 目录下添加脚本文件。

当该 skill 生效后，Agent 会在满足触发条件时自动读取本 `SKILL.md`，并遵循其中的指导执行任务。

## Sections Overview

下面列出了常用的几个 section，你可以按需保留、删减或重命名：

- **Instructions**：面向 Agent 的具体执行步骤、注意事项、工作流。
- **Checklist**：关键检查项，帮助保证输出质量。
- **Examples**：输入/输出示例，约束风格与格式。
- **Additional Resources**：链接到本目录下的其他文件，如 `reference.md`、`examples.md`。

## Checklist (示例)

在实现具体逻辑的 skill 时，可以提供一个简单 checklist，Agent 在执行时可以对照自检：

- [ ] 明确任务目标与输入输出
- [ ] 遵守项目或团队现有规范（命名、目录结构、代码风格等）
- [ ] 在进行修改前先阅读相关文件
- [ ] 如果有脚本或工具，要说明是“参考阅读”还是“直接执行”
- [ ] 输出结果前进行快速自检（格式是否正确、是否遗漏关键信息）

你可以将上面 checklist 修改成与你场景高度相关的条目。

## Examples (占位示例)

你可以在本 section 中放 1–3 个具体示例，演示该 skill 应该如何工作。

示例结构建议：

```markdown
### Example 1: [简短标题]

**Input 场景**
- 用户提供了什么信息？
- 项目当前处于什么状态？

**Agent 目标**
- Agent 需要完成的核心任务是什么？

**期望输出要点**
- 输出形式（例如：markdown 报告、代码 patch、命令行脚本）
- 必须包含的关键段落或字段
```

在真正的 skill 中，把上面模板替换成你业务相关的真实示例。

## Additional Resources (可选)

如果你需要更详细的说明或长文档，不要全部堆在 `SKILL.md` 中，可以：

- 在同目录下新增 `reference.md`：放更详细的背景、长篇说明、API 细节等。
- 在同目录下新增 `examples.md`：集中放大量输入/输出示例。
- 在 `scripts/` 目录下放脚本，并在这里说明如何调用，例如：

```bash
python scripts/your_script.py --help
```

在 `SKILL.md` 中只保留「如何使用这些文件」的简要说明，把长内容放到单独文件中，保证本文件简洁（推荐 < 500 行）。

## Notes for Future You

在你复制本模板并定制完之后，可以删除当前 section，或改成与你 skill 相关的注意事项，例如：

- 该 skill 假设项目使用的语言/框架（如 Python/Node/React 等）。
- 有哪些操作是**禁止**执行的（例如不允许修改某些目录、不能运行带破坏性的脚本）。
- 有哪些关键术语需要保持一致的翻译或命名方式。

