# VDA 5050 翻译问题与处理方案

## 文档说明

本文档用于沉淀 VDA 5050 中文翻译和复核期间发现的英文原文、Schema、Markdown 结构及中英文一致性问题，并记录中文稿的处理措施和后续版本的官方处理结果。

- **记录范围**：包括英文原文疑点、字段或枚举不一致、交叉引用错误、表格结构问题、拼写和格式问题，以及翻译过程中采用的规避或修正方案。
- **记录结构**：每个问题通常包含“EN 位置与问题描述”“译文状态”和“官方处理结果”，用于区分原始问题、中文处理及后续版本变化。
- **编号规则**：问题编号使用版本编码：翻译 V3.0.0 时发现的问题使用 `EN-300-xx`，翻译 V3.0.1 时发现的问题使用 `EN-301-xx`。跨文档或跨版本引用时应保留完整编号，避免不同版本的问题编号混淆。
- **状态标记**：✅ 表示已确认后续版本完成修复；⚠️ 表示仍需关注或进一步复核；❗ 表示尚未修复、仅部分修复或存在新增冲突。状态以各条目记录的复核日期为准。
- **位置口径**：行号对应条目注明日期时的本地文档快照，文件内容变化后可能发生偏移；复核时应结合章节、字段名和上下文定位。
- **原文保护**：`VDA5050_EN.md` 及官方英文资源只作为只读依据。发现原文问题时仅在本文档或 TODO 中记录，不直接修改英文原文。
- **相关文档**：[trans-todo-list.md](./trans-todo-list.md) 用于跟踪当前翻译任务和待确认事项；[trans-dict.md](./trans-dict.md) 用于维护统一术语、标识符及版本适用范围。

<br>

## 未解决的（疑似）问题条目汇总

| 标记 | 编号 | 标题 |
| --- | --- | --- |
| ❗ | EN-300-03 | 双层括号链接 |
| ❗ | EN-300-15 | Table 2 交叉引用错误 |
| ❗ | EN-300-16 | `actionsStates` 字段名错误 |
| ❗ | EN-300-19 | `string` 示例格式不一致 |
| ❗ | EN-300-20 | `reponses` 拼写及对象表结构错误 |
| ❗ | EN-300-23 | 序列号字段大小写及主题名单复数错误 |
| ❗ | EN-300-24 | `actions.actionsParameters` 疑点及 V3.0.1 新增冲突 |
| ❗ | EN-300-27 | 全文拼写、重复词及标记问题 |
| ❗ | EN-301-01 | `boundingBoxReference` 表重复出现 x/y 行 |
| ❗ | EN-301-02 | `actionStatus` 交叉引用错误 |
| ❗ | EN-301-03 | `versions` 数组元素名称与 Schema 不一致 |
| ❗ | EN-301-04 | `actionParameters` 链接双层括号 |
| ❗ | EN-301-05 | factsheet MQTT 参数主题名单复数不一致 |
| ❗ | EN-301-06 | 状态消息触发条件重复且载荷字段不一致 |
| ❗ | EN-301-07 | 表题缺少统一分隔符 |
| ❗ | EN-301-08 | 流程图 `response topic` 主题名单复数不一致 |
| ❗ | EN-301-09 | `requestStatus` 的 `QUEUED` 枚举与字段定义冲突 |

<br>

## EN-300 与 EN-301 关联问题说明

| 关联类型 | 条目 | 关联说明 | 当前结论 |
| --- | --- | --- | --- |
| 同一问题延续 | EN-300-03 ↔ EN-301-04 | 均为 Markdown 链接双层括号问题。V3.0.1 修复了部分位置，但第 1684 行仍保留错误。 | 中文稿已统一使用单层括号；英文问题仍需官方修复。 |
| 同一问题延续 | EN-300-15 ↔ EN-301-02 | 均为 `actionStatus` 说明错误引用 `Table 2`。表格新增后，实际目标从 V3.0.0 的表 11 顺延为 V3.0.1 的表 12。 | 中文稿当前引用表 12；英文引用仍未修复。 |
| 同一问题延续 | EN-300-23 ↔ EN-301-05 | 均涉及 factsheet 中 `response.*` 与协议主题 `responses` 的单复数不一致；EN-300-23 还包含 `state.SerialNumber` 大小写问题。 | 中文稿已使用 `state.serialNumber` 和 `responses.*`；英文仍部分修复。 |
| 同领域、不同缺陷 | EN-300-20 ↔ EN-301-05 | EN-300-20 是 `reponses` 拼写及响应对象表结构问题，EN-301-05 是 factsheet MQTT 参数主题名称问题；二者都位于 responses/factsheet 相关内容，但不能合并为同一缺陷。 | 分别保留两个编号；中文稿均已规避。 |
| 同领域、不同缺陷 | EN-300-24 ↔ EN-301-03 | EN-300-24 是 `actions.actionsParameters` 的文档与 Schema 冲突，EN-301-03 是 `versions[versionInfo]` 与 Schema 数组元素标题冲突；二者均属文档与 Schema 一致性问题，但涉及不同字段。 | 分别跟踪；两项英文/Schema 冲突均待官方确认。 |
| 汇总/延续关系 | EN-300-27 → V3.0.1 | EN-300-27 是 V3.0.0 全文拼写、重复词和标记问题的汇总项；其官方处理结果仍记录 V3.0.1 的 `Receival` 残留，但该残留尚未单独分配 EN-301 编号。 | 作为汇总项保留，不将其与 EN-301-04 或 EN-301-05 重复计数。 |
| 已闭环 | EN-300-12 ↔ V3.0.1 官方修订 | V3.0.1 已将 `COORDINATED_REPLANNING` 流程改正为对应区域语义，因此没有对应的未解决 EN-301 条目。 | 已从未解决汇总中移除。 |
| 无直接对应项 | EN-301-01、EN-301-06、EN-301-07、EN-301-08、EN-301-09 | 这些问题是在 V3.0.1 翻译期间新发现的表结构、触发条件、表题、共享流程图或枚举冲突，当前没有对应的 EN-300 历史条目。 | 按 EN-301 编号独立跟踪。 |

<br>

## 翻译 V3.0.0 时发现的（疑似）问题
V3.0.0（26-03-19）的英文版原文存在 27 个疑似的问题。<br>
译文已对发现的问题做了优化。<br>
V3.0.1 （截止 26-08-04）也修复了大部分问题：已修复 19 条、部分修复 4 条、未修复 3 条、新增冲突 1 条。

<br>

### ✅ EN-300-01：Section 4.4 引用错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 213 行。<br>
引用不存在的 Section 4.4；当前文档对应内容实际位于 4.3。

**译文（中文）状态**
<br>
已规避。<br>
第 213 行已引用 `4.3 通信主题`。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 215 行改为 Section 4.3，并使用有效锚点。

<br>

### ✅ EN-300-02：6.6.2 锚点错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 646、1483 行。<br>
指向 6.6.2 的锚点损坏或与实际标题生成的锚点不一致。

**译文（中文）状态**
<br>
已规避。<br>
ZH 第 646、1483 行均使用 `#662-节点与边的遍历`，与实际标题一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 646、1515 行均使用 `#662-traversal-of-nodes-and-edges`。

<br>

### ❗ EN-300-03：双层括号链接
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1501、1652 行。<br>
链接出现双层括号，Markdown 语法损坏。

**译文（中文）状态**
<br>
已规避。<br>
第 1501、1652 行使用正常的单层 Markdown 链接。

**官方处理结果**
<br>
部分修复。<br>
V3.0.1（截止 26-08-04）第 1533 行链接已正常；第 1684 行仍为 `]((#731-format-of-action-parameters))`。

<br>

### ✅ EN-300-04：`instantAction` 主题名单复数错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 704 行。<br>
正文使用主题名 `instantAction`，而协议定义为 `instantActions`。

**译文（中文）状态**
<br>
已修正。<br>
第 704 行改为 `instantActions` 主题；第 99、1571 行的消息章节名称和目录锚点同步改为 `instantActions`。依据 `instantActions.schema` 的 title/subtopic 及通信主题表。

**官方处理结果**
<br>
已修复<br>
V3.0.1（截止 26-08-04）第 711 行使用 `instantActions` 主题。

<br>

### ✅ EN-300-05：表 4 缺少`zone` 列值
**V3.0.0 EN 位置 + 问题描述**
<br>
第 703-704 行。<br>
表 4 的 `startHibernation` 和 `stopHibernation` 行缺少最后的 `zone` 列值，导致行列数少于表头。

**译文（中文）状态**
<br>
已修正。<br>
第 703-704 行在 `zone` 列显式补入“否”；动作仅适用于即时动作，与同表的作用域定义一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 710-711 行均补入最后的 `zone` 列值 `no`。

<br>

### ✅ EN-300-06：`defined specified` 重复限定
**V3.0.0 EN 位置 + 问题描述**
<br>
第 723 行。<br>
`defined specified` 出现语义重复，应只保留其中一个限定词。

**译文（中文）状态**
<br>
已规避。<br>
第 723 行使用“`triggerType` 参数所指定类型”，完整保留参数约束且没有继承重复词。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 730 行仅保留 `specified`。

<br>

### ✅ EN-300-07：表 5 缺少 `'RETRIABLE'` 列值
**V3.0.0 EN 位置 + 问题描述**
<br>
第 738 行。<br>
表 5 的 `startPause` 行缺少最后的 `'RETRIABLE'` 列值，导致行列数少于表头。

**译文（中文）状态**
<br>
已修正。<br>
第 738 行在 `'RETRIABLE'` 列补入 `-`，与 `stopPause` 及该表其他不可重试动作的格式一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 745 行已在末列补入 `-`。

<br>

### ✅ EN-300-08：`deleted` 重复
**V3.0.0 EN 位置 + 问题描述**
<br>
第 751 行。<br>
`could not be deleted, deleted` 重复 `deleted`。

**译文（中文）状态**
<br>
已规避。<br>
第 751 行使用“无法删除区域集”，并保留“正在使用或此前已删除”两类失败原因。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 755 行删除重复的 `deleted`。

<br>

### ✅ EN-300-09：`COORDINATED_REPLANNING` 拼写错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 929 行。<br>
区域类型拼写为 `'COORINATED_REPLANNING'`，与正式枚举 `'COORDINATED_REPLANNING'` 不一致。

**译文（中文）状态**
<br>
已规避。<br>
第 929 行使用正式枚举 `'COORDINATED_REPLANNING'`，并与区域定义、图 17 及上下文保持一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 936 行使用 `'COORDINATED_REPLANNING'`。

<br>

### ✅ EN-300-10：表 7 `direction` 子项列错位
**V3.0.0 EN 位置 + 问题描述**
<br>
第 897 行。<br>
表 7 的 `'BIDIRECTED'` `direction` 子项缺少空的“区域类型”单元格，导致后续内容左移一列。

**译文（中文）状态**
<br>
已修正。第 897 行显式补入空的“区域类型”单元格，使 `direction`、`float64` 和描述分别位于正确列。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 904 行补入空的“区域类型”单元格。

<br>

### ✅ EN-300-11：`responseType` 与 `grantType` 不一致
**V3.0.0 EN 位置 + 问题描述**
<br>
第 938-958 行。<br>
叙述使用 `responseType`，表格/UML 使用 `grantType`。

**译文（中文）状态**
<br>
已修正。第 938-942、950、958 行统一为 `grantType`。依据 Release `responses.schema`：`grantType` 是必填字段，枚举为 `GRANTED`、`QUEUED`、`REVOKED`、`REJECTED`。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 945-950、957-967 行统一使用 `grantType`，全文不再出现 `responseType`。

<br>

### ✅ EN-300-12：`COORDINATED_REPLANNING` 流程复制错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 958 行。<br>
`COORDINATED_REPLANNING` 流程误写移动机器人已经位于 `'RELEASE'` 区域，属于复制错误。

**译文（中文）状态**
<br>
已修正。<br>
当前中文稿第 968 行已明确写为移动机器人已经位于 `'COORDINATED_REPLANNING'` 区域，并同步补充停止行驶、报告 `RELEASE_LOST` / `CRITICAL`、保留请求和重新请求等处理规则；内容与 V3.0.1 英文第 967 行一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 963-967 行重写该流程；第 967 行明确写为已经位于 `'COORDINATED_REPLANNING'` 区域，并补充 `RELEASE_LOST` 错误、请求保留和重新申请规则。

<br>

### ✅ EN-300-13：`SEMIAUTOMATIC` 枚举拼写错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1185 行。<br>
枚举写成 `'SEMI-AUTOMATIC'`，而正式值为 `'SEMIAUTOMATIC'`。

**译文（中文）状态**
<br>
已修正。<br>
第 1185 行两处均改为 `'SEMIAUTOMATIC'`，与操作模式表和 state 定义一致。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 1213 行统一使用 `'SEMIAUTOMATIC'`。

<br>

### ✅ EN-300-14：`nodesStates` 字段名错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1225 行。<br>
`nodesStates` 疑似应为 `nodeStates`。

**译文（中文）状态**
<br>
已修正。<br>
第 1225 行改为 `nodeStates`。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 1253 行改为 `nodeStates`。

<br>

### ❗ EN-300-15：Table 2 交叉引用错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1241 行。<br>
引用 Table 2，按上下文很可能应为 Table 11。

**译文（中文）状态**
<br>
已修正。<br>
第 1241 行改为“见表 11”，对应紧随其后的 `actionStatus` 表。

**官方处理结果**
<br>
未修复。<br>
V3.0.1（截止 26-08-04）第 1269 行仍引用 Table 2；实际对应紧随其后的 Table 12。

<br>

### ❗ EN-300-16：`actionsStates` 字段名错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1275 行。<br>
`actionsStates` 疑似应为 `actionStates`。

**译文（中文）状态**
<br>
已修正。<br>
第 1275 行保留正式字段 `actionStates`，并移除正文中的 EN 错字译者注。

**官方处理结果**
<br>
未修复。<br>
V3.0.1（截止 26-08-04）第 1303 行仍使用 `actionsStates`。

<br>

### ✅ EN-300-17：`responses` 主题名单复数及附近拼写错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1281 行。<br>
主题名写成单数 `response`，而定义主题为 `responses`；附近还存在拼写错误。

**译文（中文）状态**
<br>
已修正。<br>
第 1281 行改为 `responses` 主题；第 100、1585 行的消息章节名称和目录锚点同步改为 `responses`。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 1309 行使用 `simultaneously`、`individually` 和 `responses` 主题。

<br>

### ✅ EN-300-18：`nodeState` 对象行列错位
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1730 行。<br>
`nodeState` 对象起始行缺少空“单位”单元格，使 `JSON object` 落入“单位”列。EN 同章其他四列表对象起始/结束行并不存在缺少末尾空单元格的问题。

**译文（中文）状态**
<br>
已修正。<br>
第 1730 行补入空“单位”单元格，使 `JSON object` 回到“数据类型”列。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 1762 行补入空“单位”单元格，`JSON object` 位于“数据类型”列。

<br>

### ❗ EN-300-19：`string` 示例格式不一致
**V3.0.0 EN 位置 + 问题描述**
<br>
第 213、1447-1945、2039、2095-2138 行（多处）。<br>
数据类型为 `string` 的具体示例值格式不一致：时间戳示例带双引号，但 `topic`、协议版本、参数路径、格式、URL、载荷类型和软硬件版本等示例未统一使用 JSON 字符串形式。

**译文（中文）状态**
<br>
已修正。<br>
将具体字符串示例统一为带双引号的代码格式，如 `"order"`、`"1.3.2"`、`"DXF"` 和 `"v1.12.4-beta"`；枚举仍按第 7.1.3 节使用单引号，场景说明不作为字符串字面量处理。

**官方处理结果**
<br>
未修复。<br>
V3.0.1（截止 26-08-04）第 215、1479、1490、1609、1623、1642、1702、1714、1961、1979、2129、2173 等行仍保留未加 JSON 双引号的具体字符串示例。

<br>

### ❗ EN-300-20：`reponses` 拼写及对象表结构错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1601 行。<br>
`reponses` 拼写错误，且该处对象表标点或结束结构异常。

**译文（中文）状态**
<br>
已修正。第 1587-1601 行按 `responses.schema` 重整为三列表格，使用 `responses [response]` 和 `grantType`，并补齐表格结束分隔符。

**官方处理结果**
<br>
部分修复。<br>
V3.0.1（截止 26-08-04）第 1617 行章节名改为复数 `responses`，第 1633 行将 `reponses` 改为 `responses`；表头、分隔行和内容行的首尾管道风格仍未统一。

<br>

### ✅ EN-300-21：`float 64` 数据类型拼写错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1829 行。<br>
数据类型写成 `float 64`，疑似应为 `float64`。

**译文（中文）状态**
<br>
已修正。第 1829 行改为 `float64`。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）对应字段第 1863 行使用 `float64`。

<br>

### ✅ EN-300-22：`INVALID_ORDER` 枚举不一致
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1880 行。<br>
使用 `INVALID_ORDER`，与定义枚举 `INVALID_ORDER_ACTION` 不一致。

**译文（中文）状态**
<br>
已修正。第 1880 行改为 `INVALID_ORDER_ACTION`，与第 538、1154 行的规范性定义一致。Release `state.schema` 将 `errorType` 定义为可扩展字符串，未提供枚举清单。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 1914 行使用 `INVALID_ORDER_ACTION`。

<br>

### ❗ EN-300-23：序列号字段大小写及主题名单复数错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 1997 行。<br>
使用 `state.SerialNumber` 和单数 `response.serialNumber`，大小写及主题单复数均与其他定义不一致。

**译文（中文）状态**
<br>
已修正。第 1997-1998 行改为 `state.serialNumber`、`responses.serialNumber` 及 `responses.timestamp/version/manufacturer`。

**官方处理结果**
<br>
部分修复。<br>
V3.0.1（截止 26-08-04）第 2031 行已改为 `state.serialNumber`，但第 2031-2032 行仍使用单数 `response.serialNumber` 和 `response.timestamp/version/manufacturer`。

<br>

### ❗ EN-300-24：`actions.actionsParameters` 疑点及 V3.0.1 新增冲突
**V3.0.0 EN 位置 + 问题描述**
<br>
第 2008 行。<br>
初步检查时将 `actions.actionsParameters` 视为普通 JSON 路径，因而怀疑其层级或单复数错误。

**译文（中文）状态**
<br>
已确认无问题。<br>
它是 `protocolLimits.maximumArrayLengths` 对象下的字面属性名，不是 action 对象的 JSON 路径。EN 第 2008 行与 Release `factsheet.schema` 第 260 行一致，ZH 第 2008 行保持 `actions.actionsParameters` 正确，无需修改。Schema 其他位置的尾随逗号问题仍作为独立官方源文件问题保留。

**官方处理结果**
<br>
新增冲突。<br>
V3.0.1（截止 26-08-04）文档第 2042 行改为 `action.actionsParameters`，但同版 `factsheet.schema` 第 260 行仍定义 `actions.actionsParameters`。**这不是 V3.0.0 问题的修复，而是 V3.0.1 新增的文档与 Schema 不一致。**

<br>

### ✅ EN-300-25：数组元素名称及 Markdown 对象结构错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 2037-2048 行。<br>
数组元素名称使用复数，部分 Markdown 强调符号和对象结束标记异常。

**译文（中文）状态**
<br>
已修正。第 2037-2059 行将数组元素整理为 `optionalParameter`、`mobileRobotAction`、`actionParameter`，并按对象层级修正强调符号、缩进和结束标记。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 2071-2093 行将数组元素改为单数，补齐外层对象结束标记，并修正后续字段的对象内缩进。

<br>

### ✅ EN-300-26：`versions` 等对象表嵌套错误
**V3.0.0 EN 位置 + 问题描述**
<br>
第 2136-2152 行。<br>
`versions`、`network`、`batteryCharging` 等表格嵌套和结束标记存在异常。

**译文（中文）状态**
<br>
已修正。当前第 2136-2153 行重建三者的对象层级；`versions [version]` 依据 Release Schema 中 items 的 title `version`。新增对象起始行后，后续行号顺延 1。

**官方处理结果**
<br>
已修复。<br>
V3.0.1（截止 26-08-04）第 2170-2187 行拆分 `versions` 对象起始行，并统一 `network`、`batteryCharging` 子项的缩进和结束标记。

<br>

### ❗ EN-300-27：全文拼写、重复词及标记问题
**V3.0.0 EN 位置 + 问题描述**
<br>
全文。<br>
存在 `simulatenously`、`inidivdually`、`overrulling`、重复的 `Receival`、`defined specified`、`deleted, deleted`、`COORINATED_REPLANNING` 以及错误的 `<\\br>` 等拼写、重复词或标记问题。

**译文（中文）状态**
<br>
已规避。<br>
未保留已识别的英文拼写、重复词或错误标记；2026-08-04 P5 复核未发现 `<a>`、`</a>`、`<\\br>` 或 `</br>`。第 723、751、929 行及表格结构问题已单列追溯。

**官方处理结果**
<br>
部分修复。<br>
V3.0.1（截止 26-08-04）已修复 `simulatenously`、`inidivdually`、`overrulling`、`defined specified`、`deleted, deleted`、`COORINATED_REPLANNING` 和坏换行标记；第 1174-1196 行仍多次使用不自然的 `Receival`。

<br>

## 翻译 V3.0.1 时发现的（疑似）问题
V3.0.1 翻译和复核期间，发现 9 项英文原文或共享资源问题。以下内容仅记录问题、影响和中文稿处理，不修改 `VDA5050_EN.md`、英文流程图或 UML 源文件。<br>
相关问题在官方确认前均保留待确认状态。

<br>

### ❗ EN-301-01：`boundingBoxReference` 表重复出现 x/y 行
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:1859-1863`。<br>
`boundingBoxReference` 表中重复出现两组 x/y 行，疑似为重复内容，导致字段表结构不一致。

**译文（中文）状态**
<br>
已规避。<br>
未机械复制重复行，仅保留 x/y/z 各一行。

**官方处理结果**
<br>
待官方确认。<br>
英文原文当前仍保留该重复结构，未据此修改英文内容。

<br>

### ❗ EN-301-02：`actionStatus` 交叉引用错误
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:1269`。<br>
`actionStatus` 说明仍引用 `Table 2`；由于前文新增表格，按当前文档结构实际应引用表 12。

**译文（中文）状态**
<br>
已修正。<br>
中文稿按实际表号引用表 12。

**官方处理结果**
<br>
待官方确认。<br>
英文原文仍保留 `Table 2` 引用，未修改英文内容。

<br>

### ❗ EN-301-03：`versions` 数组元素名称与 Schema 不一致
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:2170`、`json_schemas/factsheet.schema:831`。<br>
英文文档使用 `versions[versionInfo]`，但 Schema 中数组元素标题仍为 `version`，文档与 Schema 定义不一致。

**译文（中文）状态**
<br>
已按英文处理。<br>
中文稿采用 `versions[versionInfo]`，并保留文档与 Schema 的冲突记录。

**官方处理结果**
<br>
待官方确认。<br>
未修改英文文档或 Schema，等待官方统一字段命名。

<br>

### ❗ EN-301-04：`actionParameters` 链接双层括号
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:1684`。<br>
链接写成 `]((#731-format-of-action-parameters))`，多出一个左括号，导致 Markdown 链接无法正常跳转。

**译文（中文）状态**
<br>
已规避。<br>
中文稿使用可正常跳转的单层括号链接。

**官方处理结果**
<br>
待官方确认。<br>
英文原文仍保留双层括号问题，未修改英文内容。

<br>

### ❗ EN-301-05：factsheet MQTT 参数主题名单复数不一致
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:2031-2032`。<br>
factsheet 的 MQTT 参数列表使用 `response.*`，但协议主题和第 7.5 节使用复数主题 `responses`，主题名称不一致。

**译文（中文）状态**
<br>
已修正。<br>
中文稿按协议主题名称使用 `responses.*`。

**官方处理结果**
<br>
待官方确认。<br>
英文 factsheet 仍使用单数 `response.*`，未修改英文内容。

<br>

### ❗ EN-301-06：状态消息触发条件重复且载荷字段不一致
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:1045-1068`。<br>
状态消息触发条件重复列出 `operatingMode` 至 `zoneSets` 等条目，同时出现旧的单数 `load` 对象和新的 `loads` 数组，字段定义存在不一致。

**译文（中文）状态**
<br>
已规避。<br>
中文稿去除重复项，并按状态契约使用 `loads` 数组。

**官方处理结果**
<br>
待官方确认。<br>
英文原文的重复条目及 `load`/`loads` 并存问题仍待官方澄清，未修改英文内容。

<br>

### ❗ EN-301-07：表题缺少统一分隔符
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:217,237,687,1295`。<br>
表 1、表 2、表 3、表 13 的题注缺少其他表题普遍使用的 ` - ` 分隔符，格式不统一。

**译文（中文）状态**
<br>
已修正。<br>
中文稿统一使用“编号 - 题名”格式。

**官方处理结果**
<br>
待官方确认。<br>
英文表题当前仍未统一使用分隔符，未修改英文内容。

<br>

### ❗ EN-301-08：流程图 `response topic` 主题名单复数不一致
**V3.0.1 EN 位置 + 问题描述**
<br>
`assets/request_release_zone_access_UML.md:23,27,30,35,47` 及图 16。<br>
共享流程图仍使用单数 `response topic`，与协议主题 `responses` 不一致。

**译文（中文）状态**
<br>
已规避。<br>
中文正文使用 `responses`；继续引用官方共享图片，不修改图片或 UML 源文件。

**官方处理结果**
<br>
待官方确认。<br>
英文流程图及其 UML 源文件仍待官方统一主题名称，未修改英文共享资源。

<br>

### ❗ EN-301-09：`requestStatus` 的 `QUEUED` 枚举与字段定义冲突
**V3.0.1 EN 位置 + 问题描述**
<br>
`VDA5050_EN.md:1358-1364,1880,1890`、`json_schemas/state.schema:630-633,668-671`。<br>
第 6.9 节将 `'QUEUED'` 列为 `requestStatus` 支持值，但第 7.8 节的 `zoneRequest`/`edgeRequest` 字段表和 Schema 枚举均不包含 `'QUEUED'`；该值同时被定义为响应决定，存在归属冲突。

**译文（中文）状态**
<br>
已保留原文语义。<br>
中文字段表未扩展 `requestStatus` 枚举，保留第 6.9 节的原文翻译并等待官方确认其归属。

**官方处理结果**
<br>
待官方确认。<br>
英文文档和 Schema 当前定义仍不一致，未修改英文内容。

<br>
