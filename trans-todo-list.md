# VDA5050_210_ZH.md 翻译同步 TODO

## 0. 当前任务与原文保护

- **当前分支**：`2.1.0-zh-CN`。
- **英文基准**：`VDA5050_EN.md`，标题和版本元信息为 VDA 5050 Version 2.1.0。
- **中文目标**：`VDA5050_210_ZH.md`。
- `VDA5050_EN.md` 仅作为只读对照基准；英文原文、Schema、流程图和 UML 的问题只记录，不直接修改。
- V3.0.0/V3.0.1 的历史差异和问题编号保留在 [trans-issues-sols.md](./trans-issues-sols.md)，不得套用到 V2.1.0 的字段定义。

## 1. 翻译状态

V2.1.0 全文翻译已完成。译文覆盖 EN 的全部章节、表格、图片引用、代码示例和 factsheet 对象；已按 [trans-guide.md](./trans-guide.md) 和 [trans-dict.md](./trans-dict.md) 复核协议字段、枚举、数据类型、规范性措辞及 Markdown 结构。

## 2. 已完成检查

### P0：协议语义和字段契约

- [x] 对照全文主体、触发条件、行为、完成条件、失败结果和恢复规则。
- [x] 保留 V2.1.0 字段和枚举：`lhd`、`.load`、`resultDescription`、`agvPosition`、`initPosition`、`TEACHIN`、`agvGeometry`、`vehicleConfig`。
- [x] 核对 V2.1.0 的 `actionStatus`/`actionState`、`nodeSequenceId`/`sequenceId`、`state.serialNumber` 等高风险标识符；发现原文问题时按 `EN-210-*` 记录并在中文稿中采用有依据的保守处理。
- [x] 核对 `factsheet` 表中的字面属性 `actions.actionsParameters`，未将其误改为普通对象路径。

### P1：章节、字面量和交叉引用

- [x] 标题层级、目录锚点、内部链接和图片路径与英文结构对应。
- [x] 保持字段、主题、动作、枚举、类型、单位和版本示例的原始拼写；`float64`、`TEACHIN` 等类型/枚举未翻译。
- [x] 修正中文稿中的已确认原文问题：即时动作收到后的对象名称、`initPosition` 完成字段、`nodeSequenceId` 叙述、走廊图号和 factsheet 表格嵌套。
- [x] 核对对象结构表中普通、粗体、斜体和粗斜体的必填/可选语义。

### P2：排版和语言

- [x] 中英文标题、图片、表格分隔行、无序列表、有序步骤和代码围栏数量对齐。
- [x] 中文稿未复制英文的损坏链接、`</br>` 等错误换行标签或错位表格列。
- [x] 中文与英文标识符、数字和单位之间的空格、图表题注格式及文件末尾换行已检查。

## 3. 结构统计（2026-08-10）

| 项目 | EN | ZH | 结论 |
| --- | ---: | ---: | --- |
| 标题（H1-H4） | 71 | 71 | 一致 |
| 图片引用 | 17 | 17 | 一致 |
| 图表题注 | 20 | 20 | 一致 |
| 表格分隔行 | 48 | 48 | 一致 |
| 无序列表项 | 55 | 55 | 一致 |
| 有序步骤项 | 25 | 25 | 一致 |
| 代码围栏 | 6 | 6 | 一致 |

## 4. 完成验收

- [x] `git diff --check` 通过。
- [x] `git diff HEAD -- VDA5050_EN.md` 无输出；英文原文未修改。
- [x] `VDA5050_EN.md` 与 `VDA5050_210_ZH.md` 的标题、图片、表格、列表和代码围栏统计通过。
- [x] 中文内部锚点、表格列数、代码围栏和高风险字段检索通过。
- [x] 维护文档已同步到分支 `2.1.0-zh-CN` 和目标 `VDA5050_210_ZH.md`。

## 5. 待确认问题

以下问题属于 V2.1.0 英文原文或共享资源，中文稿已避免复制其错误；详细证据和处理方案见 [trans-issues-sols.md](./trans-issues-sols.md)。

| 编号 | 位置 | 问题摘要 | 中文稿处理 | 状态 |
| --- | --- | --- | --- | --- |
| EN-210-01 | `VDA5050_EN.md:511` | 叙述使用不存在的 `nodeSequenceId`，同一版本字段和后文使用 `sequenceId`。 | 按字段表和后文译为 `sequenceId`，不新增字段。 | 待官方确认 |
| EN-210-02 | `VDA5050_EN.md:926` | 收到即时动作后错误写成添加 `actionStatus`，实际应添加 `actionState` 对象。 | 中文稿写为添加 `actionState`，对象内状态字段仍为 `actionStatus`。 | 待官方确认 |
| EN-210-03 | `VDA5050_EN.md:889` | `initPosition` 完成状态误写 `.agvPosition.lastNodeId`，动作参数表定义为顶层 `lastNodeId`。 | 中文稿按参数契约使用顶层 `lastNodeId`。 | 待官方确认 |
| EN-210-04 | `VDA5050_EN.md:1351` | factsheet 受影响参数写成 `state.SerialNumber`，字段定义为 `state.serialNumber`。 | 中文稿使用小写 `serialNumber`。 | 待官方确认 |
| EN-210-05 | `VDA5050_EN.md:1102` | 数据类型拼写为 `float 64`。 | 中文稿规范为 `float64`。 | 待官方确认 |
| EN-210-06 | `VDA5050_EN.md:701,743` | 节点对象使用 `actions [action]`，边对象却写成单数 `action [action]`，并与对象闭合标记混排。 | 中文稿按字段契约统一使用 `actions [action]`，并保持表格闭合和列数正确。 | 待官方确认 |
| EN-210-07 | `VDA5050_EN.md:764-765` | `corridor` 宽度说明错误引用图 13，实际走廊图为图 10。 | 中文稿引用图 10。 | 待官方确认 |
| EN-210-08 | `VDA5050_EN.md:1288-1496` | factsheet 表存在嵌套列、错误换行标签和 `versions[versionInfo]` 行结构损坏。 | 中文稿保证自身表格列数、换行和嵌套结构有效，并保留字面属性。 | 待官方确认 |
| EN-210-09 | `VDA5050_EN.md:1320,1408,1525` | 混用 `<br/>` 和 `</br>` 换行标记，部分 Markdown 表格因此难以解析。 | 中文稿统一使用 `<br>`，不复制错误闭合标签。 | 待官方确认 |

## 6. 后续触发项

- [ ] 官方修订 V2.1.0 英文或配套 Schema 后，按 `EN-210-*` 条目逐项复查中文稿。
- [ ] 若新增 V2.1.0 勘误或版本分支，先更新字典和问题记录，再修改中文译文。
