# VDA 5050 中英文文档对照检查

## 文档说明

本文档记录当前分支中 `VDA5050_EN.md` 与 `VDA5050_210_ZH.md` 的对照检查结果。

- **检查分支**：`2.1.0-zh-CN`
- **检查提交**：当前工作树（英文原文只读）
- **检查日期**：2026-08-10
- **英文原文**：`VDA5050_EN.md`，VDA 5050 Version 2.1.0
- **中文译稿**：`VDA5050_210_ZH.md`
- **英文原文约束**：英文原文、Schema 和共享英文资源的问题只记录，不修改源文件。
- **相关记录**：[trans-guide.md](./trans-guide.md)、[trans-dict.md](./trans-dict.md)、[trans-todo-list.md](./trans-todo-list.md)、[trans-issues-sols.md](./trans-issues-sols.md)

## 总体结论

V2.1.0 中文译稿已完成全文翻译和结构复核。未发现中文稿存在必须立即修复的协议语义、字段名称、枚举值或 Markdown 结构错误。英文原文中已确认的疑点已在 `trans-issues-sols.md` 记录，中文稿按字段表、章节上下文和版本边界作了必要规避；`VDA5050_EN.md` 未被修改。

## 分级结果

| 分级 | 结论 | 检查结果 | 处理建议 |
| --- | --- | --- | --- |
| P0：必须处理 | 已完成 | 未发现中文稿字段缺失、字段误译、枚举错误、状态流程错误或规范性强度改变。 | 当前无 P0 中文修改项。 |
| P1：不着急处理 | 已完成，保留源问题追踪 | `nodeSequenceId`/`sequenceId`、即时动作的 `actionState`、`initPosition` 完成字段、`state.serialNumber` 等高风险项已逐项核对。 | 等待 `EN-210-*` 对应的英文或 Schema 结论。 |
| P2：可忽略或等待官方 | 已完成 | 表格样式、换行标签、图号和 factsheet 结构问题已在中文稿中规避；英文源问题仍保留记录。 | 不回写英文，后续按官方修订复核。 |

## 结构核对

| 项目 | EN | ZH | 结论 |
| --- | ---: | ---: | --- |
| 标题（H1-H4） | 71 | 71 | 一致 |
| 图片引用 | 17 | 17 | 一致，路径对应 |
| 图表题注 | 20 | 20 | 一致 |
| 表格分隔行 | 48 | 48 | 一致 |
| 无序列表项 | 55 | 55 | 一致 |
| 有序步骤项 | 25 | 25 | 一致 |
| 代码围栏 | 6 | 6 | 一致 |

- 表格列数、空白格式、中文内部锚点和代码围栏检查通过。
- 中文稿未发现 `<a>`、`</a>`、`</br>`、`<\\br>` 或双层括号链接。
- `git diff --check` 通过。

## 已记录的 V2.1.0 原文问题

- `EN-210-01`：`nodeSequenceId` 与实际 `sequenceId` 不一致。
- `EN-210-02`：即时动作叙述将 `actionState` 对象误写为 `actionStatus`。
- `EN-210-03`：`initPosition` 完成状态误写 `.agvPosition.lastNodeId`。
- `EN-210-04`：`state.SerialNumber` 大小写错误。
- `EN-210-05`：`float 64` 类型拼写错误。
- `EN-210-06`：边对象将 `actions [action]` 错写为单数 `action [action]`，且闭合标记混排。
- `EN-210-07`：`corridor` 宽度错误引用图 13，中文改为图 10。
- `EN-210-08`：factsheet 表格嵌套及 `versions[versionInfo]` 行结构损坏。
- `EN-210-09`：`<br/>`、`</br>` 等换行标记不一致。

问题位置、证据、中文处理和官方状态以 [trans-issues-sols.md](./trans-issues-sols.md) 为准。

## 后续触发条件

- 官方修订 V2.1.0 英文或配套 Schema 后，按 `EN-210-*` 条目逐项复查中文稿。
- 新版本翻译必须新建或明确命名对应中文目标文件，并更新字典、TODO、问题记录和检查报告；不得将 V2.1.0 结论直接套用于 3.x。
