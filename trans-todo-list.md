# VDA5050_ZH.md 翻译同步 TODO

## 0. 原文保护约束

- `VDA5050_EN.md` 是只读对照基准，任何情况下不得修改其内容。
- EN 原文中的版本号、拼写、语义、字段定义、表格结构或其他问题，只在本清单中记录文件位置、问题描述和影响；不得在 EN 文件中修复、润色、回写或调整格式。
- 中文翻译任务仅修改 `VDA5050_ZH.md`（如后续明确授权）；遇到英文源文档疑点时，保留问题记录并等待原文维护方确认。

## 1. 比对基准

- 当前分支：`local-3.0.1-zh-cn`。
- 英文基准：当前分支的 `VDA5050_EN.md`，内容与 `dev/3.0.1` 一致。
- 差异命令：`git diff 3.0.0..HEAD -- VDA5050_EN.md`。
- 差异规模：333 行变更（184 行新增、149 行删除）；变更既包括协议语义，也包括拼写、Markdown、表格和链接修正。
- 仓库级差异共涉及 14 个文件：除中英文文档外，还包括 2 张流程图及其 UML 源文件，以及 8 个 JSON Schema。中文稿直接引用已更新的 `process_order_update.png` 和 `request_release_zone_access.png`，无需复制图片。图 8、图 16 的题注、正文和新版流程已完成复核，结论见第 6 节。Schema 不需要翻译，但可用于校验本清单中的字段名、枚举和可选性。
- `VDA5050_ZH.md` 在 `3.0.0` tag 中不存在，因此不能直接对中文文件做 tag-to-head 的文件 diff；本清单将英文 `3.0.0 -> 3.0.1` 的变化映射到当前中文稿，并标注中文稿已经同步或仍需更新的部分。
- 当前英文文件标题仍写作 `Version 3.0.0`（`VDA5050_EN.md:7,27`）。在官方确认版本号前，不要仅因分支名为 3.0.1 而把中文标题改为“3.0.1”。

英文原文及共享英文资源中的问题统一归入第 5 节，只记录、不修改；中文稿的复核结论和剩余任务分别归入第 6、7 节。

## 2. 3.0.0 -> 3.0.1 diff 细节

### 2.1 文档头、目录与通用格式

| 英文位置 | diff 细节 | 对中文稿的影响与现状 |
|---|---|---|
| `VDA5050_EN.md:23-25` | Copyright 文案由 `Reproduction` 改为 `Reprint`。 | 已完成复核：中文“复制或以其他形式再现”覆盖原文语义，无需修改。 |
| `VDA5050_EN.md:52-100` | 目录修正 6.1.2、6.3.2、6.4.4、7.5 的标题复数/介词及锚点。 | 中文目录标题和锚点已按中文章节名同步，`已同步`；完成全量链接检查。 |
| `VDA5050_EN.md:128-143,275-290,534,633,1332-1365` | 在列表前增加空行、统一列表缩进和换行。 | 中文列表前空行、缩进和换行已统一，`已同步`。 |
| `VDA5050_EN.md:149,198,242` | `their -> its`、`followed -> follows`、补冠词等英文语法修正。 | 中文不产生对应语法变化，相关句子已校对，`已同步`。 |
| `VDA5050_EN.md:213` | Topic levels 表中的章节链接由错误的 4.4 改为 4.3。 | 中文已链接到 4.3，`已同步`。 |
| `VDA5050_EN.md:2192-2197` | 参考文献将破折号改为冒号，并补齐末尾换行。 | ISO 9787、ISO 8601 已改用冒号，LIF 名称使用连接号，文件末尾换行已保留，`已同步`。 |

### 2.2 订单、动作与地图（6.1-6.3）

| 英文位置 | diff 细节 | 中文稿待办 |
|---|---|---|
| `VDA5050_EN.md:346` | 6.1.2 标题改为 `Order and order updates`。 | 中文标题“订单与订单更新”已同步。 |
| `VDA5050_EN.md:366-409` | 图 4 的伪 JSON 在 `orderId` 后补逗号；图 4、图 5 题注统一为 `Figure n - ...`。 | 中文图题已带连字符，`VDA5050_ZH.md:364` 的伪 JSON 逗号已补齐。 |
| `VDA5050_EN.md:441-458` | 订单更新判断中 `orderUpdateId` 从“小于或等于当前值”改为“严格小于当前值”；并修正英文语法。 | `VDA5050_ZH.md:448` 已改为“小于”；第 10 项“也不等待订单的继续”与英文 `nor` 语义一致。 |
| `VDA5050_EN.md:520-534,608` | 警告标点、示例列表排版，以及“order mode”改为“operating mode”。 | 中文错误级别标点、示例列表空行和“操作模式”用词均已同步。 |
| `VDA5050_EN.md:650-663` | 边动作链接改指 6.6.2；即时动作状态字段由 `actionStatus` 更正为 `actionState`。 | 链接已同步；`VDA5050_ZH.md:661` 已改为“添加 `actionState`”，后续 `actionStatus` 状态字段保持不变。 |
| `VDA5050_EN.md:707-727` | 休眠动作增加 `wakeUpTime` 的 ISO 8601 UTC 时间戳格式；`instantAction` topic 改为 `instantActions`；`pick/drop` 参数 `lhd` 改为 `loadHandlingDevice`，关联状态 `.load` 改为 `loads`；`clearZoneActions` 清理 `zoneActions`。 | `VDA5050_ZH.md:703` 已补充时间戳格式和示例；`clearZoneActions` 与休眠唤醒 topic 已同步；`:719-720` 的参数和关联状态已更新为 `loadHandlingDevice`、`loads`，factsheet `:2107` 的参数说明也已同步。 |
| `VDA5050_EN.md:743-756` | 预定义动作状态表补齐末列占位符；`initializePosition` 完成状态中的 `mobileRobotPosition.lastNodeId` 改为顶层 `lastNodeId`；删除区域集错误说明中的重复词；`clearZoneActions` 的清理对象改为 `zoneActions`。 | `initializePosition` 已改为顶层 `lastNodeId`，区域动作语义已同步，动作状态表各行均为 7 列并包含末列占位符。 |
| `VDA5050_EN.md:766,781,833` | `cancelOrder` 错误列表标点、坐标系语法、`Other versions` 大小写修正。 | 中文标点和对应措辞已校对，`已同步`。 |
| `VDA5050_EN.md:849` | `supportedZones` 所在 factsheet 节点由错误的 `typeSpecifications` 改为 `typeSpecification`。 | `VDA5050_ZH.md:845` 已改为单数字段名 `typeSpecification`。 |

### 2.3 区域、区域请求与释放丢失处理（6.4）

| 英文位置 | diff 细节 | 中文稿待办 |
|---|---|---|
| `VDA5050_EN.md:874` | `releaseLossBehavior` 改为可选字段，并明确撤销/过期发生在区域内时的三种行为：`STOP` 停止并报告 `RELEASE_LOST/CRITICAL`；`EVACUATE` 或 `CONTINUE` 保留请求、将状态置为 `REVOKED/EXPIRED`，并报告 `RELEASE_LOSS_HANDLING/WARNING`；完成离区或订单在区域内结束后停止报告。 | `VDA5050_ZH.md:867` 已标记为可选字段，并已完整同步默认行为、三种处理方式、请求状态、错误类型/级别及各自的终止条件。 |
| `VDA5050_EN.md:902` | 修正 `<br>` 标签；`DUPLICATE_ZONE_SET` 强制使用 `shall report`。 | 中文语义已覆盖，换行标签统一为 `<br>`，`已同步`。 |
| `VDA5050_EN.md:916-934` | 6.4.3 标题层级由二级改为三级；修正 `COORINATED_REPLANNING` 拼写；响应对象统一称 `responses message`，`responseType` 统一改为 `grantType`；补充请求方所有格。 | 中文标题 `VDA5050_ZH.md:914` 已改为 `###`；`grantType`、`responses` 字段已同步，全文无旧 `responseType`。 |
| `VDA5050_EN.md:956-967` | 明确 RELEASE 和 COORDINATED_REPLANNING 在“尚未进入/已经在内”两种情况下收到撤销或过期许可时的不同处理；后者必须报告 `RELEASE_LOST/CRITICAL` 并保留请求。 | `VDA5050_ZH.md:949-951,958-960` 已按两类区域分别拆分进入前和区域内规则；已同步请求移除/保留、`requestStatus`、错误级别、终止条件及重新请求要求。 |
| `VDA5050_EN.md:973` | `overrulling -> overruling`，矩阵行末多余竖线删除。 | 中文区域交互矩阵已核为 13 列并删除行末多余竖线，`已同步`。 |

### 2.4 状态、错误、操作模式与请求机制（6.5-6.9）

| 英文位置 | diff 细节 | 中文稿待办 |
|---|---|---|
| `VDA5050_EN.md:1017` | 连接示例中的 `OFFLINE` 统一使用枚举代码格式。 | 中文已用枚举代码，`已同步`。 |
| `VDA5050_EN.md:1054-1068` | 明确触发状态消息的字段变化：`operatingMode`、`driving`、`paused`、`safetyState`、`newBaseRequest`、节点/边/动作/区域请求、电源充电、载荷、错误、区域集等。 | 中文已包含这些触发项，并额外保留地图变化；载荷字段按状态契约使用 `loads` 数组，`已同步`。 |
| `VDA5050_EN.md:1117` | 图 20 题注明确为 `allowedDeviationXY ellipse`。 | 中文题注已包含 `allowedDeviationXY`，`已同步`。 |
| `VDA5050_EN.md:1125` | 信息报告持续时间说明由“information message”改为“this information”。 | 中文已明确为“报告某项信息的时长”，`已同步`。 |
| `VDA5050_EN.md:1185-1200` | 错误表新增 `RELEASE_LOSS_HANDLING/WARNING`；`RELEASE_LOST` 扩展到 RELEASE 和 COORDINATED_REPLANNING 且说明“在区域内停止”；新增 `INSTANT_ACTION_STATES_FULL/URGENT` 和 `ZONE_ACTION_STATES_FULL/URGENT`；插入表 9 题注并导致后续表号顺延。 | `VDA5050_ZH.md:1166-1178` 已补充三类错误行、更新 `RELEASE_LOST` 描述并插入表 9 题注；后续表题已顺延为表 10-14。状态消息表中的两个 FULL 错误描述与预定义表一致。 |
| `VDA5050_EN.md:1211-1253` | `SEMIAUTOMATIC` 拼写统一；表 10 中 MANUAL 的清除条件改为“无法再开始新订单”；清除订单时字段由 `nodesStates` 修正为 `nodeStates`，并在等待动作完成后允许报告 `STARTUP`。 | 中文枚举和 `nodeStates` 已同步；`VDA5050_ZH.md:1206` 的 MANUAL 条件及 `:1232` 的 `STARTUP` 等待条件已更新。 |
| `VDA5050_EN.md:1274-1295` | `PAUSED` 的原因改为 `startPause` 即时动作；表题因前文新增表格顺延到表 12、表 13。 | `VDA5050_ZH.md:1255` 已明确为 `startPause` 即时动作；表 12 和表 13 的题注也已同步。 |
| `VDA5050_EN.md:1307-1316` | 修正 simultaneously/individually 拼写，走廊审批引用从 `response` topic 改为 `responses` topic。 | 中文走廊段落已使用“同时请求”“分别批准”和 `responses` 主题，`已同步`。 |
| `VDA5050_EN.md:1351-1377` | 请求列表格式化；请求完成后的处理由仅引用 `releaseLossBehavior` 改为适用于请求资源的通用 release-loss handling；已开始的操作保留请求并标记 `REVOKED/EXPIRED`，未开始的立即移除。 | `VDA5050_ZH.md:1351-1352` 已改为面向请求资源的通用释放丢失处理；已开始的操作保留请求并设置 `REVOKED/EXPIRED`，尚未开始的操作立即移除。 |

### 2.5 消息字段与 factsheet（7.1-7.10）

| 英文位置 | diff 细节 | 中文稿待办 |
|---|---|---|
| `VDA5050_EN.md:1415-1457` | 表号顺延；修正 unsupported parameter 语法、`paramter` 拼写。 | 中文语义和表 14 题注均已校对，`已同步`。 |
| `VDA5050_EN.md:1502-1544` | `nodeDescriptor` 改为“用户定义、可读名称/描述符，不得用于逻辑”；`allowedDeviationXY` 引用改为 6.6.2；修正 `mapId` 行闭合；`actionId` 单复数和 UUID 表述；修正 actionParameters 链接；修正 orientation 语句。 | `nodeDescriptor`、`allowedDeviationXY`、`actionId`、orientation 说明和链接均已同步，`nodePosition` 的 `mapId` 行已补结束花括号。 |
| `VDA5050_EN.md:1588-1632` | 7.5 改为 `responses`；`grantType` 描述分行并修正 timestamp 示例标点；zoneSet、maximumSpeed、vertex 等仅作 Markdown 修正。 | 中文 7.5 标题和 `grantType` 已同步；`VDA5050_ZH.md:1607` 已按 `GRANTED/QUEUED/REVOKED/REJECTED` 顺序分行。 |
| `VDA5050_EN.md:1716-1765` | `zoneSets` 数据类型改为 `array`；速度明确为 mobile robot coordinates；`actionStates` 的结果字段改为 `actionResult`；`zoneSet` 对象格式修正，`zoneSetId` 仅保留“唯一标识符”，不再附带“当前启用/无区域时为空”的旧限制；枚举补齐引号。 | `zoneSets`、`actionResult`、`zoneSetId`、速度坐标系、枚举引号及对象格式均已同步。 |
| `VDA5050_EN.md:1820-1875` | 位姿角补充单位 `rad`；载荷包围盒 reference 补充 x/y/z 及 `m` 单位；`requestType`/`trajectory` 换行和措辞；统一直引号；`localized` 语法修正。 | 位姿和包围盒单位、请求字段、`trajectory` 可选性及引号格式均已同步；英文重复的 x/y 行已记录且未复制。 |
| `VDA5050_EN.md:1912-1950` | errorType 可扩展枚举补充 `INVALID_ORDER_ACTION`、`INSUFFICIENT_MEMORY`、`RELEASE_LOSS_HANDLING`、`OTHER_ORDER_ACTIVE`、`START_NODE_OUT_OF_RANGE`、`MOBILE_ROBOT_NOT_AVAILABLE`、`INSTANT_ACTION_STATES_FULL`、`ZONE_ACTION_STATES_FULL` 等；`infoReferences` 加粗；`fieldViolation` 空格修正。 | 预定义枚举已按英文完整集合更新，`infoReferences` 已标为可选数组，`fieldViolation` 格式已同步。 |
| `VDA5050_EN.md:1996-2095` | factsheet 的 `<br/>` 统一为 `<br>`；`state.SerialNumber -> state.serialNumber`；`actions.actionsParameters -> action.actionsParameters`；`optionalParameters` 元素名改为单数 `optionalParameter`；`mobileRobotGeometry` 标题层级改为四级。 | 中文已使用 `state.serialNumber`、`optionalParameter`，`已同步`；`VDA5050_ZH.md:2015` 已改为 `action.actionsParameters`；`:2068` 已改为四级标题。 |
| `VDA5050_EN.md:2139-2187` | `loadPositions` 说明中的动作参数由 `lhd` 改为 `loadHandlingDevice`；load set 说明由 `btw.` 改为 `or`；版本表和 batteryCharging 表修正缩进/表格结构。 | 已完成复核：`loadHandlingDevice` 和“位置或载荷搬运装置”语义已同步，版本表与 `batteryCharging` 缩进和列结构正确。 |

## 3. 翻译 TODO List

### P0：协议语义和字段契约

- [x] **6.1.2 订单更新判断**：将 `VDA5050_ZH.md:448` 的“`orderUpdateId` 小于或等于当前值”改为“严格小于当前值”；第 10 项英文 `nor` 的中文逻辑已核对。
- [x] **6.1.2 伪 JSON**：在 `VDA5050_ZH.md:364` 的 `orderId: "1234"` 后补逗号，确保示例与英文一致。
- [x] **6.2.1 即时动作状态**：将 `VDA5050_ZH.md:661` 中“添加 `actionStatus`”改为“添加 `actionState`”；后续 `actionStatus` 状态字段含义保持不变。
- [x] **6.2.3 休眠动作**：在 `VDA5050_ZH.md:703` 增加 `wakeUpTime` 为 ISO 8601 UTC 时间戳的格式和示例：`YYYY-MM-DDTHH:mm:ss.fffZ`。
- [x] **6.2.3 pick/drop**：在 `VDA5050_ZH.md:719-720` 和 factsheet `:2107` 将 `lhd` 全部改为 `loadHandlingDevice`，将关联状态 `.load` 改为 `loads`。
- [x] **6.2.3 initializePosition**：将 `VDA5050_ZH.md:745` 的 `mobileRobotPosition.lastNodeId = lastNodeId` 改为顶层字段 `lastNodeId = lastNodeId`。
- [x] **6.4.1 releaseLossBehavior**：重译 `VDA5050_ZH.md:867`，标为可选字段，并完整表达 STOP/EVACUATE/CONTINUE 的状态保留、错误类型/级别和终止条件。
- [x] **6.4.3 交互式区域**：将 `VDA5050_ZH.md:949-950` 的 RELEASE 撤销/过期规则拆成“尚未进入”和“已在区域内”；将 `:957-958` 的 COORDINATED_REPLANNING 规则改为 `RELEASE_LOST/CRITICAL`、保留请求并重新请求；不得误写为 RELEASE 区域。
- [x] **6.6.5 预定义错误表**：在 `VDA5050_ZH.md:1158-1172` 增加 `RELEASE_LOSS_HANDLING`、`INSTANT_ACTION_STATES_FULL`、`ZONE_ACTION_STATES_FULL`，并修改 `RELEASE_LOST` 描述以覆盖 RELEASE/COORDINATED_REPLANNING；补充表题并顺延后续表号。
- [x] **6.6.6 操作模式**：将 `VDA5050_ZH.md:1206` 的 MANUAL 条件改为“如果无法再开始新订单”；将 `:1232` 的等待条件加入 `STARTUP`。
- [x] **6.6.9 动作状态**：将 `VDA5050_ZH.md:1255` 的“暂停即时动作”改为“`startPause` 即时动作或外部触发器”。
- [x] **6.9 请求/响应机制**：将 `VDA5050_ZH.md:1351-1352` 改为面向请求资源的通用 release-loss handling；已开始的操作保留请求并设 `REVOKED/EXPIRED`，未开始的操作立即移除。
- [x] **7.3 订单消息字段**：将 `VDA5050_ZH.md:1479` 的 `nodeDescriptor` 改为“用户定义、人类可读名称或描述符，不得用于逻辑目的”；将 `:1490` 的旧章节链接改为 6.6.2。
- [x] **7.8 state 字段**：将 `VDA5050_ZH.md:1693` 的 `zoneSets` 数据类型改为 `array`；将 `:1711` 的 `resultDescription` 改为 `actionResult`；将 `:1731` 的 `zoneSetId` 说明改为仅“区域集的唯一标识符”。
- [x] **7.8/7.9 坐标单位**：为 `VDA5050_ZH.md:1807` 的 `mobileRobotPosition.theta` 补 `rad`；为 `:1834-1836` 的 boundingBoxReference x/y/z 补 `m`，并确认 `theta` 的朝向说明与英文一致。
- [x] **7.8 errorType 字段**：将 `VDA5050_ZH.md:1887` 的预定义枚举更新为英文完整集合，至少包含 `INVALID_ORDER_ACTION`、`INSUFFICIENT_MEMORY`、`RELEASE_LOSS_HANDLING`、`OTHER_ORDER_ACTIVE`、`START_NODE_OUT_OF_RANGE`、`MOBILE_ROBOT_NOT_AVAILABLE`、`INSTANT_ACTION_STATES_FULL`、`ZONE_ACTION_STATES_FULL`。
- [x] **7.10 factsheet 字段**：将 `VDA5050_ZH.md:2015` 的 `actions.actionsParameters` 改为 `action.actionsParameters`；将 `:2114` 的 `lhd` 改为 `loadHandlingDevice`。

### P1：章节层级、字段字面量和交叉引用

- [x] 将 `VDA5050_ZH.md:914` 的 `## 6.4.3` 改为 `### 6.4.3`，并检查目录层级与锚点。
- [x] 全文检索并确认 `responseType`、`typeSpecifications`、`state.SerialNumber`、`resultDescription`、`actions.actionsParameters`、`lhd`、`.load` 等旧字段没有残留；协议字段名不得翻译或变形。
- [x] 核对 `responses` 主题、`response` 对象、`grantType` 枚举的使用边界：主题使用复数 `responses`，数组元素仍为 `response`，许可字段为 `grantType`。
- [x] 同步表号：新增错误表后，操作模式、动作状态、请求机制和表格符号对应的中文表题已分别与英文表 9-14 对齐。
- [x] 将 `VDA5050_ZH.md:2068` 的 `### mobileRobotGeometry` 改为 `####`，与 factsheet 同级字段保持一致。
- [x] 检查 `VDA5050_ZH.md:1607` 的 `grantType` 描述顺序和分行，已按 `GRANTED/QUEUED/REVOKED/REJECTED` 与英文一致。
- [x] 将 `VDA5050_ZH.md:1656` 的 `zoneAction.actionType` 交叉引用改为明确引用“表 4”；已核对 factsheet `blockingTypes` 的枚举顺序为 `NONE, SINGLE, SOFT, HARD`。
- [x] 核对 `VDA5050_ZH.md:2143` 的数组元素名，已按英文文档采用 `versions[versionInfo]`；英文与 Schema 的 `versionInfo/version` 冲突已记录。
- [x] 检查 7.3 `allowedDeviationXY`、7.5 `responses`、7.8 `state`、7.10 `factsheet` 的所有内部链接，已确认 6.6.2、6.4.4、7.5 等目标可跳转。

### P2：排版、表格和语言校对

- [x] 统一中文稿 `<br/>` 与 `<br>` 写法、列表前空行、表格列数、对象花括号间空格及多余竖线；已检查动作状态表、区域交互矩阵和 factsheet 表。
- [x] 对照英文修正图题和表题中的连字符、表号、引号（直引号/中文引号）及 ISO 8601 示例标点；中文 22 个图题和 14 个表题均采用“编号 - 题名”格式。
- [x] 校对 6.1、6.2、6.4、6.6 的语法变化，已统一“操作模式”、“同时/分别”以及“已开始/尚未开始”等措辞，并将状态触发字段规范为 `loads`。
- [x] 统一参考文献 ISO 9787、ISO 8601、LIF 的标点格式，并保留文件末尾换行。

## 4. 完成验收

- [x] `rg` 检索不再出现上述旧字段名；`loads [load]` 中的数组元素名 `load` 和独立的 `load` 对象为有效字段，不属于旧的 `state.load` 路径。
- [x] 已逐节对照 6.1.2、6.2.1、6.2.3、6.4.1、6.4.3、6.6.5、6.6.6、6.6.9、6.9、7.3、7.8、7.10，新增句子、字段和枚举均已翻译。
- [x] Markdown 标题层级与英文一致（H1-H4 数量分别为 11、34、36、31）；内部链接、表格列数和 6 个代码围栏已复核。
- [x] 已重新执行 `git diff --check`，未发现尾随空格、空白错误或缺失换行。
- [ ] 若英文文档最终将版本号从 3.0.0 更新为 3.0.1，再同步修改中文文档头部的版本号和目录元信息。

## 5. 待官方确认的 EN 原文及共享资源问题

以下项目只记录，不修改 `VDA5050_EN.md`、英文流程图或其 UML 源文件。
本节编号使用 `EN-301-xx`，表示翻译 V3.0.1 期间发现的问题；V3.0.0 问题统一使用 `EN-300-xx`，详见 [trans-issues-sols.md](./trans-issues-sols.md)。

| 编号 | 位置 | 待确认问题 | 中文稿当前处理 | 状态 |
|---|---|---|---|---|
| EN-301-01 | `VDA5050_EN.md:1859-1863` | `boundingBoxReference` 表重复出现两组 x/y 行。 | 未机械复制重复行，仅保留 x/y/z 各一行。 | 待官方确认 |
| EN-301-02 | `VDA5050_EN.md:1269` | `actionStatus` 说明仍引用 `Table 2`，新增表格后实际应为表 12。 | 按实际表号引用表 12。 | 待官方确认 |
| EN-301-03 | `VDA5050_EN.md:2170`、`json_schemas/factsheet.schema:831` | 英文使用 `versions[versionInfo]`，Schema 数组元素标题仍为 `version`。 | 按英文文档采用 `versions[versionInfo]`。 | 待官方确认 |
| EN-301-04 | `VDA5050_EN.md:1684` | `actionParameters` 链接为 `]((#731-format-of-action-parameters))`，多了一个左括号。 | 使用可正常跳转的单括号链接。 | 待官方确认 |
| EN-301-05 | `VDA5050_EN.md:2031-2032` | factsheet 的 MQTT 参数列表使用 `response.*`，但协议主题和 7.5 章节使用复数 `responses`。 | 按协议主题名称使用 `responses.*`。 | 待官方确认 |
| EN-301-06 | `VDA5050_EN.md:1045-1068` | 状态消息触发条件重复列出 `operatingMode` 至 `zoneSets` 等条目，并同时出现旧的单数 `load` 对象和新的 `loads` 数组。 | 去除重复项并使用 `loads` 数组。 | 待官方确认 |
| EN-301-07 | `VDA5050_EN.md:217,237,687,1295` | 表 1、表 2、表 3、表 13 题注缺少其他题注普遍使用的 ` - ` 分隔符。 | 统一使用“编号 - 题名”格式。 | 待官方确认 |
| EN-301-08 | `assets/request_release_zone_access_UML.md:23,27,30,35,47`、图 16 | 流程图仍使用单数 `response topic`，与协议主题 `responses` 不一致。 | 中文正文使用 `responses`；继续引用官方共享图片，不改图片或 UML。 | 待官方确认 |
| EN-301-09 | `VDA5050_EN.md:1358-1364,1880,1890`、`json_schemas/state.schema:630-633,668-671` | 6.9 将 `'QUEUED'` 列为 `requestStatus` 支持值，但 7.8 的 `zoneRequest`/`edgeRequest` 字段表和 Schema 枚举均不包含 `'QUEUED'`；该值同时被定义为响应决定。 | 不扩展中文字段表中的 `requestStatus` 枚举；保留 6.9 的原文翻译并等待官方确认其归属。 | 待官方确认 |

## 6. 中文稿已完成复核

| 复核项 | 结论 |
|---|---|
| 图 8 订单/订单更新流程 | 已确认图片为当前分支更新后的资源；新订单和订单更新分支均引用步骤 11，与正文的状态填充步骤一致。中文引导语、题注和步骤 1-11 与新版流程一致。 |
| 图 16 RELEASE 区域请求流程 | 已确认撤销和过期分支限定为“区域内”，并增加按 `releaseLossBehavior` 处理的步骤；中文正文已分别说明进入区域前和已在区域内的处理，题注正确。共享英文图片的单数主题名问题已登记为 EN-301-08。 |
| Copyright 措辞 | `Reproduction -> Reprint` 不改变现有中文免责声明的实质含义，“复制或以其他形式再现”无需调整。 |
| factsheet `loadPositions` | `loadHandlingDevice`、`state.loads[].loadPosition`、位置/载荷搬运装置语义以及空数组规则均已与英文对齐。 |
| 表名、表号和引用 | 14 个中文表题均采用“表 n - 题名”；新增表 9 后，表 10-14 及正文引用已复核，未发现引用旧表号的中文内容。 |
| 字段残留与 Markdown 结构 | 未发现待替换的旧字段名；标题层级、内部链接、表格列数、代码围栏和空白检查均通过。 |

## 7. 尚未完成的中文任务

当前没有可独立继续修改的中文内容。仅保留以下条件触发项：

- [ ] 等待官方确认英文文档版本号；仅当 `VDA5050_EN.md` 的标题和元信息正式更新为 3.0.1 后，才同步修改中文版本号。
- [ ] 官方处理第 5 节问题后，按最终英文原文逐项复查中文稿；在此之前不预判或回写英文修正。
